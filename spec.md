# Spec — Desafio Diário de Linguagem Crítica (v1)

## Objetivo (por quê)
Treinar o Nando a desconstruir, detetar e ser crítico perante linguagem "insuflada" ou tipicamente gerada por IA em textos que lhe partilham (LinkedIn, propostas, relatórios), de forma automática e espontânea — sem ter de pensar conscientemente em aplicar a técnica cada vez que lê algo.

## Contexto
Baseado no artigo "Usaste a IA para escrever o post? Ótimo... Revê a linguagem!" (Duarte Drumond, LinkedIn, 14 de agosto de 2026), que identifica 4 padrões de linguagem vazia comuns em texto gerado ou fortemente assistido por IA. O v1 cobre apenas este artigo (Nível 2 da série); o Nível 1 (tiques de escrita: travessões, "não é X, é Y") fica fora de escopo até ser partilhado.

## Escopo
- Um banco de padrões de deteção em `conteudo/padroes.md`, cada um com definição, sinais e um teste prático.
- Um scheduled task diário ("Desafio Diário de Linguagem") que envia ao Nando, numa sessão própria:
  1. Uma frase real ou verosímil que contém um dos padrões (rotação pelos 4 padrões, um por dia, repetindo o ciclo).
  2. Um convite direto para a desconstruir (ex: "Consegues explicar esta frase? Que abordagem é? Comparado com quê?").
  3. Após a resposta do Nando nessa mesma sessão, feedback imediato: o que ele acertou, o que falhou, e a versão reescrita sem o padrão.
- Rotação: dia 1 vocabulário insuflado, dia 2 anglicismos traduzidos, dia 3 cerimónia/transição, dia 4 palha e nominalização, dia 5 repete o ciclo com uma frase nova (não repetir a mesma frase em ciclos diferentes).

## Fora de escopo (v1)
- Interface web ou jogo (ex: ao estilo SDD Quest) — decidido explicitamente que a entrega é só por scheduled task.
- Conteúdo do Nível 1 do artigo (tiques de escrita) — entra como incremento futuro se o Nando partilhar esse artigo.
- Pontuação acumulada, streaks ou histórico persistente entre execuções.
- Deteção automática de linguagem insuflada em textos que o Nando cole — isto é sobre treinar o próprio Nando a detetar, não construir um detetor automático de texto.

## Requisitos funcionais
1. O scheduled task lê `conteudo/padroes.md` (e `conteudo/desafios-seed.md` nos primeiros 4 dias) diretamente do GitHub a cada execução.
2. Escolhe o padrão do dia por rotação simples (dia do ano módulo 4, ou sequencial a partir da data de criação do trigger).
3. Gera ou reutiliza uma frase de exemplo alinhada com o padrão escolhido, evitando repetir literalmente uma frase já enviada nos últimos 4 dias.
4. Apresenta a frase e faz 1 a 2 perguntas de desconstrução diretas (no estilo do próprio artigo: "Que X é? Comparado com quê?").
5. Espera a resposta do Nando na mesma sessão e dá feedback concreto (correto/incorreto + explicação + reescrita sem o padrão).

## Requisitos não-funcionais
- Mensagem curta (a frase + pergunta cabem num ecrã de telemóvel sem scroll excessivo).
- Em português europeu (pt_PT), tom direto, sem os próprios padrões que o projeto ensina a detetar (a mensagem não deve ela própria estar "insuflada").
- Não depende de nenhuma infraestrutura além do GitHub (leitura pública do repositório) e do scheduled task nativo.

## Critérios de aceite
- ✓ Cada execução do scheduled task cobre exatamente um dos 4 padrões, em rotação, sem repetir o padrão do dia anterior.
- ✓ A frase de exemplo enviada não é idêntica a nenhuma das 3 execuções anteriores.
- ✓ A mensagem inclui pelo menos uma pergunta de desconstrução direta.
- ✓ Quando o Nando responde na mesma sessão, recebe feedback específico à sua resposta (não uma explicação genérica do padrão).

## Restrições técnicas
- Scheduled task criado via `create_trigger` (nunca `CronCreate`, que não sobrevive ao fim da sessão).
- Repositório público em `github.com/Nankov-ai/linguagem-critica`, lido em cada execução via `git clone` raso (não requer autenticação para leitura).
- Sem build step, sem dependências — o conteúdo é apenas Markdown.
