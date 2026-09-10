# Banco de Padrões — Linguagem Insuflada / Gerada por IA

Fonte primária: "Usaste a IA para escrever o post? Ótimo... Revê a linguagem!" (Duarte Drumond, LinkedIn, 14/08/2026). Ver `fontes.md`.

Contexto do artigo: entre 2022 e 2024 os erros de LLMs eram fáceis de detetar (alucinações completas, informação inventada). Hoje, com muito mais capacidade, o problema mudou: o texto é gramaticalmente correto, o tom é corporativo, nada ofende ninguém — mas muitas vezes não acrescenta conteúdo real. Os 4 padrões abaixo são as formas mais comuns dessa "eloquência vazia".

---

## Padrão 1 — Vocabulário insuflado

**Definição:** palavras que "agigantam" uma frase (transformador, robusto, estratégico, disruptivo, holístico, impactante, diferenciador, revolucionário, exponencial, poderoso, acionável, escalável) usadas soltas, sem ligação concreta ao sujeito da frase.

**Importante:** estas palavras não são proibidas. Uma infraestrutura pode ser genuinamente robusta; retirar o adjetivo certo tira força à frase. O problema é quando são "despejadas" sem consideração pelo sujeito.

**Sinais:**
- Vários adjetivos "grandes" na mesma frase, sem um facto concreto a suportá-los.
- A frase soa bem lida uma vez, mas ninguém consegue dizer o que significa na prática.

**Teste prático de deteção:** reler a frase e fazer perguntas concretas sobre cada elemento (Que abordagem é esta? O que confere robustez? Qual estratégia, especificamente? Resultados comparados com quê?). Se a frase perde o impacto depois de 1 a 2 perguntas, a força estava no vocabulário, não no conteúdo.

**Exemplo do artigo:** "Uma abordagem robusta e estratégica permite alcançar resultados significativos." → decompõe-se em 2 nomes abstratos (abordagem, resultados), 3 adjetivos (robusta, estratégica, significativos), 2 verbos (permite, alcançar) e nenhum facto verificável.

---

## Padrão 2 — Anglicismos traduzidos literalmente

**Definição:** expressões inglesas comuns em conteúdo empresarial (a maior fonte de treino dos LLMs) traduzidas literalmente para português, mas que não são naturais em Portugal.

**Exemplos:** "desbloquear o potencial" (unlock potential), "abraçar a mudança" (embrace change), "navegar a complexidade" (navigate complexity), "moldar o futuro" (shape the future), "quebrar barreiras" (break barriers), "embarcar numa jornada" (embark on a journey), "no ambiente empresarial competitivo de hoje" (in today's competitive business environment).

**Sinais:**
- Uma expressão isolada pode passar despercebida; três ou mais no mesmo texto parecem "uma brochura traduzida à pressa".
- Pesquisar a expressão exata no Google devolve dezenas de textos com fraseado quase idêntico.

**Teste prático de deteção:** contar quantas destas expressões aparecem no mesmo texto. Duas ou mais é sinal forte. Pesquisar a frase entre aspas para confirmar se é uma fórmula recorrente.

---

## Padrão 3 — A "cerimónia" antes da informação (abuso de transições)

**Definição:** a IA tende a anunciar a informação em vez de a dar diretamente ("Antes de explorar esta questão em maior profundidade, importa compreender o contexto que lhe está subjacente" em vez de simplesmente explicar o contexto), e a abusar de palavras de transição ("Importa salientar que...", "Vale a pena destacar...", "Neste contexto...", "Dito isto...", "Em última análise...").

**Importante:** palavras de transição não são más — ajudam a ligar ideias e tornam a leitura mais fácil. O problema é a densidade: humanos são tendencialmente mais "desleixados" nisto, por isso um texto com transições em quase todos os parágrafos soa como "ter um narrador a avisar que vem aí um parágrafo".

**Sinais:**
- Cada parágrafo começa por anunciar o que vai fazer, em vez de simplesmente o fazer.
- Muitas frases de transição por texto curto (mais do que seria natural em fala/escrita humana equivalente).

**Teste prático de deteção:** sublinhar todas as palavras/expressões de transição do texto. Se aparecem no início de quase todos os parágrafos, é sinal do padrão.

---

## Padrão 4 — Palha e nominalização

**Definição:** dois problemas relacionados. (a) "Texto de palha": conteúdo excessivo, repetitivo ou vazio, usado só para aumentar o tamanho do texto sem acrescentar nada útil ao leitor. (b) Nominalização: o verbo principal raramente aparece sozinho — é transformado num substantivo "apoiado" por um verbo cerimonioso.

**Exemplos de nominalização:** analisar → realizar uma análise; decidir → tomar uma decisão; implementar → proceder à implementação; melhorar → contribuir para a melhoria; usar → fazer uso de.

**Sinais:**
- Frases que, ao serem cortadas, perdem zero informação (só perdem palavras).
- Verbos "escondidos" atrás de um substantivo e de um verbo de apoio.

**Teste prático de deteção:** tentar cortar a frase ao essencial e ver se perde algum facto. Se não perde nada, era palha. Depois, procurar o par nome+verbo-de-apoio e substituir pelo verbo direto.

**Exemplo do artigo — progressão de reescrita:**
1. Original: "A implementação desta solução poderá contribuir para a melhoria da produtividade."
2. Corte de palha: "A solução pode aumentar a produtividade."
3. Com resultado explícito (melhor versão): "A solução reduziu o tempo de preparação do relatório para três horas."

**Regra geral do artigo:** o texto só deve ficar maior se isso acrescentar algo útil ao leitor. Caso contrário, corta-se a palha.
