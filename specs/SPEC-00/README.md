# SPEC-00 — Fundação visual e técnica

**Status:** documentação pronta para prototipagem; implementação não iniciada.

## Objetivo
Consolidar identidade GeFin azul e a experiência responsiva inspirada nos anexos aprovados. Criar protótipo HTML navegável (sem dados reais), depois iniciar fundação técnica apenas mediante aceite.

## Telas prototipadas
1. Login Firebase Google (visual; autenticação real na implementação).
2. Chat mobile inicial: bolhas, envio de texto, anexos/áudio visuais, prévia e confirmação.
3. Dashboard mobile: saldo, receitas, despesas, transações e status de sincronização.
4. Cartões: limites, consumo e faturas.
5. Relatórios: período, categoria e gráficos.
6. Configurações: perfil, consentimentos, segurança, exportação/exclusão.
7. Desktop: sidebar, KPIs, gráficos, transações e chat flutuante.

## Critérios de aceite
- Layout coerente com Art Concept v2, sem verde como cor principal.
- Mobile 320px–430px, tablet e desktop >=1024px; sem overflow horizontal.
- Navegação clicável entre telas; estados offline/pendente/erro; dados sintéticos.
- Contraste e navegação por teclado; sem bibliotecas externas obrigatórias no protótipo.
- Aprovação explícita do usuário registrada em CHECKPOINT antes de implementar.

## Fora de escopo
Open Finance real, integração de IA, pagamentos, persistência financeira e produção.

## Tarefas do orquestrador
Preparar HTML em `prototypes/spec-00/index.html`, screenshots e checklist; abrir branch SPEC-00; solicitar aprovação; somente depois implementar scaffold Next.js/Fastify, CI, Firebase e banco seguindo docs.
