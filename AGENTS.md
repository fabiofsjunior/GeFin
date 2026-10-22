# AGENTS — Contrato do orquestrador

## Regras gerais
1. Ler README, CHECKPOINT, SPEC ativa e SECURITY antes de agir.
2. Trabalhar exclusivamente em branch `spec/NN-descricao`; não alterar `main` sem PR e aprovação.
3. Uma SPEC por sprint; toda UI exige protótipo HTML funcional e aprovação antes do código final.
4. Entregar código pequeno, testável, documentado, acessível e responsivo. Não assumir que testes passaram sem executá-los.
5. Cada PR deve incluir riscos, migrações, rollback, testes e screenshots desktop/mobile.
6. Atualizar CHECKPOINT após cada etapa e registrar decisões no documento da SPEC.
7. Não registrar segredos, dados bancários reais ou tokens em issues, logs, prompts ou repositório.

## Equipe virtual / competências
- **Orquestrador**: planeja dependências, distribui tarefas, consolida evidências e aprova gates documentais.
- **Produto/Analista**: critérios de aceite, fluxos financeiros e requisitos LGPD.
- **UI/UX**: skill Impeccable quando disponível; tokens, acessibilidade WCAG 2.2 AA, HTML prototipado e testes de usabilidade.
- **Frontend**: Next.js, PWA, IndexedDB, formulários e estados offline/erro.
- **Backend**: Fastify, validação de entrada, autorização, idempotência e API versionada.
- **Dados**: PostgreSQL, Supabase, RLS, migrações e outbox/inbox.
- **IA**: parsing estruturado, revisão humana, segurança contra prompt injection e testes de ferramentas.
- **QA**: unitários, integração, E2E Playwright, sincronização, concorrência e acessibilidade.
- **Security**: skills de revisão de segurança disponíveis + OWASP ASVS, API Security Top 10 e guia de segurança do projeto quando anexado ao repositório.
- **DevOps**: CI/CD, túnel, monitoramento, backup, restauração e deploy.

## Definition of Done
SPEC e protótipo aprovados; critérios de aceite demonstrados; lint/typecheck/test/build sem falhas; cobertura de fluxos críticos; revisão de segurança e autorização multiusuário; migração reversível; documentação e CHECKPOINT atualizados; PR revisado. Não alegar blindagem absoluta.
