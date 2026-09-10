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
1. O prompt do scheduled task carrega um retrato congelado dos 4 padrões e das 4 frases seed (ver `trigger-prompt.md`, v2). Não faz `git clone` nem lê ficheiros no arranque — o desafio aparece sem passos de ferramenta.
2. Escolhe o padrão do dia por rotação simples: `((dia_do_ano - 1) mod 4) + 1`.
3. O desafio diário usa sempre uma frase gerada de novo, curta e verosímil no contexto do Nando, variando setor/papel/formato; nunca reutiliza uma frase dos últimos 14 dias nem as 4 frases de referência do artigo. A repetição de exemplos fica reservada à revisão semanal (requisito 6), onde é intencional para testar retenção.
4. Apresenta a frase e faz 1 a 2 perguntas de desconstrução diretas (no estilo do próprio artigo: "Que X é? Comparado com quê?"). A partir do 2.º dia inclui uma linha de recall com o teste prático do padrão da véspera.
5. Espera a resposta do Nando na mesma sessão e dá feedback compacto — no máximo 4 linhas (Certo / Falhou / Reescrita / Fixa), uma frase cada, específico à resposta dele.
6. Revisão relâmpago nos dias 7, 14, 21, ... após 2026-09-10: 4 frases baralhadas, uma por padrão, o Nando identifica cada uma; substitui o desafio normal desse dia. Aqui as frases são reutilizadas de propósito (referência do artigo e desafios anteriores) para testar se o reconhecimento ficou retido.

## Sincronização
- `conteudo/padroes.md` e `conteudo/desafios-seed.md` continuam a ser a fonte da verdade em SDD.
- Uma alteração a esses ficheiros só chega ao desafio diário depois de atualizar o bloco em `trigger-prompt.md` e correr um `update_trigger` com o novo conteúdo. É um passo manual e deliberado (trade da v2: arranque mais rápido em troca de sincronização não automática).

## Requisitos não-funcionais
- Mensagem curta (a frase + pergunta cabem num ecrã de telemóvel sem scroll excessivo).
- Em português europeu (pt_PT), tom direto, sem os próprios padrões que o projeto ensina a detetar (a mensagem não deve ela própria estar "insuflada").
- Não depende de nenhuma infraestrutura além do GitHub (leitura pública do repositório) e do scheduled task nativo.

## Critérios de aceite
- ✓ Cada execução do scheduled task cobre exatamente um dos 4 padrões, em rotação, sem repetir o padrão do dia anterior.
- ✓ A frase de exemplo enviada não é idêntica a nenhuma das 3 execuções anteriores.
- ✓ A mensagem inclui pelo menos uma pergunta de desconstrução direta.
- ✓ O desafio aparece sem passos de ferramenta visíveis (sem clone, sem leitura de ficheiros).
- ✓ O feedback tem no máximo 4 linhas e é específico à resposta do Nando (não uma explicação genérica do padrão).
- ✓ A partir do 2.º dia, a mensagem do desafio traz a linha de recall do padrão da véspera.

## Restrições técnicas
- Scheduled task criado via `create_trigger` (nunca `CronCreate`, que não sobrevive ao fim da sessão).
- Repositório público em `github.com/Nankov-ai/linguagem-critica` como fonte da verdade em SDD; o trigger em produção não o lê em runtime (ver "Sincronização").
- Sem build step, sem dependências — o conteúdo é apenas Markdown.
- Trigger em produção: `trig_016UGL2qZHGnm38qaNjw2hYx`, `0 12 * * *` Europe/Lisbon.
