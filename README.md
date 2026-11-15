Porsche Sales Intelligence

Dashboard interativo de vendas da Porsche que desenvolvi para transformar uma planilha de vendas em uma análise visual, rápida e fácil de explorar. Tudo roda em um único arquivo HTML, sem backend e sem instalação.

O visual foi inspirado no site oficial da Porsche Brasil: fundo escuro, detalhes em dourado e vermelho e tipografia refinada.

Projeto independente, sem vínculo com a Porsche AG. Marcas e nomes de modelos pertencem aos seus respectivos titulares e aparecem aqui apenas para fins de demonstração e análise.

Objetivo

Reunir modelos, cidades, anos de modelo e formas de pagamento em uma única tela, para responder perguntas comerciais sem precisar abrir a planilha.

Pergunta de negócio	Como o dashboard responde
Quais os principais modelos vendidos por cidade?	Tabela Insights por Cidade, com modelo líder, volume e receita de cada praça
Qual ano de modelo mais saiu em um período?	Gráfico Vendas por Ano do Modelo, com o pico destacado, e KPI Ano de Modelo Líder
Quais carros são mais populares em cada cidade?	Insights por Cidade combinado com Top Cidades por Volume
Como as vendas evoluem ao longo do tempo?	Gráfico Evolução de Vendas, com vendas mensais e receita acumulada
Funcionalidades
Filtros

Multi-seleção, com busca nas listas longas, e combináveis entre si:

Modelo da Porsche
Ano do modelo (model year)
Cidade
Forma de pagamento (pay method)

Cada filtro recalcula KPIs, gráficos e tabela em tempo real. Também há o botão Limpar filtros e um contador com o total de vendas exibidas.

KPIs
Vendas totais
Receita total
Ticket médio
Modelo líder
Ano de modelo líder
Cidade líder, com o percentual de entregas concluídas no recorte
Visualizações
Evolução de Vendas: barras com as vendas por mês e linha com a receita acumulada
Modelos Mais Vendidos: top 10 por volume
Forma de Pagamento: distribuição em rosca
Vendas por Ano do Modelo
Top Cidades por Volume
Insights por Cidade: ranking com modelo líder, unidades e receita
Como usar

Basta abrir o arquivo porsche_dashboard.html em qualquer navegador moderno. Não há build nem dependências para instalar.

O Chart.js e as fontes são carregados por CDN, então é necessário estar conectado à internet.

Estrutura do projeto
.
├── porsche_dashboard.html    # Dashboard completo (HTML, CSS, JS e dados)
└── README.md
Dados

A base de origem é a planilha Planilha_base_Porsche_Sanitizada, aba Sanitized, com 100 registros de vendas já tratados. Os dados ficam embutidos no próprio HTML, dentro de uma tag <script id="raw-data" type="application/json">.

Coluna	Uso no dashboard
SaleDateSanitized	Linha do tempo
PorscheModelSanitized	Filtro de modelo e rankings
ModelYearSanitized	Filtro e gráfico de ano do modelo
SalesPriceSanitized	Receita e ticket médio (valores em USD)
PayMethodSanitized	Filtro e gráfico de pagamento
CitySanitized	Filtro, ranking e insights por cidade
DeliveryStatusSanitized	Percentual de entregas concluídas

A aba Normalizedb ou Deparas guarda as tabelas de normalização (status de entrega, estado e cidade) usadas na sanitização e não é lida pelo dashboard.

Observações sobre a qualidade dos dados
24 dos 100 registros têm SaleDateSanitized igual a INVALID. Eles entram em todos os KPIs e gráficos, exceto na Evolução de Vendas, que exige data válida. O painel exibe uma nota informando quantos registros ficaram de fora dessa visão.
Existem datas de venda posteriores à data atual (até 2027), o que sugere pedidos futuros ou erros de digitação na base de origem.
Tecnologias
HTML, CSS e JavaScript puros
Chart.js 4.4 para os gráficos
Google Fonts: Inter e Barlow Condensed
Python (pandas) para ler a planilha e gerar o JSON embutido
Design
Elemento	Escolha
Fundo	Preto profundo 
#08080a, com painéis em grafite
Destaque principal	Dourado 
#c9a769
Ênfase	Vermelho 
#d5001c, usado no líder de cada ranking e na linha de receita
Títulos e números	Barlow Condensed
Texto e interface	Inter

O layout é responsivo e se adapta a telas menores.

Próximos passos
Filtro por intervalo de datas
Exportação dos dados filtrados em CSV
Carregamento direto de arquivo .xlsx no navegador
Tratamento das datas inválidas na origem
