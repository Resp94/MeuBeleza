# Documentação de domínio

Este documento define como as skills de engenharia devem consumir a documentação de domínio do repositório ao explorar o código.

## Antes de explorar, leia estes documentos

- O arquivo **`CONTEXT.md`** na raiz do repositório; ou
- O arquivo **`CONTEXT-MAP.md`** na raiz, caso exista. Ele aponta para um arquivo `CONTEXT.md` em cada contexto. Leia todos os arquivos relevantes para o assunto em questão.
- Os ADRs relevantes em **`docs/adr/`**. Em repositórios com múltiplos contextos, verifique também `src/<contexto>/docs/adr/` para encontrar decisões específicas daquele contexto.

Se algum desses arquivos não existir, **prossiga silenciosamente**. Não destaque sua ausência nem sugira sua criação antecipadamente. A skill `/domain-modeling`, acessada por meio de `/grill-with-docs` e `/improve-codebase-architecture`, cria esses documentos apenas quando termos ou decisões forem efetivamente definidos.

## Estrutura de arquivos

Repositório com contexto único, utilizado na maioria dos projetos:

```text
/
├── CONTEXT.md
├── docs/adr/
│   ├── 0001-pedidos-orientados-a-eventos.md
│   └── 0002-postgres-para-modelo-de-escrita.md
└── src/
```

Repositório com múltiplos contextos, identificado pela presença de `CONTEXT-MAP.md` na raiz:

```text
/
├── CONTEXT-MAP.md
├── docs/adr/                          ← decisões que abrangem todo o sistema
└── src/
    ├── pedidos/
    │   ├── CONTEXT.md
    │   └── docs/adr/                  ← decisões específicas do contexto
    └── faturamento/
        ├── CONTEXT.md
        └── docs/adr/
```

## Use o vocabulário do glossário

Quando uma saída mencionar um conceito do domínio — no título de uma issue, em uma proposta de refatoração, em uma hipótese ou no nome de um teste — use o termo definido em `CONTEXT.md`. Não adote sinônimos que o glossário determine explicitamente que devem ser evitados.

Caso o conceito necessário ainda não esteja no glossário, isso é um sinal de atenção: talvez esteja sendo inventado um termo que o projeto não utiliza, o que deve ser reconsiderado, ou talvez exista uma lacuna real que deve ser registrada para a skill `/domain-modeling`.

## Sinalize conflitos com ADRs

Caso uma saída contradiga um ADR existente, informe o conflito explicitamente em vez de substituir silenciosamente a decisão:

> _Contradiz o ADR-0007, que define pedidos orientados a eventos — mas vale reabrir essa decisão porque…_
