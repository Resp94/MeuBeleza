# Rastreador de issues: GitHub

As issues e os PRDs deste repositório ficam armazenados como issues do GitHub. Use a CLI `gh` para todas as operações.

## Convenções

- **Criar uma issue**: `gh issue create --title "..." --body "..."`. Use um heredoc para corpos com várias linhas.
- **Ler uma issue**: `gh issue view <número> --comments`, filtrando os comentários com `jq` e obtendo também os rótulos.
- **Listar issues**: `gh issue list --state open --json number,title,body,labels,comments --jq '[.[] | {number, title, body, labels: [.labels[].name], comments: [.comments[].body]}]'`, usando os filtros `--label` e `--state` adequados.
- **Comentar em uma issue**: `gh issue comment <número> --body "..."`
- **Adicionar ou remover rótulos**: `gh issue edit <número> --add-label "..."` / `--remove-label "..."`
- **Fechar uma issue**: `gh issue close <número> --comment "..."`

Determine o repositório por meio de `git remote -v` — a CLI `gh` faz isso automaticamente quando executada dentro de um clone.

## Pull requests como superfície de triagem

**PRs como superfície de solicitações: não.** _(Altere para `sim` caso este repositório trate PRs externos como solicitações de funcionalidades; a skill `/triage` consulta esta configuração.)_

Quando configuradas como `sim`, as PRs passam pelos mesmos rótulos e estados das issues, usando os comandos equivalentes de `gh pr`:

- **Ler uma PR**: `gh pr view <número> --comments` e `gh pr diff <número>` para visualizar as alterações.
- **Listar PRs externas para triagem**: `gh pr list --state open --json number,title,body,labels,author,authorAssociation,comments`. Depois, mantenha apenas aquelas cujo `authorAssociation` seja `CONTRIBUTOR`, `FIRST_TIME_CONTRIBUTOR` ou `NONE`. Desconsidere `OWNER`, `MEMBER` e `COLLABORATOR`.
- **Comentar, rotular ou fechar**: use `gh pr comment`, `gh pr edit --add-label`/`--remove-label` e `gh pr close`.

O GitHub utiliza o mesmo espaço de numeração para issues e PRs. Portanto, uma referência isolada como `#42` pode representar qualquer uma delas. Verifique primeiro com `gh pr view 42` e, caso não seja uma PR, use `gh issue view 42`.

## Quando uma skill disser “publicar no rastreador de issues”

Crie uma issue no GitHub.

## Quando uma skill disser “obter o ticket relevante”

Execute `gh issue view <número> --comments`.

## Operações de orientação

Estas operações são utilizadas pela skill `/wayfinder`. O **mapa** é uma única issue que possui outras issues como **tickets filhos**.

- **Mapa**: uma única issue com o rótulo `wayfinder:map`, contendo em seu corpo as seções de notas, decisões tomadas até o momento e pontos de incerteza. Crie-a com `gh issue create --label wayfinder:map`.
- **Ticket filho**: uma issue vinculada ao mapa como sub-issue do GitHub, usando `gh api` no endpoint de sub-issues. Quando sub-issues não estiverem disponíveis, adicione o ticket filho a uma lista de tarefas no corpo do mapa e coloque `Parte de #<mapa>` no início do corpo do ticket filho. Use um dos rótulos `wayfinder:<tipo>`, em que o tipo pode ser `research`, `prototype`, `grilling` ou `task`. Depois de reivindicado, o ticket deve ser atribuído ao desenvolvedor responsável.
- **Bloqueio**: use as dependências nativas de issues do GitHub como representação canônica e visível na interface. Adicione uma dependência com `gh api --method POST repos/<proprietário>/<repositório>/issues/<filho>/dependencies/blocked_by -F issue_id=<id-do-bloqueador>`. O valor `<id-do-bloqueador>` deve ser o `id` numérico do banco de dados, obtido por `gh api repos/<proprietário>/<repositório>/issues/<número> --jq .id`, e não o número `#<número>` nem o `node_id`. O GitHub informa os bloqueadores abertos por meio de `issue_dependencies_summary.blocked_by`. Quando dependências nativas não estiverem disponíveis, use como alternativa uma linha `Bloqueado por: #<número>, #<número>` no início do corpo do ticket. Um ticket deixa de estar bloqueado quando todos os seus bloqueadores são fechados.
- **Consulta da fronteira de trabalho**: liste os tickets filhos abertos do mapa usando `gh issue list --state open`, limitando a consulta às sub-issues ou à lista de tarefas do mapa. Desconsidere os tickets que tenham um bloqueador aberto ou uma pessoa atribuída. O primeiro ticket restante na ordem do mapa é o próximo a ser trabalhado.
- **Reivindicar um ticket**: execute `gh issue edit <número> --add-assignee @me`. Essa deve ser a primeira operação de escrita da sessão.
- **Resolver um ticket**: publique a resposta com `gh issue comment <número> --body "<resposta>"`, feche o ticket com `gh issue close <número>` e acrescente às decisões do mapa uma referência ao contexto, incluindo um gist e seu link.
