# Linguagem Crítica

Repositório de conteúdo para treinar, de forma ativa e diária, a deteção de linguagem "insuflada", vazia ou tipicamente gerada por IA em textos que o Nando recebe (LinkedIn, emails, propostas, relatórios).

Construído seguindo a metodologia **Spec-Driven Development (SDD)**: cada padrão de deteção tem uma spec antes de entrar no banco de conteúdo, tal como praticado em `spec-driven-development` (repositório do curso SDD).

## Estrutura

- `spec.md` — spec v1 deste projeto: objetivo, escopo, requisitos e critérios de aceite do sistema de desafios diários.
- `conteudo/padroes.md` — banco de padrões de deteção (definição, sinais, teste prático, exemplo). É a fonte da verdade usada pelo scheduled task para gerar os desafios diários.
- `conteudo/desafios-seed.md` — desafios iniciais extraídos diretamente do artigo fonte (usados nos primeiros dias, antes do banco crescer com exemplos gerados).
- `fontes.md` — fontes usadas para construir `padroes.md`, com data e link.
- `trigger-prompt.md` — prompt do scheduled task (v2: conteúdo inlined, feedback de 4 linhas, recall diário, revisão semanal).

## Convenções

- Cada padrão novo em `padroes.md` precisa de: definição, 2 a 4 sinais concretos, um teste prático de deteção (não uma opinião vaga) e pelo menos um exemplo real ou verosímil.
- O scheduled task "Desafio Diário de Linguagem" carrega o conteúdo dos padrões no próprio prompt (v2, por velocidade). Alterações a `padroes.md` só chegam ao desafio depois de sincronizar `trigger-prompt.md` e correr `update_trigger` (ver `spec.md`, "Sincronização").
- Adicionar um novo padrão é um incremento SDD como outro qualquer: descrever o padrão em `padroes.md` primeiro, depois refletir no bloco de `trigger-prompt.md` e sincronizar o trigger.
