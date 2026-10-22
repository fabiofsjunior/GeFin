# Roadmap — uma SPEC por sprint

| SPEC | Entrega | Gate de aceite |
|---|---|---|
| 00 | Identidade visual, protótipo HTML, contratos e infraestrutura planejada | Aprovação visual + arquitetura + threat model |
| 01 | Firebase login, contas, categorias, receitas/despesas manuais, dashboard básico | Isolamento multiusuário e CRUD E2E |
| 02 | Chat IA texto, proposta estruturada e confirmação | Nenhuma escrita sem autorização/confirmação |
| 03 | Cartões, limites, parcelas, faturas, salários e orçamento mensal | Cálculos e fechamento de fatura testados |
| 04 | IndexedDB, fila offline, sincronização e conflitos | Replays, reconexão e estado pendente testados |
| 05 | Importação CSV/OFX/PDF em lote com prévia | Deduplicação e conciliação com revisão humana |
| 06 | Open Finance via provedor autorizado | Consentimento, reconciliação, revogação e segurança |
| 07 | Áudio, anexos, análises IA, insights e relatórios | Precisão, custo e privacidade avaliados |
| 08 | Observabilidade, backups, hardening e release | Restore, carga, segurança e plano de rollback |

MVP utilizável após SPEC-02, com limites explícitos. Cada SPEC exige: documento de escopo, dependências, critérios de aceite, protótipo HTML, aprovação, implementação em branch, testes, revisão de segurança, PR e atualização do CHECKPOINT. Não avançar sem aceite.
