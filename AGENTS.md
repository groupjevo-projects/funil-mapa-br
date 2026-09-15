# Funil Mapa do Prazer Masculino — Brasil

Repositório de produção do funil `mapa-prazer-masculino-br`. Site estático servido pela Vercel.

## O que este repositório é

Portado a partir de `funil-mapa-latam` (`mapa-prazer-masculino-latam`) e adaptado para o mercado brasileiro: idioma `pt-BR`, escada de preços em BRL, `offer_id` de tracking `br`.

Domínio de produção: `https://mapadoprazer.site` (apex). `www` redireciona 308 para o apex. DNS na Hostinger (nameservers `lunar`/`solar.dns-parking.com`), sem Cloudflare na frente. Projeto Vercel: `funil-mapa-br`, deploy automático a cada push em `main`.

**Não há cloak neste funil.** Por decisão do owner, este funil não tem página isca (`/w`), não tem variantes white dos upsells (`/up1w`, `/up2w`) e não tem Worker de cloaking na Cloudflare. Todo o tráfego vê a página real. Se um dia isso mudar, é uma decisão nova do owner — não replique o cloak do LATAM por analogia.

## Estrutura

| Rota       | Arquivo         | Papel                                                     |
|------------|-----------------|-----------------------------------------------------------|
| `/`        | `index.html` + `index.js` + `style.css` | Gate de toque + página de vendas com VSL |
| `/up1`     | `up1.html`      | Upsell 1 — A Cavalgada Proibida (chat guiado interativo Sofia Villar) |
| `/down1`   | `down1.html`    | Downsell 1 — A Cavalgada Proibida (condição especial R$97)       |
| `/up2`, `/upsell2` | `upsell2.html` | Upsell 2 — Método das Deusas (chat guiado)         |
| `/tks`     | `tks.html`      | Obrigado / instruções de acesso                            |

`index.js` é um bundle React já buildado. Não há toolchain de build neste repositório: alterações de copy e de comportamento são feitas editando o bundle minificado diretamente e validando com `node --check index.js`.

## Escada de preços

Front-end em teste A/B (R$47 / R$67 / R$97, definido no nível da oferta — não aparece em copy na página) → UP1 R$147 → DS1 R$97 (âncora R$147) → UP2 R$297 (5x de R$59,40, âncora R$897).

## Tracking

Eventos vão para a tabela `funnel_events` no Supabase com `offer_id: 'br'`. Contrato de eventos: `docs/architecture/analytics-event-contract.md` no repositório orquestrador (`group-jevo-funnel-ops`). Não renomeie nem reutilize um `event_type` com outro significado.

## Cache

Sempre que alterar `index.js` ou `style.css`, bump a query string de versão nas duas referências do `<head>` do `index.html` (`?v=YYYYMMDD-N`) no mesmo commit. Os assets são servidos com `max-age=14400`; sem o bump, parte do tráfego continua com o bundle antigo por até 4 horas.

## Pendências antes de ir ao ar

Estão listadas em `LESSONS.md` e no registro do funil em `registry/funnels/mapa-prazer-masculino-br/AGENTS.md` do orquestrador. Em resumo: VSLs em português, ids de widget Kiwify das ofertas BR, domínio e deploy.
