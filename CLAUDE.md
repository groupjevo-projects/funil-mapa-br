@AGENTS.md

## Claude Code

Antes de mexer neste funil, leia também o `AGENTS.md` do repositório orquestrador (`group-jevo-funnel-ops`) e o registro do funil em `registry/funnels/mapa-prazer-masculino-br/`.

Regras que valem especificamente aqui:

- Não faça push nem deploy sem pedido explícito do owner.
- Não replique o cloak do funil LATAM neste repositório. A ausência de cloak é uma decisão do owner, não um esquecimento.
- Nunca edite os outros funis (`funil-mapa-latam`, `funil-mapa-en`, `funil-chave-deusa-br`) a partir de uma tarefa que começou aqui.
- Ao alterar `index.js`, valide com `node --check index.js` antes de commitar e bump a query string `?v=` do `index.html` no mesmo commit.
