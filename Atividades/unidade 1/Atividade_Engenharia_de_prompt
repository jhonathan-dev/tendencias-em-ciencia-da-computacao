# Aula 02 — Engenharia de Prompt
### Atividade Avaliativa A2 — Estudo de Caso em Marketing Digital

## 1. Identificação
- **Disciplina:** Tendências em Ciências da Computação
- **Unidade:** I — Fundamentos
- **Data:** 20/08/2026
- **Integrantes:** Melissa Aragão Leite (33999554) e Jhonathan de Moura Santos (32813589)
- **Valor da atividade:** 0,5 ponto
- **Ferramenta de IA generativa utilizada:** Claude (Anthropic), modelo Claude Sonnet 5

## 2. Problema escolhido

### Contexto
O **Café Aroma** é uma cafeteria de bairro com 1.200 seguidores no Instagram e uma
lista de transmissão no WhatsApp com cerca de 300 contatos. O negócio é administrado
pelo proprietário e conta com uma equipe de marketing composta por dois estagiários,
sem experiência prévia em tráfego pago ou ferramentas avançadas de marketing digital.
Nos últimos três meses, o movimento no período da tarde (14h às 17h em dias de semana)
caiu cerca de 30% em relação ao mesmo período do ano anterior, enquanto o movimento da
manhã e do fim de semana se manteve estável. O orçamento disponível para ações de
marketing é de **R$ 500,00 por mês**.

### Problema
A equipe de marketing precisa (1) gerar ideias de campanha viáveis para reverter a
queda de movimento no período da tarde e (2) preparar uma apresentação de 10 minutos
para convencer o proprietário a aprovar a campanha escolhida — sem contar com uma
agência de publicidade e com orçamento limitado.

### Objetivo
Utilizar IA generativa para (a) gerar e avaliar ideias de campanha de marketing digital
de baixo custo e (b) transformar a ideia mais recomendada em um roteiro de apresentação
persuasivo e realista para uma reunião de aprovação com o proprietário.

> **Por que esse caso combina os dois casos de uso da atividade?**
> A geração de ideias de projeto e a criação do roteiro de apresentação não são tarefas
> isoladas: a apresentação só é boa se comunicar bem a ideia escolhida. Por isso, o
> grupo tratou os dois como **um único fluxo de prompt**, em que a segunda tarefa
> depende diretamente do resultado da primeira.

## 3. Prompt inicial

```text
Crie ideias de marketing para um café e um roteiro de apresentação.
```

## 4. Resultado inicial

```text
Aqui estão algumas ideias de marketing para o seu café:

1. Faça promoções nas redes sociais.
2. Crie um programa de fidelidade.
3. Ofereça descontos em horários de menor movimento.
4. Faça parcerias com influenciadores.
5. Invista em anúncios pagos no Instagram.

Roteiro de apresentação:
1. Introdução sobre o café.
2. Apresentação do problema.
3. Apresentação das ideias de marketing.
4. Explicação dos benefícios.
5. Encerramento agradecendo a atenção.
```

## 5. Análise crítica

- **O que funcionou:** a IA entendeu que o pedido envolvia duas entregas (ideias de
  marketing e um roteiro) e produziu algo em cada uma.
- **O que não funcionou:** as ideias são genéricas e poderiam servir para qualquer
  negócio — não consideram o orçamento de R$ 500/mês, a equipe pequena e sem
  experiência, nem o problema específico (queda de movimento *à tarde*).
- **O que faltou:** custo estimado de cada ideia, prazo, métrica de sucesso, duração
  do roteiro, e conexão entre a ideia recomendada e o conteúdo da apresentação.
- **O que precisa ser validado:** nenhuma das ideias traz uma fonte ou estimativa
  realista de custo/resultado — tudo precisaria ser verificado manualmente antes de
  ser levado ao proprietário.

## 6. Prompt refinado

```text
PAPEL:
Você é um consultor de marketing digital especializado em pequenos negócios locais
com orçamento reduzido.

CONTEXTO:
O Café Aroma é uma cafeteria de bairro com 1.200 seguidores no Instagram e uma lista
de transmissão de WhatsApp com 300 contatos. A equipe de marketing é formada por dois
estagiários sem experiência em tráfego pago. Nos últimos três meses, o movimento das
14h às 17h (dias de semana) caiu 30% em relação ao ano anterior. O orçamento
disponível é de R$ 500,00 por mês.

OBJETIVO:
Aumentar em 20% o movimento no período da tarde em até 60 dias, e apresentar a
proposta ao proprietário em uma reunião de 10 minutos.

TAREFA:
1. Gere 3 ideias de campanha de marketing viáveis dentro do orçamento de R$ 500/mês.
2. Escolha e justifique a ideia mais recomendada.
3. Com base nela, crie um roteiro de apresentação de 10 minutos para o proprietário.

RESTRIÇÕES:
- Orçamento máximo de R$ 500,00/mês.
- Usar apenas canais já disponíveis: Instagram e WhatsApp.
- Linguagem acessível, sem jargões avançados de marketing.
- O roteiro deve caber em 10 minutos de fala (aprox. 1.300–1.500 palavras).

FORMATO:
- Ideias em tabela: Nome da campanha | Descrição | Custo estimado | Métrica de sucesso.
- Roteiro em tópicos, com tempo estimado por seção.

CRITÉRIOS DE QUALIDADE:
- As ideias devem ser exequíveis por uma equipe de dois estagiários sem experiência
  avançada.
- O roteiro deve conter abertura, diagnóstico do problema, proposta de solução,
  investimento e retorno esperado, e pedido claro de aprovação.
- O tom deve ser persuasivo, porém honesto quanto às incertezas dos resultados.
```

## 7. Resultado refinado

**Três ideias de campanha**

| Campanha | Descrição | Custo/mês | Métrica de sucesso |
|---|---|---|---|
| Happy Hour da Tarde | Desconto de 20% em combos das 14h às 17h, divulgado por Stories interativos (enquetes de sabor) e disparo semanal no WhatsApp. | R$ 150 | Nº de resgates do cupom via QR code |
| Cartão Fidelidade Digital | Sistema simples de pontos por compra na tarde, controlado em planilha, com prêmio após 8 visitas. | R$ 100 | Nº de cartões ativos após 30 dias |
| Parceria com Microinfluenciadores do Bairro | Troca de produto por post de 2 a 3 criadores locais com até 5 mil seguidores, divulgando o horário da tarde. | R$ 450 | Alcance e menções geradas |

**Ideia recomendada:** *Happy Hour da Tarde*, por ter o menor custo, ser fácil de
operar pela equipe atual e atacar diretamente o horário problemático, com resultado
mensurável em poucas semanas.

**Roteiro de apresentação (10 minutos)**

1. **Abertura (1 min):** contextualizar a reunião e o objetivo: reverter a queda de
   movimento da tarde.
2. **Diagnóstico do problema (2 min):** apresentar o dado da queda de 30% e possíveis
   causas observadas (concorrência, clima, rotina do bairro).
3. **Proposta de solução (3 min):** apresentar a campanha *Happy Hour da Tarde*,
   explicando mecânica do desconto, uso de Stories e WhatsApp.
4. **Investimento e cronograma (2 min):** detalhar o custo de R$ 150/mês e o prazo de
   60 dias para avaliação de resultados.
5. **Resultado esperado (1 min):** projeção de aumento de 20% no movimento da tarde,
   com ressalva de que é uma estimativa a ser validada nas primeiras semanas.
6. **Pedido de aprovação e próximos passos (1 min):** solicitar aprovação do
   orçamento e definir data de início.

## 8. Técnicas utilizadas

- [x] Role Prompting
- [x] Contexto
- [x] Restrições
- [x] Formato de saída
- [x] Prompt em etapas (ideias → escolha → roteiro)
- [x] Refinamento iterativo
- [ ] Few-Shot Prompting
- [ ] Outra

## 9. Comparação

| Critério | Prompt A (inicial) | Prompt B (refinado) |
|---|---|---|
| Clareza | Baixa | Alta |
| Contexto | Ausente | Completo |
| Relevância | Genérica | Específica para o caso |
| Organização | Fraca | Estruturada (tabela + tópicos) |
| Precisão | Baixa | Alta (custos e métricas definidos) |
| Utilidade | Limitada | Pronto para uso na reunião |

**Qual prompt produziu o resultado mais adequado? Por quê?**
O Prompt B, pois incorporou o orçamento real, o público, a equipe disponível e o
formato exigido pela reunião — reduzindo a necessidade de retrabalho manual pela
equipe de marketing.

## 10. Teste de robustez

Para observar o impacto de uma variável, o grupo alterou o orçamento de **R$ 500,00**
para **R$ 150,00** por mês, mantendo o restante do prompt refinado.

- **O que mudou na resposta:** a IA descartou a ideia de parceria com
  microinfluenciadores (que custava R$ 450) e concentrou as três ideias em ações sem
  custo direto, como conteúdo orgânico e ativação da lista de WhatsApp.
- **Por que acreditamos que mudou:** a restrição de orçamento estava explícita no
  prompt, então o modelo ajustou as sugestões para caber no novo limite.
- **A alteração melhorou ou piorou o resultado?** Para um orçamento menor, melhorou —
  mostrou que o prompt responde de forma consistente a mudanças de restrição, o que
  reforça a importância de declarar essas restrições com clareza.

## 11. Validação

O grupo validou o resultado da seguinte forma:

- Conferiu manualmente se os custos estimados (cupons, planilha de fidelidade,
  brindes para influenciadores) eram compatíveis com valores praticados no mercado local.
- Verificou que o uso do WhatsApp para disparos respeita a exigência de opt-in
  (contatos que já autorizaram receber mensagens), conforme a LGPD.
- Confirmou junto ao "proprietário" (papel simulado pelo grupo) se o horário de 14h
  às 17h e os dados de queda de movimento faziam sentido com a realidade do negócio.
- Considerou a projeção de aumento de 20% como uma **hipótese a testar**, não como
  garantia, e assim o roteiro apresenta essa ressalva.

## 12. Ética e responsabilidade

- **Viés de contexto:** as ideias geradas podem refletir estratégias comuns em
  grandes centros urbanos e não considerar particularidades culturais do bairro
  específico do Café Aroma — por isso a validação humana com o proprietário é essencial.
- **Estimativas não verificadas:** os custos e a projeção de 20% de aumento são
  estimativas do modelo, não dados de mercado auditados; apresentá-los como certeza
  ao proprietário seria antiético.
- **Privacidade dos clientes:** a lista de WhatsApp só pode ser usada para campanhas
  com contatos que optaram por recebê-las, respeitando a LGPD.
- **Responsabilidade humana:** cabe à equipe de marketing revisar, validar e assumir
  a responsabilidade pelas decisões tomadas com apoio da IA — a ferramenta apoia o
  raciocínio, mas não substitui o julgamento humano.

## 13. Take Away

**O que mudou na nossa compreensão sobre IA depois de aprender a estruturar um prompt?**
Percebemos que um prompt vago gera respostas genéricas e difíceis de usar na prática,
enquanto um prompt estruturado — com papel, contexto, restrições e formato — produz
um resultado quase pronto para uso real, reduzindo o retrabalho da equipe.

**Qual é a principal responsabilidade de uma pessoa que utiliza IA generativa para
produzir conhecimento ou tomar decisões?**
Verificar a veracidade e a viabilidade prática do que foi gerado antes de aplicá-lo,
reconhecendo que a IA pode errar, ter vieses ou apresentar estimativas otimistas
demais — a decisão final e a responsabilidade continuam sendo humanas.

## 14. Declaração de uso de Inteligência Artificial

Em conformidade com as boas práticas de transparência acadêmica, o grupo declara que
utilizou a ferramenta de IA generativa **Claude (Anthropic), modelo Claude Sonnet 5**,
como apoio na geração e no refinamento iterativo dos prompts e das respostas
apresentadas nas seções 3 a 7 deste documento. Todo o conteúdo gerado pela IA foi
lido, analisado criticamente e validado pelos integrantes do grupo antes de compor
este relatório, conforme descrito nas seções 11 (Validação) e 12 (Ética e
Responsabilidade).

## 15. Referências

ANTHROPIC. *Claude* (Sonnet 5). São Francisco: Anthropic, 2026. Disponível em:
https://claude.ai. Acesso em: 20 ago. 2026.

ASSOCIAÇÃO BRASILEIRA DE NORMAS TÉCNICAS. **NBR 6023**: informação e documentação —
referências — elaboração. Rio de Janeiro: ABNT, 2018.

ASSOCIAÇÃO BRASILEIRA DE NORMAS TÉCNICAS. **NBR 14724**: informação e documentação —
trabalhos acadêmicos — apresentação. Rio de Janeiro: ABNT, 2011.

BRASIL. **Lei nº 13.709, de 14 de agosto de 2018**. Lei Geral de Proteção de Dados
Pessoais (LGPD). Brasília, DF: Presidência da República, 2018. Disponível em:
https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm. Acesso em:
20 ago. 2026.
