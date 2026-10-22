# Arquitetura de produção — GeFin

## Objetivo
MVP web/PWA com evolução incremental. Frontend Next.js na Vercel; API Fastify/Node.js em infraestrutura local inicialmente, migrável para host gerenciado; autenticação Firebase Google; Supabase PostgreSQL como fonte canônica; PostgreSQL local como réplica/espelho operacional, não como segundo escritor independente.

## Fluxos
1. Firebase autentica; cliente envia ID token via HTTPS; API valida assinatura, issuer, audience, expiração e revogação conforme política; UID identifica usuário.
2. Entrada manual/chat/arquivo cria intenção com UUID e chave de idempotência estável; se offline, persiste em IndexedDB e exibe **pendente**, não **confirmado**.
3. API valida schema, propriedade dos recursos, moeda, valor e data; faz commit atômico da transação e evento outbox no Supabase; resposta inclui ID, status e versão.
4. Worker replica eventos ordenados e reexecutáveis ao PostgreSQL local com checkpoint, retry e reconciliação. Falha da réplica não desfaz a escrita canônica.
5. Chat IA propõe operações estruturadas; usuário confirma antes da execução; ferramentas autorizadas aplicam as mesmas regras de API.
6. Importações em lote entram em staging para prévia, conciliação e confirmação; itens duplicados ou incertos são revisados.

## Componentes
- apps/web: Next.js, TypeScript, Tailwind, PWA, IndexedDB/Dexie.
- apps/api: Fastify, Zod, Firebase Admin, Drizzle, OpenAPI.
- apps/worker: BullMQ/Redis para jobs; preferir mecanismo durável de outbox no PostgreSQL e evitar depender só da memória do Redis.
- packages/shared: tipos e contratos de API; infra/docker: PostgreSQL local e pgAdmin (somente rede privada).
- Observabilidade: logs estruturados com redaction, métricas, tracing e alertas; backups criptografados e restauração periódica.

## Disponibilidade
Ngrok/Cloudflare Tunnel apenas com TLS, autenticação, limitação de acesso e monitoramento. Nenhum túnel substitui alta disponibilidade. Backend local desligado = IA e sincronização indisponíveis; UI cacheada e fila local continuam, se o dispositivo tiver dados. PWA não promete persistência absoluta nem sincronização em segundo plano em todos os navegadores.

## Escala
API stateless; serviços separados por domínio lógico; filas e jobs idempotentes; índices e paginação; migrações versionadas; estratégia de migração do backend local para cloud sem alterar contratos. Não fazer replicação bidirecional sem resolução de conflitos especificada.
