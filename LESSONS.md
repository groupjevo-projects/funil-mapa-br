# Lessons — Mapa do Prazer Masculino — Brasil

Registre uma lesson somente após observar evidência suficiente. Cada entrada deve conter data, hipótese, evidência, impacto, decisão e status.

## Lessons herdadas (já confirmadas em outro funil do mesmo código)

- **Bump da query string de versão a cada deploy que muda `index.js`/`style.css`.** Confirmada no funil em inglês (`mapa-prazer-masculino-en`) em 2026-09-13: servir `index.js?v=X` com o mesmo `X` em deploys sucessivos deixou a produção mostrando o VSL antigo por horas, porque o asset vai com `Cache-Control: public, max-age=14400`. Aplicada preventivamente aqui desde a criação do repositório (`?v=20260914-1`). Status: herdada, ainda não observada neste funil.

## Pendências abertas (não são lessons — são trabalho não feito)

Criado em 2026-09-14 como porte do funil LATAM. Faltam, todos dependentes do owner:

1. **VSLs em português.** Três players VTURB estão com id placeholder e não carregam vídeo nenhum: `PENDING-BR` (página de vendas, em `index.html` e `index.js`), `PENDING-UP1-BR` (`up1.html`), `PENDING-UP2-BR` (`upsell2.html`).
2. **Checkout do front-end.** O botão da página de vendas aponta para `#checkout-pending`; falta o link real da oferta BR.
3. **Widgets de upsell de 1 clique da Kiwify.** Os ids `PENDING-UP1-BR`, `PENDING-DS1-BR` e `PENDING-UP2-BR` precisam ser substituídos pelos ids reais das ofertas BR no painel da Kiwify.
4. ~~**Domínio.**~~ Resolvido em 2026-09-14: `mapadoprazer.site` apontado para o projeto Vercel `funil-mapa-br`, `www` com 308 para o apex. Os placeholders `DOMINIO-BR-PENDENTE` de `up1.html` e `down1.html` foram trocados pelo domínio real, e `index.html` ganhou `og:url`/`og:image`/`twitter:image`.
5. **Minutagem do CTA.** `REVEAL_AT = 358` (5:58) no `index.html` e `REVEAL_AT_SECONDS = 395` (6:35) no `up1.html` foram herdados do VSL em espanhol. Reconferir contra os VSLs em português quando existirem.
6. **Âncora do UP2.** `R$897` foi derivada da proporção do LATAM (US$147 sobre US$47), não foi definida pelo owner. Confirmar antes de publicar.
