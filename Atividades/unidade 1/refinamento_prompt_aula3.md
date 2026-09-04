# Atividade - Refinamento de Prompts

## Identificação
- Nome: Jhonathan de Moura Santos (RGM 32813589) e Melissa Aragão Leite (RGM 33999554)
- Turma: Tendências em Ciência da Computação
- Data: 03/09
- Ferramenta de IA utilizada: Claude (Anthropic)

---

## Problema escolhido

### Contexto
Somos estudantes do primeiro ano de Ciência da Computação. Já estudamos vetores/arrays e estruturas de repetição (for/while), mas ainda não vimos formalmente algoritmos de busca nem o conceito de complexidade assintótica (notação Big-O).

### Problema
Muitos colegas confundem busca linear com busca binária e não entendem por que a busca binária é considerada "mais eficiente", nem sob qual condição ela pode ser usada. Precisamos de uma explicação didática para revisar antes da prova de complexidade de algoritmos.

### Objetivo
Utilizar a IA para obter uma explicação clara sobre **busca binária**, com exemplo numérico passo a passo, comparação com a busca linear e verificação de compreensão — sem simplesmente pedir "faça meu resumo".

---

## Prompt 1

### Prompt
```text
Explique o que é busca binária.
```

### Resultado
```text
Busca binária é um algoritmo de busca eficiente usado para encontrar um
elemento em uma lista ordenada. Ele funciona dividindo repetidamente o
intervalo de busca pela metade: compara o elemento do meio com o valor
procurado; se forem iguais, a busca termina; se o valor procurado for
menor, a busca continua na metade esquerda; se for maior, continua na
metade direita. Esse processo se repete até encontrar o elemento ou até
o intervalo ficar vazio. A complexidade da busca binária é O(log n),
o que a torna muito mais rápida que a busca linear, especialmente em
listas grandes. É amplamente utilizada em bancos de dados, estruturas
de dados e sistemas de busca.
```

### Análise
- O objetivo ficou claro? Parcialmente — a IA "adivinhou" que queríamos uma explicação geral, mas não sabia para quem nem com qual finalidade.
- A IA compreendeu o público? Não. A resposta usa "O(log n)" sem explicar o que é logaritmo nem complexidade assintótica.
- Houve informações genéricas? Sim — cita "bancos de dados e sistemas de busca" sem detalhar.
- Faltaram exemplos? Sim, não há nenhum exemplo numérico.
- Alguma informação precisa ser verificada? A pré-condição mais importante do algoritmo — **o vetor precisa estar ordenado** — nem é mencionada.
- Nível de profundidade: raso para quem nunca viu o assunto, mas também não aprofunda o suficiente para quem já entende programação.

---

## Prompt 2

### Alterações realizadas
- Papel: "Atue como professor de Ciência da Computação."
- Contexto: parcial (menciona o nível dos estudantes dentro do próprio pedido).
- Objetivo: implícito em "explicar para estudantes iniciantes".
- Público: primeiro ano, já conhece vetores e laços, nunca viu algoritmos de busca.
- Formato: lista numerada de tópicos obrigatórios.
- Restrições: linguagem acessível, limite de ~400 palavras.
- Critérios: não definidos ainda.

### Prompt
```text
Atue como professor de Ciência da Computação.

Explique o algoritmo de busca binária para estudantes do primeiro ano
de graduação que já conhecem vetores e estruturas de repetição, mas
nunca estudaram algoritmos de busca.

Apresente:
1. uma definição simples;
2. como o algoritmo funciona, passo a passo;
3. um exemplo numérico com um vetor pequeno;
4. uma comparação com a busca linear em termos de eficiência.

Utilize linguagem acessível e limite a resposta a aproximadamente
400 palavras.
```

### Resultado
```text
BUSCA BINÁRIA

Definição
A busca binária é uma técnica para encontrar um valor dentro de um
vetor ORDENADO, "cortando" o espaço de busca pela metade a cada
tentativa, em vez de olhar elemento por elemento.

Como funciona
1. Definimos dois ponteiros: início (primeiro índice) e fim (último
   índice).
2. Calculamos o meio: meio = (início + fim) / 2.
3. Comparamos o valor do meio com o valor procurado.
4. Se forem iguais, encontramos o valor.
5. Se o valor procurado for menor, descartamos a metade direita e
   repetimos o processo na metade esquerda.
6. Se for maior, descartamos a metade esquerda e repetimos na direita.
7. O processo termina quando encontramos o valor ou quando início
   ultrapassa fim (valor não existe no vetor).

Exemplo
Vetor: [2, 5, 8, 12, 16, 23, 38, 45, 56, 72]
Procurando o valor 23:
- meio = elemento na posição 4 (16); 23 > 16, buscamos à direita.
- novo meio = elemento na posição 7 (45); 23 < 45, buscamos à esquerda.
- novo meio = elemento na posição 5 (23); encontramos o valor!
Foram necessárias apenas 3 comparações em um vetor de 10 elementos.

Comparação com busca linear
A busca linear verifica os elementos um a um, do início ao fim, e por
isso pode precisar de até n comparações. A busca binária, por dividir
o vetor pela metade a cada passo, precisa de no máximo log2(n)
comparações. Em um vetor de 1 milhão de elementos, a busca linear pode
levar até 1 milhão de comparações, enquanto a busca binária resolve em
cerca de 20.
```

### Comparação (Prompt 1 x Prompt 2)

| Critério | Prompt 1 | Prompt 2 |
|---|---:|---:|
| Clareza | 2 | 4 |
| Precisão | 3 | 4 |
| Relevância | 2 | 4 |
| Organização | 1 | 4 |
| Adequação ao público | 1 | 4 |
| Atendimento ao objetivo | 2 | 3 |
| Utilidade prática | 2 | 3 |

### Análise das melhorias
O Prompt 2 trouxe estrutura (definição, passo a passo, exemplo, comparação) e um exemplo numérico concreto, o que tornou a resposta muito mais didática. Porém, ainda faltava algo essencial: em nenhum momento a resposta afirma explicitamente que o vetor **precisa estar ordenado** para o algoritmo funcionar — só se pode inferir isso pela definição. Também não há alerta sobre erros comuns de implementação (por exemplo, cálculo incorreto do índice do meio, ou esquecer de atualizar início/fim, gerando loop infinito), nem uma forma de o estudante checar se realmente entendeu.

---

## Prompt 3

### O que ainda precisava melhorar?
- Tornar explícita a pré-condição (vetor ordenado) e o que acontece se ela for violada.
- Mostrar o rastreamento do exemplo com os índices início/fim/meio a cada iteração, não só o valor do meio.
- Alertar sobre um erro comum de implementação.
- Organizar visualmente com subtítulos e tabela (não apenas texto corrido).
- Definir um critério de qualidade objetivo (o estudante conseguir explicar com as próprias palavras) e terminar com perguntas de verificação — fechando o ciclo de estudo, não apenas de leitura.

### Hipótese
Acreditamos que a resposta ficará melhor porque, ao explicitar contexto (nível da turma e finalidade — revisão para prova), pré-condição, formato de saída (tabela) e critério de qualidade, a IA deixará de omitir informações importantes e produzirá um material verificável e autoavaliável, e não apenas "bonito".

### Prompt
```text
Atue como professor de Ciência da Computação especializado em
Algoritmos e Estruturas de Dados.

CONTEXTO:
Os estudantes estão no primeiro semestre, já conhecem vetores e laços
de repetição (for/while), mas nunca estudaram algoritmos de busca.
Eles terão uma avaliação sobre complexidade de algoritmos na próxima
semana.

OBJETIVO:
Fazer com que os estudantes compreendam intuitivamente por que a busca
binária é mais eficiente que a busca linear e sob quais condições ela
pode ser utilizada.

TAREFA:
Explique o algoritmo de busca binária apresentando:
1. definição em linguagem simples;
2. pré-condição obrigatória para usar o algoritmo (vetor ordenado) e o
   que acontece se essa condição não for respeitada;
3. funcionamento passo a passo;
4. um exemplo numérico completo, mostrando os índices início, fim e
   meio a cada iteração;
5. comparação de complexidade com a busca linear (O(n) x O(log n));
6. um erro comum cometido por iniciantes ao implementar o algoritmo.

FORMATO:
Organize a resposta utilizando subtítulos e uma tabela para a
comparação de complexidade.

RESTRIÇÕES:
- máximo de 500 palavras;
- evitar fórmulas matemáticas complexas, usar apenas o necessário;
- explicar qualquer termo técnico utilizado (ex.: logaritmo,
  complexidade assintótica).

CRITÉRIO DE QUALIDADE:
Ao final da explicação, um estudante iniciante deverá conseguir
explicar com suas próprias palavras por que a busca binária é mais
rápida que a busca linear.

Finalize apresentando duas perguntas para verificar a compreensão do
estudante.
```

### Resultado
```text
BUSCA BINÁRIA: ENCONTRANDO RÁPIDO EM VETORES ORDENADOS

1. Definição
Busca binária é um método para localizar um valor em um vetor,
eliminando metade das possibilidades a cada tentativa — como jogar
"maior ou menor" em vez de checar número por número.

2. Pré-condição: o vetor precisa estar ORDENADO
Esse é o ponto mais importante. Se o vetor não estiver ordenado, a
lógica de "descartar metade" deixa de fazer sentido, e o algoritmo pode
simplesmente não encontrar um valor que existe no vetor, sem avisar
que houve erro. Por isso, se os dados não estão ordenados, é preciso
ordená-los antes (ou usar busca linear).

3. Passo a passo
1. início = 0, fim = último índice.
2. Enquanto início <= fim: calcule meio = (início + fim) / 2.
3. Se vetor[meio] == valor procurado -> encontrado.
4. Se vetor[meio] > valor procurado -> fim = meio - 1 (descarta a
   direita).
5. Se vetor[meio] < valor procurado -> início = meio + 1 (descarta a
   esquerda).
6. Se início > fim, o valor não existe no vetor.

4. Exemplo com rastreamento completo
Vetor: [2, 5, 8, 12, 16, 23, 38, 45, 56, 72] (índices 0 a 9)
Procurando o valor 23:

| Iteração | início | fim | meio | vetor[meio] | Ação |
|---|---|---|---|---|---|
| 1 | 0 | 9 | 4 | 16 | 23 > 16, início = 5 |
| 2 | 5 | 9 | 7 | 45 | 23 < 45, fim = 6 |
| 3 | 5 | 6 | 5 | 23 | Encontrado! |

Apenas 3 comparações para um vetor de 10 elementos.

5. Comparação de complexidade
"Complexidade" mede quantas operações o algoritmo faz no pior caso,
conforme o vetor cresce. "Logaritmo na base 2" (log2 n) representa,
de forma simples, quantas vezes é possível dividir n pela metade até
sobrar 1 elemento.

| Algoritmo | Pior caso | Vetor com 1.000.000 de elementos |
|---|---|---|
| Busca linear | O(n) | até 1.000.000 comparações |
| Busca binária | O(log n) | cerca de 20 comparações |

6. Erro comum de iniciantes
Um erro frequente é não atualizar corretamente início ou fim (por
exemplo, esquecer o "+1" ou "-1"), o que pode fazer o algoritmo entrar
em loop infinito ou pular o elemento procurado. Sempre teste o
algoritmo com um valor que não existe no vetor para verificar se ele
termina corretamente.

Perguntas para verificar sua compreensão:
1. Por que a busca binária não funciona corretamente em um vetor
   desordenado?
2. Se um vetor tem 1.024 elementos, aproximadamente quantas
   comparações a busca binária faz no pior caso? Explique seu
   raciocínio.
```

### Comparação final

| Critério | Prompt 1 | Prompt 2 | Prompt 3 |
|---|---:|---:|---:|
| Clareza | 2 | 4 | 5 |
| Precisão | 3 | 4 | 5 |
| Relevância | 2 | 4 | 5 |
| Organização | 1 | 4 | 5 |
| Adequação ao público | 1 | 4 | 5 |
| Atendimento ao objetivo | 2 | 3 | 5 |
| Utilidade prática | 2 | 3 | 5 |
| **Total** | **13** | **26** | **35** |

---

## Validação

Antes de utilizar o conteúdo, conferimos:
- **Complexidade dos algoritmos** — O(n) para busca linear e O(log n) para busca binária são fatos consolidados na literatura de Estruturas de Dados e Algoritmos (ex.: Cormen et al., *Introduction to Algorithms*), então não é uma afirmação inventada pela IA.
- **O exemplo numérico** — refizemos manualmente o rastreamento (início/fim/meio) do vetor `[2,5,8,12,16,23,38,45,56,72]` buscando o valor 23, e conferimos que os índices e o resultado (encontrado na 3ª iteração) batem com o que a IA apresentou.
- **A pré-condição do vetor ordenado** — é um requisito conhecido do algoritmo e coerente com o passo a passo apresentado.
- **Não houve citação de fontes, dados estatísticos externos ou nomes de autores** que pudessem ser "alucinados" — por isso o risco de referência inventada, nesse caso específico, era baixo. Ainda assim, seguimos o hábito de checar toda afirmação técnica antes de usá-la para estudar.

---

## Reflexão

### 1. Qual foi a principal diferença entre os prompts?
O Prompt 1 pedia apenas uma "explicação" genérica, sem indicar público, formato ou objetivo, e por isso a IA teve que adivinhar o que era relevante. O Prompt 2 adicionou papel, público e uma lista de tópicos obrigatórios, o que já organizou bastante a resposta. O Prompt 3 foi o que realmente resolveu os problemas restantes, porque explicitou a pré-condição do algoritmo, pediu o rastreamento completo do exemplo, um erro comum e perguntas de verificação — elementos que nenhum dos prompts anteriores havia solicitado.

### 2. Quais elementos tiveram maior impacto no resultado?
Pedir explicitamente a **pré-condição do algoritmo** e o **rastreamento passo a passo com índices** foi o que mais mudou a qualidade técnica da resposta. Do ponto de vista pedagógico, pedir **perguntas de verificação ao final** foi o que transformou a resposta de "texto para ler" em "material para estudar".

### 3. Um prompt mais longo necessariamente produz uma resposta melhor? Justifique.
Não. O Prompt 3 é mais longo que o Prompt 1, mas o que o tornou melhor não foi o tamanho, e sim a especificidade: cada seção do prompt (contexto, pré-condição, formato, restrição, critério de qualidade) correspondia a uma lacuna real identificada na análise do resultado anterior. Um prompt longo cheio de adjetivos vagos ("explique de forma muito completa e detalhada") não teria o mesmo efeito, como o próprio material de apoio (cartilha) demonstra no exemplo sobre Python.

### 4. O que acontece quando o objetivo solicitado à IA não está claramente definido?
A IA precisa inferir o objetivo, e normalmente escolhe uma resposta genérica que tenta agradar a qualquer leitor possível — o que, na prática, deixa de atender bem a nenhum leitor específico. Foi exatamente o que aconteceu no Prompt 1: por não saber que era para estudantes iniciantes que nunca viram o assunto, a resposta usou termos técnicos (O(log n)) sem explicá-los.

### 5. Quais informações você considera indispensáveis para elaborar um bom prompt?
Papel (quem responde), público (para quem), objetivo (para quê), tarefa detalhada (o quê), formato de saída (como apresentar) e critério de qualidade (como saber se está bom). Em tarefas técnicas, também é essencial explicitar pré-condições e restrições do domínio — no nosso caso, o vetor precisar estar ordenado.

### 6. Como o refinamento de prompts pode ser útil para um profissional de Ciência da Computação?
Um profissional de TI frequentemente usa IA para gerar documentação, revisar código, estudar novas tecnologias ou propor arquiteturas. Saber refinar prompts evita retrabalho, reduz respostas genéricas ou tecnicamente incompletas e aumenta a chance de obter uma resposta realmente utilizável no primeiro ou segundo ciclo, economizando tempo.

### 7. Que riscos podem surgir quando confiamos em uma resposta da IA sem avaliar sua qualidade?
Podemos incorporar erros conceituais, exemplos incorretos ou pré-condições omitidas (como aconteceu no Prompt 1, que nem menciona que o vetor precisa estar ordenado) em um trabalho acadêmico ou em código de produção. Em contextos mais sérios, isso pode incluir dados inventados, fontes inexistentes ou informações desatualizadas.

### 8. Houve alguma situação em que o Prompt 3 ficou pior que o Prompt 2? Se sim, explique.
Não, nesse caso o Prompt 3 melhorou em todos os critérios avaliados. O único cuidado necessário foi verificar se o limite de 500 palavras e a restrição de "evitar fórmulas complexas" não fariam a IA omitir a tabela de complexidade — o que não aconteceu, pois a tabela foi mantida de forma simplificada.

### 9. Existe um ponto em que adicionar mais instruções começa a prejudicar a resposta?
Sim. Se pedíssemos, por exemplo, 15 itens obrigatórios dentro do mesmo limite de 500 palavras, a IA provavelmente teria que tratar cada item superficialmente, ou estouraria o limite de palavras. Instruções em excesso, ou contraditórias entre si (ex.: "seja bem detalhado" + "limite a 100 palavras"), tendem a piorar a coerência da resposta.

### 10. O que você faria para verificar se a resposta tecnicamente está correta?
Conferir a complexidade dos algoritmos em uma fonte confiável (livro-texto ou material da disciplina), refazer manualmente o exemplo numérico para confirmar os índices e o resultado, e testar a lógica descrita (ou implementá-la em código) para confirmar que ela realmente encontra o valor e trata corretamente o caso de valor inexistente.

---

## Take Away

> Um bom prompt não é simplesmente um prompt longo. Ele precisa **ser específico o suficiente para eliminar as principais ambiguidades que a IA teria de adivinhar** — quem vai responder, para quem, com qual objetivo, em qual formato e com quais critérios de qualidade — sem, no entanto, virar uma lista de instruções tão extensa que a resposta perca coerência.

### Cinco recomendações práticas

```text
1. Defina o papel e o público antes de pedir qualquer conteúdo — isso
   sozinho já elimina boa parte da generalidade da resposta.
2. Peça exemplos concretos e, quando fizer sentido, peça o
   "rastreamento" ou raciocínio passo a passo, não só a conclusão.
3. Explicite pré-condições, restrições e o formato de saída desejado
   (tabelas, subtítulos, limite de palavras).
4. Estabeleça um critério de qualidade objetivo (ex.: "o leitor deve
   conseguir explicar isso com as próprias palavras") em vez de pedir
   apenas "uma boa explicação".
5. Nunca aceite a primeira resposta como definitiva: analise o que
   falta, refine e, principalmente, verifique tecnicamente o conteúdo
   antes de usá-lo.
```

---

## Desafio final

Um colega diz: *"Meu prompt não funcionou. A IA respondeu errado."*

Cinco perguntas para diagnosticar o problema antes de mexer no prompt:

```text
1. O prompt deixava claro qual era exatamente a tarefa, ou poderia ser
   interpretado de mais de uma forma?
2. O prompt informava o contexto necessário (público, finalidade,
   nível de conhecimento prévio) para a IA responder de forma
   adequada?
3. A resposta está "errada" tecnicamente (fato incorreto,
   comprovável) ou apenas "não é o que eu esperava" (expectativa não
   comunicada no prompt)?
4. O erro foi verificado em uma fonte confiável, ou foi apenas
   presumido porque a resposta "parecia estranha"?
5. O prompt continha alguma instrução contraditória ou restrição
   incompatível com o que foi pedido (ex.: pedir muito detalhe com
   pouco espaço de resposta)?
```

### Pergunta final
O problema pode estar no prompt (ambíguo ou incompleto), na resposta da IA (erro real do modelo), nas informações utilizadas (dados desatualizados ou incorretos) ou na forma como o usuário avaliou o resultado (expectativa não alinhada com o que foi pedido). A Engenharia de Prompt envolve aprender a investigar todas essas possibilidades antes de simplesmente "tentar de novo".

---

## Referência

GRUPO IA STHEM/SEMESP; METARED TIC BRASIL. **IA no comando? Você no controle: guia prático para usar a inteligência artificial de forma inteligente, crítica e responsável na universidade.** Concepção, desenvolvimento e execução do projeto gráfico e design editorial: B42 EdTech; Karina N. Tomelin; Henrique Bergamasco. ISBN 978-85-60272-27-3.

Cartilha utilizada como material de apoio conceitual desta atividade (definição de refinamento de prompt, estrutura de comandos com papel/tarefa/cenário/formato de saída, e princípios de validação crítica de respostas de IA).
