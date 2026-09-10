# Linguagem Crítica

Repositório de conteúdo para treinar, de forma ativa e diária, a deteção de linguagem "insuflada", vazia ou tipicamente gerada por IA em textos que o Nando recebe (LinkedIn, emails, propostas, relatórios).

Construído seguindo a metodologia **Spec-Driven Development (SDD)**: cada padrão de deteção tem uma spec antes de entrar no banco de conteúdo, tal como praticado em `spec-driven-development` (repositório do curso SDD).

## Estrutura

- `spec.md` — spec deste projeto: objetivo, escopo, requisitos e critérios de aceite do sistema de desafios diários.
- `conteudo/padroes.md` — banco de padrões de deteção (definição, sinais, teste prático, exemplo). É a fonte da verdade; o seu conteúdo é copiado para `trigger-prompt.md`.
- `conteudo/desafios-seed.md` — as 4 frases do artigo fonte, uma por padrão. Já não alimentam o desafio diário; servem de calibração e de banco para a revisão semanal.
- `fontes.md` — fontes usadas para construir `padroes.md`, com data e link.
- `trigger-prompt.md` — prompt do scheduled task (v3: conteúdo inlined, feedback de 4 linhas, recall diário, revisão semanal, frases diárias sempre novas).

## Convenções

- Cada padrão novo em `padroes.md` precisa de: definição, 2 a 4 sinais concretos, um teste prático de deteção (não uma opinião vaga) e pelo menos um exemplo real ou verosímil.
- O scheduled task "Desafio Diário de Linguagem" (`trig_016UGL2qZHGnm38qaNjw2hYx`, `0 12 * * *` Europe/Lisbon) carrega o conteúdo dos padrões no próprio prompt, por velocidade. Alterações a `padroes.md` só chegam ao desafio depois de sincronizar `trigger-prompt.md` e correr `update_trigger` (ver `spec.md`, "Sincronização").
- Adicionar um novo padrão é um incremento SDD como outro qualquer: descrever o padrão em `padroes.md` primeiro, depois refletir no bloco de `trigger-prompt.md` e sincronizar o trigger.
- O desafio diário usa sempre frases geradas de novo; a repetição de exemplos vive só na revisão semanal, para testar retenção.
