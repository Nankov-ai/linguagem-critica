# Linguagem Crítica

Repositório de conteúdo para treinar, de forma ativa e diária, a deteção de linguagem "insuflada", vazia ou tipicamente gerada por IA em textos que o Nando recebe (LinkedIn, emails, propostas, relatórios).

Construído seguindo a metodologia **Spec-Driven Development (SDD)**: cada padrão de deteção tem uma spec antes de entrar no banco de conteúdo, tal como praticado em `spec-driven-development` (repositório do curso SDD).

## Estrutura

- `spec.md` — spec v1 deste projeto: objetivo, escopo, requisitos e critérios de aceite do sistema de desafios diários.
- `conteudo/padroes.md` — banco de padrões de deteção (definição, sinais, teste prático, exemplo). É a fonte da verdade usada pelo scheduled task para gerar os desafios diários.
- `conteudo/desafios-seed.md` — desafios iniciais extraídos diretamente do artigo fonte (usados nos primeiros dias, antes do banco crescer com exemplos gerados).
- `fontes.md` — fontes usadas para construir `padroes.md`, com data e link.

## Convenções

- Cada padrão novo em `padroes.md` precisa de: definição, 2 a 4 sinais concretos, um teste prático de deteção (não uma opinião vaga) e pelo menos um exemplo real ou verosímil.
- O scheduled task "Desafio Diário de Linguagem" lê este repositório a cada execução (não guarda cópia local persistente) para que atualizações a `padroes.md` se reflitam no dia seguinte sem alterar a rotina.
- Adicionar um novo padrão é um incremento SDD como outro qualquer: descrever o padrão em `padroes.md` primeiro, só depois ajustar o prompt do scheduled task se for necessário.
