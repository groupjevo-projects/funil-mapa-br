# Lessons — Mapa do Prazer Masculino — Brasil

Registre uma lesson somente após observar evidência suficiente. Cada entrada deve conter data, hipótese, evidência, impacto, decisão e status.

## Lessons herdadas (já confirmadas em outro funil do mesmo código)

- **Bump da query string de versão a cada deploy que muda `index.js`/`style.css`.** Confirmada no funil em inglês (`mapa-prazer-masculino-en`) em 2026-09-13: servir `index.js?v=X` com o mesmo `X` em deploys sucessivos deixou a produção mostrando o VSL antigo por horas, porque o asset vai com `Cache-Control: public, max-age=14400`. Aplicada preventivamente aqui desde a criação do repositório (`?v=20260914-1`). Status: herdada, ainda não observada neste funil.

## Decisões registradas

- **2026-09-14 — "UTM de cloak" e UTMify são coisas distintas neste funil.** O funil BR não tem cloak, então não existe nenhuma checagem de `utm_campaign` para liberar a página real — tráfego sem UTM vê a página normalmente. Isso NÃO torna a UTMify dispensável: ela é atribuição, não gate. O script em `index.html` captura as UTMs de entrada e as cola no link da Payt; o webhook da Payt no dashboard BRL da UTMify fecha o laço. Sem `data-utmify-replace-links="payt.site"` as vendas chegam sem campanha e o CPA por criativo se perde. Decisão do owner em 2026-09-14: manter. Não remover o script por parecer resíduo de cloak.

## Pendências abertas (não são lessons — são trabalho não feito)

Criado em 2026-09-14 como porte do funil LATAM. Faltam, todos dependentes do owner:

1. **VSLs dos upsells em português.** Dois players VTURB seguem com id placeholder: `PENDING-UP1-BR` (`up1.html`) e `PENDING-UP2-BR` (`upsell2.html`). O da página de vendas já foi conectado em 2026-09-14 (`69c1e55d137969468e801497`).
2. ~~**Checkout do front-end.**~~ Resolvido em 2026-09-14: `https://payt.site/4pC2KXv` (Payt), que redireciona 302 para `checkout.payt.com.br` preservando as UTMs.
3. **Widgets de upsell de 1 clique da Kiwify.** Os ids `PENDING-UP1-BR`, `PENDING-DS1-BR` e `PENDING-UP2-BR` precisam ser substituídos pelos ids reais das ofertas BR no painel da Kiwify.
4. ~~**Domínio.**~~ Resolvido em 2026-09-14: `mapadoprazer.site` apontado para o projeto Vercel `funil-mapa-br`, `www` com 308 para o apex. Os placeholders `DOMINIO-BR-PENDENTE` de `up1.html` e `down1.html` foram trocados pelo domínio real, e `index.html` ganhou `og:url`/`og:image`/`twitter:image`.
5. **Minutagem do CTA do upsell.** `REVEAL_AT_SECONDS = 395` (6:35) no `up1.html` segue herdado do VSL em espanhol; reconferir quando o VSL do UP1 em português existir. O da página de vendas já foi definido pelo owner em 5:46 (`REVEAL_AT = 346`).
6. **Âncora do UP2.** `R$897` foi derivada da proporção do LATAM (US$147 sobre US$47), não foi definida pelo owner. Confirmar antes de publicar.
