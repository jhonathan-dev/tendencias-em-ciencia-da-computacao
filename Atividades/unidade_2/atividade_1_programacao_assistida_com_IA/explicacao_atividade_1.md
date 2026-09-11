# Atividade Prática: Calculadora Simples (Nível Básico)

Disciplina: Programação Assistida por Inteligência Artificial
Projeto escolhido no menu: **Calculadora Simples** (Nível Básico)

## 1. Objetivo da atividade

A proposta do slide é usar a IA como apoio contínuo à programação, indo além
do código básico até chegar a uma refatoração inteligente. Na prática, isso
significa:

1. Construir uma versão funcional, porém ingênua, do projeto ("Antes").
2. Usar a IA para revisar, criticar e refatorar esse código ("Depois").
3. Documentar o que mudou e por quê, porque quem assina o commit é o
   humano, não a IA.

Este pacote entrega os dois códigos completos (HTML + CSS + JS em cada
arquivo) e esta explicação.

## 2. Arquivos entregues

| Arquivo | O que é |
|---|---|
| `calculadora_base.html` | Versão "Antes": funcional, mas com más práticas deliberadas. |
| `calculadora_refatorada.html` | Versão "Depois": mesma interface, código revisado e mais seguro. |
| `EXPLICACAO.md` | Este documento. |

Ambos os arquivos são independentes. Basta abrir cada `.html` no navegador;
não precisam de servidor nem de instalação.

## 3. O ciclo de colaboração Humano-IA aplicado aqui

Seguindo o ciclo do slide (Contextualizar & Sugerir, Avaliar Criticamente,
Refatorar & Ajustar, Decidir & Integrar):

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
  mas é uma prática arriscada: `eval` executa qualquer código JavaScript
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
  diretamente por várias funções, o que torna fácil perder o controle
  conforme o projeto cresce.
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

### 4.6 HTML semântico

A versão refatorada foi ajustada para usar marcação semântica em vez de
`<div>`s genéricos para tudo:

- `<header>` envolve o título e o subtítulo da calculadora.
- `<main aria-label="Calculadora simples">` é o landmark principal da página.
- O visor deixou de ser um `<input readonly>` e passou a ser um
  `<output id="visor" for="teclado">`, que é o elemento correto do HTML para
  "o resultado de um cálculo feito por outros controles", exatamente o
  papel que ele cumpre aqui.
- O teclado de botões ganhou um `<div role="group" aria-label="Teclado da
  calculadora">` envolvendo as linhas, e cada botão simbólico (`÷`, `×`,
  `−`, `+`, `=`, `%`, `⌫`, `C`) recebeu um `aria-label` descritivo, para
  que leitores de tela anunciem "Dividir" em vez de apenas o símbolo `÷`.

Isso não muda o comportamento visual nem a lógica de cálculo. É apenas uma
melhoria de acessibilidade e de significado da estrutura, sem tocar no
"Depois" que já tínhamos validado.

### 4.7 Digitação pelo teclado físico (incluindo NumPad)

A versão refatorada também passou a escutar `keydown` no `document`,
mapeando:

- `0`–`9`, `.`, `+`, `-`, `*`, `/`, `%` → `digitar(...)`
- `Enter` ou `=` → `calcular()`
- `Backspace` → `apagarUltimo()`
- `Escape` ou `Delete` → `limparTudo()`

O navegador já normaliza as teclas do teclado numérico (NumPad) para os
mesmos valores de `e.key` das teclas normais (`"7"`, `"+"`, `"."` etc.).
Por isso não foi preciso nenhum tratamento especial para o NumPad; ele
funciona automaticamente assim que o teclado normal funciona. O ponto
importante aqui é que **nenhuma lógica foi duplicada**: as teclas chamam
exatamente as mesmas funções (`digitar`, `apagarUltimo`, `limparTudo`,
`calcular`) que os botões de clique já usavam.

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
- Garantir que nenhuma regra de negócio fosse perdida no processo. Aqui a
  regra é simples ("uma calculadora básica de quatro operações"), mas em
  projetos reais essa validação de contexto é o papel que a IA não cobre.

## 7. Como testar

1. Abra `calculadora_base.html` no navegador e teste, por exemplo, `5 / 0`.
   Repare que o resultado não é tratado.
2. Abra `calculadora_refatorada.html` e repita o mesmo teste. O visor
   mostra `Erro: ÷0` e fica destacado em vermelho.
3. Compare o código-fonte de cada arquivo (é só abrir com um editor de
   texto) lado a lado com as seções 4 e 5 acima.

## 8. Etapa 2: o prompt estruturado usado

Seguindo o template pedido na atividade, este foi o prompt construído para
gerar a refatoração da calculadora:

```
PAPEL: Desenvolvedor front-end sênior, especialista em JavaScript
vanilla, acessibilidade web e boas práticas de segurança.

CONTEXTO: Existe uma calculadora simples de quatro operações em
HTML/CSS/JS, feita de forma propositalmente ingênua (versão "Antes"),
para servir de base de comparação numa atividade sobre refatoração
assistida por IA.

PROBLEMA: A versão atual usa eval() para calcular expressões, guarda o
estado em uma variável global, liga os botões via onclick inline, não
trata divisão por zero, usa <input readonly> no lugar de um elemento
semântico para o visor e só aceita clique de mouse (sem suporte a
teclado físico ou NumPad).

ENTRADA: O arquivo HTML da versão "Antes" (calculadora_base.html), com
a interface e a lógica completas.

SAÍDA ESPERADA: Um único arquivo HTML autocontido (HTML + CSS + JS),
com a mesma interface visual da versão original, porém com o código
refatorado: sem eval(), com tratamento de divisão por zero, estado
organizado, marcação semântica e suporte a teclado (incluindo NumPad).

LINGUAGEM: HTML5, CSS3 e JavaScript (ES6+), sem frameworks ou
bibliotecas externas.

RESTRIÇÕES:
- Não usar eval() nem qualquer execução de código arbitrário.
- Não alterar a aparência visual da calculadora.
- Não usar bibliotecas externas nem chamadas de rede.
- Manter tudo em um único arquivo .html.

CRITÉRIOS DE QUALIDADE:
- Nenhuma variável global solta; estado isolado em um objeto.
- Funções pequenas, nomeadas e com responsabilidade única.
- Uso de marcação semântica (header, main, output, aria-label) em vez
  de apenas <div>.
- Delegação de eventos em vez de onclick inline.
- Tratamento explícito de erros, com mensagem visível ao usuário.

CASOS DE TESTE:
- 2 + 3 * 4 deve resultar em 14 (respeitando precedência).
- 10 - 2 - 3 deve resultar em 5.
- 5 / 0 deve mostrar uma mensagem de erro, não Infinity.
- Digitar pelos números do teclado físico e do NumPad deve funcionar
  igual a clicar nos botões.
- Enter deve calcular; Backspace deve apagar o último dígito; Escape
  deve limpar tudo.
```

## 9. Etapa 3: checklist de verificação do código gerado

Antes de aceitar o código gerado pela IA como versão final, respondi ao
checklist da atividade com base no que foi efetivamente entregue:

- [x] **Eu compreendo o código?** Sim. Cada função tem uma única
  responsabilidade (`digitar`, `apagarUltimo`, `limparTudo`,
  `calcularExpressao`, `aplicarOperador`, `atualizaVisor`), o que tornou
  fácil ler e explicar cada trecho (ver seção 4).
- [x] **O código atende ao problema definido?** Sim. A calculadora
  continua fazendo as quatro operações básicas, com a mesma interface,
  mas agora sem os problemas listados no PROBLEMA do prompt.
- [x] **Há bibliotecas que eu não conheço?** Não. O código usa apenas
  APIs nativas do navegador (DOM, `addEventListener`, expressões
  regulares), sem nenhuma dependência externa.
- [x] **Há operações que podem apagar ou sobrescrever dados?** Não se
  aplica diretamente: a calculadora não lê nem grava nada fora da
  própria página (não usa `localStorage`, cookies ou requisições de
  rede), então não há risco de apagar dados do usuário.
- [ ] **O código utiliza dados sensíveis?** Não. Não há coleta, envio
  ou armazenamento de nenhuma informação do usuário.
- [x] **Há tratamento de erros?** Sim, e esse foi um dos pontos centrais
  da refatoração: divisão por zero e expressões inválidas são
  capturadas em `try/catch` e mostradas como mensagem de erro no visor,
  em vez de gerar `Infinity`/`NaN` silenciosamente.
- [x] **Consigo explicar cada função ou bloco principal?** Sim, estão
  documentadas na seção 4 deste documento, função por função.
- [x] **Existem casos que o código não considera?** Sim, alguns
  conscientemente fora de escopo para uma calculadora "nível básico":
  não há suporte a parênteses, não há histórico de operações anteriores
  e o resultado é arredondado em 10 casas decimais (`toFixed(10)`), o
  que pode gerar pequenas imprecisões em contas com muitas casas
  decimais. Nada disso compromete o objetivo da atividade, mas fica
  registrado aqui como limitação conhecida.
