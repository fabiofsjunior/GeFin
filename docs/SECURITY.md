# Segurança e privacidade — requisitos de entrega

Referências: OWASP ASVS, OWASP API Security Top 10, OWASP LLM Top 10, LGPD e guia de segurança fornecido na conversa (repositório ainda não contém o PDF original). Esta matriz é proposta técnica, não certificação de segurança.

## Controles obrigatórios
1. Firebase Admin valida tokens; API aplica autorização de owner_uid em **cada** leitura/escrita, inclusive exportação, arquivos, cartões, relatórios e jobs.
2. Zod valida dados, limites, MIME real, tamanho e conteúdo de uploads; PDF/CSV/OFX em sandbox, proteção contra zip bomb, malware, SSRF e fórmulas CSV.
3. Segredos só no servidor, em secret manager/env protegida; nunca commitar .env; rotacionar tokens; menor privilégio em Supabase e serviços.
4. HTTPS obrigatório, CORS allowlist, CSP, cookies seguros quando usados, proteção CSRF conforme transporte, rate limit por usuário/IP e limites de custo da IA.
5. SQL parametrizado, nenhuma interpolação de consultas; proteção XSS por escaping/sanitização; nada de HTML arbitrário retornado pelo modelo.
6. Ferramentas de IA com schema estrito, autorização independente e confirmação para operações financeiras; conteúdo de arquivo/chat não pode alterar instruções de sistema.
7. Open Finance apenas via provedor autorizado; consentimento explícito, escopos mínimos, revogação, expiração e proteção de credenciais; nunca coletar senha bancária.
8. Logs com redaction de PII, contas, tokens e extratos; criptografia em trânsito e repouso; política de retenção, exportação e exclusão de dados.
9. Backups criptografados, restore testado, monitoração de falhas e reconciliação entre bancos.
10. CI: SAST, secret scan, dependency audit, lint, typecheck, testes de autorização multiusuário e cenários de replay/duplicação.

## Gate de segurança por SPEC
Threat model → controles aplicáveis → testes positivos e negativos → revisão de permissões → relatório de riscos residuais → aprovação. Bloqueadores críticos/altos impedem merge. Testar IDOR/BOLA, injeção, auth bypass, rate-limit, upload malicioso, prompt injection, vazamento de dados, fila offline adulterada e concorrência de importação.
