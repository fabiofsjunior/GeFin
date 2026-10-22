# Design system — GeFin / Art Concept v2

## Referência aprovada
Conceito visual azul inspirado nos screenshots AUTOZAPGFIN (desktop e mobile) e no mockup GeFin v2 aprovado. Asset original PNG ainda não versionado: destino planejado `docs/design/gefin-art-concept-v2.png`. Não substituir por arte genérica.

## Tokens iniciais (sujeitos a validação no protótipo)
- Primary #2878F0; primary-hover #175AC9; accent #60A5FA; background #F6F8FA.
- Navy #0F172A; surface #FFFFFF; text #111827; muted #64748B; border #E2E8F0.
- Error #EF4444; warning #F59E0B; info #06B6D4; success #22C55E somente estado semântico, nunca identidade principal.
- Font Inter (fallback system-ui); escala modular, peso 400/500/600/700; ícones Lucide.
- Cards radius 16–20px; inputs e botões com alvo >=44x44px; espaçamento em múltiplos de 4px.

## Layout
- Desktop >=1024px: sidebar, header, dashboard com KPIs, gráficos, transações e chat em painel flutuante.
- Tablet 768–1023px: sidebar compacta e grids reduzidos.
- Mobile <768px: login → chat como home; barra inferior ou menu acessível para dashboard, cartões, relatórios e configurações; safe-area e teclado virtual; largura fluida, viewport 390x693 como referência e não dimensão fixa.
- Estados obrigatórios: loading, vazio, erro, offline, sincronizando, sincronizado, conflito, duplicata suspeita, confirmação IA e autorização expirada.
- Dark mode opcional; contraste WCAG 2.2 AA, foco visível, navegação por teclado, labels e suporte a redução de movimento.

## Aprovação
Antes de cada SPEC funcional, entregar HTML responsivo navegável com dados fictícios, screenshots mobile/desktop, testes de usabilidade e aprovação explícita. Usar skill Impeccable quando disponível; ausência da skill não dispensa os critérios de design.
