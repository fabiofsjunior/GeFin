# GeFin — Gestão Financeira Inteligente

> Status: planejamento e prototipagem; **não é software em produção**.

Plataforma web e PWA mobile-first para finanças pessoais, com chat de IA, transações, cartões, orçamentos, importação de faturas e futura integração Open Finance.

## Experiência
- Desktop: dashboard como entrada, navegação lateral, chat flutuante.
- Mobile: login Firebase Google → chat estilo mensageiro → dashboard, cartões, relatórios e configurações.
- Mensagens, áudio e anexos: interpretar, exibir prévia, pedir confirmação e registrar.
- Offline-first: IndexedDB e fila persistente; **pendente de sincronização não significa salvo no servidor**.

## Arquitetura alvo
Next.js + TypeScript + PWA (Vercel); Firebase Authentication; API Node.js/Fastify; Supabase PostgreSQL canônico; PostgreSQL local como réplica operacional com sincronização por outbox/inbox; Redis/BullMQ para tarefas; IA com ferramentas restritas. Backend local por túnel HTTPS autenticado somente no MVP controlado. Sem backend disponível, operações remotas ficam pendentes; não prometer disponibilidade absoluta.

## Princípios
Segurança por padrão; autorização por UID Firebase verificado no servidor; isolamento de dados; valores monetários em centavos inteiros; datas com timezone; IDs UUID; idempotência e deduplicação separadas; logs sem dados sensíveis; observabilidade, backup e restauração testada; LGPD e consentimento explícito. Nunca expor service-role keys no navegador.

## Processo de entrega
Uma SPEC por sprint: especificar → protótipo HTML responsivo → aprovação humana → implementação em branch → QA e auditoria → PR → checkpoint → merge. Sem deploy de branch de trabalho na produção.

## Documentação
- [Arquitetura](docs/ARCHITECTURE.md)
- [Design system e art concept](docs/DESIGN-SYSTEM.md)
- [Modelo de dados](docs/DATA-MODEL.md)
- [Segurança](docs/SECURITY.md)
- [Roadmap](docs/ROADMAP.md)
- [Orquestração de agentes](AGENTS.md)
- [Checkpoint](CHECKPOINT.md)
- [SPEC-00](specs/SPEC-00/README.md)

Referência de produto: AUTOZAPGFIN. O GeFin é projeto novo, não uma migração automática de código. Imagem aprovada: Art Concept v2 azul, a incorporar em `docs/design/gefin-art-concept-v2.png` após disponibilização do asset no repositório.
