# Prompt utilizado no Lovable

Este prompt foi gerado pelo **Claude** a partir da leitura do protótipo no **Figma** (via conector Figma) e colado no **Lovable** para gerar a primeira versão da aplicação. Depois, ajustes finos foram feitos com prompts curtos.

---

```
Crie uma aplicação web chamada "MVC Finance", um app de controle financeiro pessoal, em português do Brasil. É um protótipo acadêmico: NÃO use backend, banco de dados, autenticação real nem APIs externas. Todos os dados devem ser fictícios, mantidos em estado React e salvos no localStorage para persistir ao recarregar a página.

## Identidade visual
- Fundo geral: azul muito claro (#EEF3FC). Cards brancos com borda cinza-clara (#E2E8F0), cantos arredondados de 16px e sombra suave.
- Cor primária: azul-marinho escuro (#001858) para o card de saldo e títulos de destaque.
- Botão de ação principal: azul royal (#3B4FE0), texto branco, cantos totalmente arredondados (pill).
- Verde para entradas/ganhos (#2DB400), vermelho para saídas/gastos (#E5332A), preto/cinza-escuro para investimentos (#222).
- Fonte: Nunito (Google Fonts). Ícones: lucide-react.
- Layout desktop com largura máxima de 1440px, responsivo para celular (colunas viram uma só).

## Cabeçalho (todas as páginas logadas)
- Logo "MVC FINANCE" à esquerda (ícone de carteira com cifrão + texto azul-marinho).
- Menu: Dashboard, Transações, Assinatura, Plataforma de Ensino. O item ativo fica em azul.
- À direita: avatar circular + nome do usuário fictício ("Alícia Koch").
- "Plataforma de Ensino" pode abrir uma página simples "Em breve".

## 1. Página de Login (/login)
- Tela dividida: à esquerda um card branco com o logo, título "Bem-vindo", um parágrafo curto explicando que o MVC Finance ajuda a organizar receitas, despesas e investimentos, e o botão "Fazer login". À direita uma área decorativa em azul-marinho com uma prévia do dashboard.
- Ao clicar em "Fazer login", entrar com um usuário fictício (sem senha) e ir para o Dashboard. Incluir opção de "Sair" no menu do avatar.

## 2. Dashboard (/)
Título "Dashboard". No canto superior direito: botão de texto "Relatório IA" (ícone file-text) e um seletor de mês em formato pill ("Novembro" com chevron-down) que filtra os dados pelo mês escolhido.

Coluna esquerda (≈ 2/3 da largura):
- Card grande azul-marinho "Saldo" com o valor em destaque (ex.: R$ 2.700), ícone de olho que esconde/mostra o valor (troca por "R$ ••••"), e botão "Adicionar Transação" (ícone arrow-down-up) à direita.
- Linha com 3 cards: "Investido" (ícone porquinho, fundo cinza), "Receita" (ícone trending-up verde), "Despesas" (ícone trending-down vermelho), cada um com o valor total do mês.
- Abaixo, dois cards lado a lado:
  - Gráfico de rosca (Recharts) com a proporção Ganhos (verde), Gastos (vermelho) e Investimentos (preto), e a legenda com ícones e percentuais.
  - "Gastos por categoria": lista com Moradia, Alimentação, Saúde e Transporte, cada uma com nome, percentual à direita, barra de progresso cinza e o valor em R$ abaixo.

Coluna direita (≈ 1/3):
- Card "Transações" com botão "Ver mais" (leva para /transacoes) e lista das últimas transações: ícone colorido à esquerda, título, data ("15 Nov, 2024") e valor à direita (verde com "+" para depósito, vermelho com "-" para gasto, cinza-escuro para investimento).

Todos os totais, percentuais e o gráfico devem ser CALCULADOS a partir da lista de transações, para atualizar automaticamente ao adicionar, editar ou excluir.

## 3. Modal "Adicionar Transação"
Abre centralizado com fundo escurecido. Título "Adicionar Transação" e subtítulo "Insira as informações abaixo". Campos:
- Título (texto)
- Valor (máscara de moeda "R$ 0.000,00")
- Tipo da transação (select: Depósito, Gasto, Investimento)
- Categoria (select que aparece só quando o tipo for "Gasto": Moradia, Alimentação, Saúde, Transporte, Outros)
- Método de pagamento (select: Pix, Cartão de crédito, Cartão de débito, Boleto, Dinheiro)
- Data (date picker com ícone de calendário, placeholder "Selecionar Dia")
Botões: "Cancelar" (contorno) e "Adicionar" (azul). Validar: todos os campos obrigatórios e valor maior que zero, mostrando mensagem de erro em vermelho abaixo do campo. Ao salvar, fechar o modal e mostrar um toast de sucesso.

## 4. Página Transações (/transacoes)
- Título "Transações" e botão "Adicionar Transação" no topo à direita.
- Tabela com colunas: Título, Tipo (badge com bolinha colorida: Depósito verde, Gasto vermelho, Investimento cinza), Categoria, Método, Data, Valor e Ações (ícones de lápis e lixeira).
- Editar: ao clicar no lápis, abrir um painel lateral (sheet) à direita em azul-marinho, título "Transação", com os mesmos campos do formulário já preenchidos e botões "Cancelar" e "Salvar" (verde). Ao salvar, mostrar toast "Transação editada com sucesso".
- Excluir: ao clicar na lixeira, abrir um diálogo de confirmação "Deseja excluir esta transação?" com botões "Cancelar" e "Excluir" (vermelho). Após confirmar, mostrar toast "Transação excluída".

## 5. Modal "Relatório IA"
Ao clicar em "Relatório IA" no dashboard, abrir um modal com ícone file-text, título "Relatório IA", botão de fechar (X) e um texto de análise do mês. O texto deve ser gerado LOCALMENTE a partir dos dados (sem API), por exemplo: total de receitas e despesas, maior categoria de gasto e percentual, saldo final e uma dica simples de economia. Botão "Fechar" no rodapé.

## 6. Página Assinatura (/assinatura)
Título "Assinatura" e dois cards de plano lado a lado:
- "Plano Básico" — R$ 0/mês, com badge "Atual", lista de benefícios com check e botão "Plano atual" desativado.
- "Plano Pro" — R$ 19/mês, lista de benefícios (relatórios de IA ilimitados, categorias personalizadas, exportação de dados) e botão azul "Assinar agora". Ao clicar, mostrar toast "Plano Pro ativado (demonstração)" e trocar o badge de plano atual.

## Dados iniciais fictícios
Pré-carregar cerca de 12 transações de novembro de 2024, por exemplo: Salário +R$ 3.900 (depósito, Pix), Freelancing +R$ 1.750 e +R$ 2.500 (depósito), Bitcoin -R$ 2.500 (investimento), Aluguel -R$ 297,90 (gasto, Moradia), Academia -R$ 120,90 (gasto, Saúde), além de gastos com Alimentação e Transporte. Incluir também algumas transações de outubro para o filtro de mês funcionar.

## Requisitos técnicos
React + TypeScript + Tailwind + shadcn/ui (Dialog, Sheet, Select, Popover/Calendar, Toast, Table, Badge), Recharts para o gráfico e react-router para as rotas. Formatar valores em BRL com Intl.NumberFormat("pt-BR") e datas no formato "15 Nov, 2024". Organizar o código em componentes reutilizáveis (Header, BalanceCard, StatCard, TransactionForm, TransactionList, CategoryBreakdown, AiReportDialog).
```
