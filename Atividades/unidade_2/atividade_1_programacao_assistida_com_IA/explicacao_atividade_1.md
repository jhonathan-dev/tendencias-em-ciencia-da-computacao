# Atividade Prática — Calculadora Simples (Nível Básico)

Disciplina: Programação Assistida por Inteligência Artificial
Projeto escolhido no menu: **Calculadora Simples** (Nível Básico)

## 1. Objetivo da atividade

A proposta do slide é usar a IA como apoio contínuo à programação, indo além
do código básico até chegar a uma refatoração inteligente. Na prática, isso
significa:

1. Construir uma versão funcional, porém ingênua, do projeto ("Antes").
2. Usar a IA para revisar, criticar e refatorar esse código ("Depois").
3. Documentar o que mudou e por quê — porque quem assina o commit é o
   humano, não a IA.

Este pacote entrega os dois códigos completos (HTML + CSS + JS em cada
arquivo) e esta explicação.

## 2. Arquivos entregues

| Arquivo | O que é |
|---|---|
| `calculadora_base.html` | Versão "Antes": funcional, mas com más práticas deliberadas. |
| `calculadora_refatorada.html` | Versão "Depois": mesma interface, código revisado e mais seguro. |
| `EXPLICACAO.md` | Este documento. |

Ambos os arquivos são independentes — basta abrir cada `.html` no navegador,
não precisam de servidor nem de instalação.

## 3. O ciclo de colaboração Humano-IA aplicado aqui

Seguindo o ciclo do slide (Contextualizar & Sugerir → Avaliar Criticamente →
Refatorar & Ajustar → Decidir & Integrar):

1. **Contextualizar & Sugerir**: pedi um primeiro rascunho de calculadora
   funcional em HTML/CSS/JS.
2. **Avaliar Criticamente**: revisei a lógica do rascunho e identifiquei
   pontos fracos típicos de código amador (ver seção 4).
3. **Refatorar & Ajustar**: reescrevi a lógica de cálculo e a estrutura do
   JavaScript, mantendo a mesma interface visual para isolar a comparação no
   código, não no design.
4. **Decidir & Integrar**: a versão refatorada foi validada manualmente
   (testes de soma, subtração, multiplicação, divisão e divisão por zero)
   antes de ser considerada final.

## 4. Comparação: o que mudou entre as duas versões

### 4.1 Uso de `eval()`

- **Base**: usa `eval(expressao)` para calcular o resultado. Isso funciona,
  mas é uma prática arriscada — `eval` executa qualquer código JavaScript
  que estiver na string, o que é uma porta aberta para bugs e, em um
  contexto real (input vindo de um usuário ou servidor), para
  vulnerabilidades de segurança.
- **Refatorada**: implementa um pequeno "parser" manual
  (`calcularExpressao`) que separa a expressão em tokens (números e
  operadores) e resolve a conta respeitando a precedência de operadores
  (`*`, `/`, `%` antes de `+`, `-`). Nada de código arbitrário é executado.

### 4.2 Tratamento de erros (divisão por zero)

- **Base**: dividir por zero gera `Infinity` ou `NaN` silenciosamente e o
  visor simplesmente exibe isso, sem explicação para quem está usando.
- **Refatorada**: a função `aplicarOperador` lança um erro específico
  (`"Divisão por zero"`), que é capturado num `try/catch` em `calcular()` e
  transformado numa mensagem amigável (`Erro: ÷0`) com destaque visual em
  vermelho no visor.

### 4.3 Organização do estado

- **Base**: usa uma variável global solta (`var expressao`), manipulada
  diretamente por várias funções — fácil de perder o controle conforme o
  projeto cresce.
- **Refatorada**: o estado vive dentro de um único objeto (`estado`), com
  um campo para a expressão atual e outro para sinalizar erro. Isso deixa
  claro, em um só lugar, tudo que descreve "o que a calculadora está
  mostrando agora".

### 4.4 Ligação entre HTML e JavaScript

- **Base**: cada botão tem um `onclick="..."` inline no HTML, chamando
  funções globais. Funciona, mas mistura estrutura (HTML) com
  comportamento (JS) e não escala bem.
- **Refatorada**: os botões usam atributos `data-value` / `data-action`, e
  um único `addEventListener` é registrado para todos eles via
  `document.querySelectorAll("button")`. É o padrão de **delegação de
  eventos**, mais próximo do que se vê em código profissional.

### 4.5 Legibilidade e nomes

- **Base**: nomes de função em português coloquial (`colocaNaTela`,
  `calcula`), tudo em poucas funções grandes.
- **Refatorada**: funções pequenas e com um propósito único
  (`digitar`, `apagarUltimo`, `limparTudo`, `calcularExpressao`,
  `aplicarOperador`, `atualizaVisor`), cada uma fácil de testar
  isoladamente (como fizemos ao validar a lógica de cálculo antes de
  integrá-la à interface).

## 5. Prompts usados como referência (cheat sheet aplicado)

Seguindo o "Roteiro de Prompts" do slide, os prompts usados para chegar na
versão refatorada seguiram o padrão estruturado, por exemplo:

> Atue como um dev front-end sênior. Refatore esta calculadora removendo o
> uso de `eval()`, tratando divisão por zero e separando o estado da
> interface em funções pequenas e nomeadas.

Em vez do prompt fraco equivalente ("melhore esse código"), que não dá à IA
nenhum critério concreto para decidir o que "melhorar" significa.

## 6. Os limites da automação (o que ficou por conta do humano)

Como o slide reforça: a IA sugeriu a estrutura do parser, o uso de
`data-attributes` e a forma do `try/catch`. Mas coube ao humano:

- Decidir que a interface visual deveria permanecer **idêntica** nas duas
  versões, para que a comparação fosse justa (só o código muda).
- Validar manualmente os cálculos (incluindo o caso de borda da divisão por
  zero) antes de aceitar a refatoração como correta.
- Garantir que nenhuma regra de negócio fosse perdida no processo — aqui,
  a regra é simples ("uma calculadora básica de quatro operações"), mas em
  projetos reais essa validação de contexto é o papel que a IA não cobre.

### 4.6 HTML semântico

A versão refatorada foi ajustada para usar marcação semântica em vez de
`<div>`s genéricos para tudo:

- `<header>` envolve o título e o subtítulo da calculadora.
- `<main aria-label="Calculadora simples">` é o landmark principal da página.
- O visor deixou de ser um `<input readonly>` e passou a ser um
  `<output id="visor" for="teclado">`, que é o elemento correto do HTML para
  "o resultado de um cálculo feito por outros controles" — exatamente o
  papel que ele cumpre aqui.
- O teclado de botões ganhou um `<div role="group" aria-label="Teclado da
  calculadora">` envolvendo as linhas, e cada botão simbólico (`÷`, `×`,
  `−`, `+`, `=`, `%`, `⌫`, `C`) recebeu um `aria-label` descritivo, para
  que leitores de tela anunciem "Dividir" em vez de apenas o símbolo `÷`.

Isso não muda o comportamento visual nem a lógica de cálculo — é uma
melhoria de acessibilidade e de significado da estrutura, sem tocar no
"Depois" que já tínhamos validado.

## 7. Como testar

1. Abra `calculadora_base.html` no navegador e teste, por exemplo, `5 / 0`
   — repare que o resultado não é tratado.
2. Abra `calculadora_refatorada.html` e repita o mesmo teste — o visor
   mostra `Erro: ÷0` e fica destacado em vermelho.
3. Compare o código-fonte de cada arquivo (é só abrir com um editor de
   texto) lado a lado com as seções 4 e 5 acima.
