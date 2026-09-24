# Vibe Coding: programar conversando com a IA

> Atividade da **Aula 06 — Programação Assistida por Inteligência Artificial**
> Centro Universitário UDF · Tendências em Ciência da Computação · Unidade II

**Aluno:** Jhonathan de Moura Santos
**RGM:** 32813589

**Texto-base:** SARKAR, Advait; DROSOS, Ian. *Vibe coding: programming through conversation with artificial intelligence*. In: Proceedings of the 36th Annual Conference of the Psychology of Programming Interest Group (PPIG 2025), 2025. [arXiv:2506.23253](https://arxiv.org/abs/2506.23253)

---

## 📂 Arquivos do repositório

| Arquivo | Descrição |
|---|---|
| [`Apresentacao_Vibe_Coding.pdf`](Apresentacao_Vibe_Coding.pdf) | Apresentação (17 slides) com as questões norteadoras, o estudo de caso e a síntese |
| [`Apresentacao_Vibe_Coding.pptx`](Apresentacao_Vibe_Coding.pptx) | Mesma apresentação em PowerPoint, com notas do apresentador |
| [`Resumo_Vibe_Coding_Jhonathan.docx`](Resumo_Vibe_Coding_Jhonathan.docx) | Resumo geral do texto em Word |
| `README.md` | Este arquivo |

---

## 🎯 Objetivo da atividade

Avaliar os limites, os riscos e o potencial da colaboração entre pessoas desenvolvedoras e sistemas de IA durante a programação. A estratégia foi leitura orientada, debate e estudo de caso.

---

## 📝 Resumo geral do texto

### 1. Tema e contexto
O artigo é o primeiro estudo empírico sobre o *vibe coding*. Nesse modo de programar, o desenvolvedor produz código principalmente conversando com modelos de linguagem, sem escrevê-lo diretamente. O termo surgiu em fevereiro de 2025, em um post de Andrej Karpathy. Nele, Karpathy descreve um estilo em que se "esquece que o código existe": aceita-se tudo o que a IA sugere, sem ler as alterações, e as mensagens de erro são apenas coladas de volta para a IA.

### 2. Método
Os autores partiram de 35 vídeos do YouTube e da Twitch. Desses, analisaram em detalhe 5 (cerca de 8,5 horas), em que programadores constroem projetos reais pensando em voz alta. A análise foi organizada em nove categorias: objetivos, intenções, fluxo de trabalho, prompts, depuração, desafios, expertise, confiança e definição do vibe coding.

### 3. Principais resultados
O vibe coding funciona como um **ciclo iterativo**. O programador define um objetivo, pede o código à IA, revisa, aceita ou rejeita, testa e depois refina o pedido ou edita à mão. Os prompts misturam pedidos vagos e estéticos com instruções técnicas bem detalhadas. Os autores também identificam o **momentum de contexto**: as primeiras escolhas da IA, aceitas por conveniência, prendem o projeto a um caminho difícil de mudar depois. A depuração continua **híbrida**. Às vezes a IA recebe a mensagem de erro e corrige. Em outras, o programador usa o console, o terminal e suas próprias hipóteses, sobretudo quando a IA inventa APIs ou usa versões erradas de bibliotecas.

### 4. Conclusão central
O vibe coding **não elimina a necessidade de saber programar: redistribui essa expertise**. O desenvolvedor passa a atuar como diretor, revisor e editor do código. Precisa de conhecimento técnico tradicional, de letramento em IA e de visão de produto, além de saber quando trocar a IA pelo trabalho manual. A confiança na IA é granular, dinâmica e construída por verificação, nunca por aceitação cega.

### 5. Discussão
Os autores descrevem o vibe coding como uma forma inicial de **"desengajamento material"**: o programador deixa de manipular diretamente o código e passa a orquestrá-lo por meio da IA. Isso reduz o trabalho tedioso, mas pode diminuir o aprendizado profundo que vem de lidar diretamente com o código. Os autores também observam que os criadores dos vídeos exibem sua competência técnica para se defender do preconceito contra quem usa IA no trabalho.

### 6. Limitações
O estudo é pequeno. Os vídeos foram gravados para um público, o que pode exagerar o sucesso da IA. E nenhum participante era iniciante, então ainda não se sabe como pessoas sem conhecimento de programação praticam o vibe coding.

---

## 🖥️ Estrutura da apresentação

Cada slide indica no rodapé a seção e a página do artigo usadas como base.

| # | Slide | Base no texto |
|---|---|---|
| 1 | Capa | — |
| 2 | O que é vibe coding | Resumo e Seção 1 (p. 1–3) |
| 3 | Como os autores estudaram o vibe coding | Seção 2 (p. 3–6) |
| 4 | O ciclo de "satisfação de objetivos" | Seção 3.3 (p. 8–9) |
| 5 | Prompts: pedidos vagos e instruções técnicas | Seção 3.4 (p. 9–12) |
| 6 | Momentum de contexto | Seção 3.2.2 (p. 7–8) |
| 7 | Depuração híbrida | Seção 3.5.1 (p. 12–14) |
| 8 | **Questão 1:** Até que ponto confiar no código da IA? | Seção 3.8 (p. 17–18) |
| 9 | **Questão 2:** A IA reduz ou transforma o conhecimento? | Seções 3.7.1 e 3.7.2 (p. 15–16) |
| 10 | **Questão 3:** Quando usar a IA e quando assumir o controle? | Seções 3.7.3, 3.6.1 e 4.1 |
| 11–12 | Estudo de caso e responsabilidades humanas | Seções 3.2.2, 3.5, 3.8 e 3.9.2 |
| 13 | Desengajamento material: ganhos e perdas | Seções 4.3 e 4.5 (p. 21–25) |
| 14 | Trechos que chamaram atenção | Resumo, 3.6.1 e 3.8 |
| 15 | Três boas práticas | Seções 3.4, 3.5, 3.7 e 3.8 |
| 16 | Síntese | Resumo, 3.7, 3.8 e Conclusão |
| 17 | Referências | — |

---

## ✅ Três boas práticas para a colaboração humano-IA

1. **Não aceitar sem entender e testar:** ler os diffs, testar além do "caminho feliz" e comparar com a documentação antes de aceitar. *(Seções 3.5 e 3.8)*
2. **Pedir em partes, com contexto:** uma fase por vez, restrições explícitas, exemplos e documentação; limpar o contexto ao mudar de tarefa. *(Seção 3.4.2)*
3. **Manter as decisões com pessoas:** saber quando assumir o controle manualmente e garantir que alguém da equipe responda por cada código. *(Seções 3.7.3 e 3.8)*

> **Boa prática essencial:** nenhum código gerado por IA entra no projeto sem ser entendido, testado e revisado por uma pessoa.

---

## 💡 Síntese

> *"Programar com IA de maneira responsável não significa apenas saber pedir código; significa também..."*

...saber avaliar, testar e assumir a responsabilidade pelo que a IA entrega. Como mostram Sarkar e Drosos, o vibe coding não elimina a expertise, mas a redistribui: o programador passa a dirigir, revisar e editar, gerenciando o contexto dos prompts e decidindo quando confiar e quando assumir o controle manualmente. A confiança deve ser construída por verificação contínua, e não por aceitação cega, porque a IA pode inventar APIs, propagar escolhas ruins e ignorar dependências que só a equipe conhece. Por isso, entender o código, proteger o sistema e responder pelo resultado continuam sendo responsabilidades humanas.

---

## 📚 Referências

- SARKAR, Advait; DROSOS, Ian. *Vibe coding: programming through conversation with artificial intelligence*. PPIG 2025. arXiv:2506.23253.
- CENTRO UNIVERSITÁRIO UDF. *Aula 06 — Programação Assistida por Inteligência Artificial: orientações*. Tendências em Ciência da Computação, 2026.

> As citações do artigo usadas na apresentação são traduções livres do original em inglês.
