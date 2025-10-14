💼 Desafio de Projeto – Modelagem Dimensional com Financial Sample
📘 Sumário

Descrição do Projeto

Objetivo

Base de Dados

Etapas do Desenvolvimento

Estrutura do Modelo Dimensional

Funções DAX Utilizadas

Etapas Realizadas no Power BI

Modelo em Estrela (Star Schema)

Materiais no Repositório

Conclusão

Autor

🧩 Descrição do Projeto

Neste desafio, o objetivo é criar um modelo dimensional baseado no formato Star Schema a partir da tabela única Financial Sample.

A proposta é transformar a tabela original em uma estrutura otimizada para análise, com tabelas dimensão e tabela fato, garantindo clareza e eficiência nas consultas e nos relatórios.

🎯 Objetivo

Criar tabelas dimensão e tabela fato a partir da Financial Sample;

Aplicar funções DAX e transformações no Power Query;

Montar um modelo em estrela (star schema);

Documentar o processo no GitHub, com foco em boas práticas de modelagem e clareza analítica.

📊 Base de Dados

Tabela original: Financials_origem

Utilizada como backup (modo oculto) e base para criação das demais tabelas;

Contém todas as colunas originais do Financial Sample.

⚙️ Etapas do Desenvolvimento

Importação da tabela Financial Sample

Importar a tabela original para o Power BI.

Renomeá-la para Financials_origem e ocultá-la no modelo.

Criação das tabelas Dimensão e Fato

Criar novas tabelas derivadas por meio do Power Query e/ou DAX.

Selecionar apenas as colunas relevantes para cada contexto.

Reorganização e limpeza dos dados

Remover colunas redundantes;

Corrigir tipos de dados;

Padronizar nomes e formatos;

Verificar nulos e valores inconsistentes.

Criação da Tabela de Datas

Criar uma tabela de calendário por meio da função CALENDAR().

🧱 Estrutura do Modelo Dimensional
🔹 Tabela Fato: F_Vendas

Contém os principais indicadores e chaves para relacionamento com as dimensões.

Campo	Descrição
SK_ID	Chave substituta
ID_Produto	Chave do produto
Produto	Nome do produto
Units Sold	Unidades vendidas
Sales Price	Valor da venda
Discount Band	Faixa de desconto
Segment	Segmento de mercado
Country	País
Sales	Valor total da venda
Profit	Lucro
Date	Chave de data
🔸 Dimensão Produto: D_Produtos
Campo	Descrição
ID_Produto	Identificador do produto
Produto	Nome
Média de Unidades Vendidas	Média das unidades vendidas
Média Valor de Vendas	Média dos valores de venda
Mediana Valor de Vendas	Mediana das vendas
Valor Máximo	Maior valor de venda
Valor Mínimo	Menor valor de venda
🔸 Dimensão Produto Detalhes: D_Produtos_Detalhes
Campo	Descrição
ID_Produto	Identificador
Discount Band	Faixa de desconto
Sale Price	Valor de venda
Units Sold	Unidades vendidas
Manufacturing Price	Custo de fabricação
🔸 Dimensão Descontos: D_Descontos
Campo	Descrição
ID_Produto	Identificador do produto
Discount	Percentual de desconto
Discount Band	Categoria de desconto
🔸 Dimensão Detalhes: D_Detalhes
Campo	Descrição
Campos não contemplados nas demais dimensões, mas relevantes para detalhar as vendas (por exemplo, Segment, Country, Salesperson).	
🔸 Dimensão Calendário: D_Calendário

Criada via DAX:

D_Calendário = CALENDAR (DATE(2013, 1, 1), DATE(2014, 12, 31))


Colunas adicionais:

Ano = YEAR(D_Calendário[Date])
Mês = FORMAT(D_Calendário[Date], "MMMM")
Trimestre = "T" & FORMAT(D_Calendário[Date], "Q")

🧮 Funções DAX Utilizadas

CALENDAR() → Criação da tabela de datas.

AVERAGE() → Média de valores.

MEDIAN() → Mediana de vendas.

MIN() / MAX() → Identificação de valores extremos.

RELATED() → Relacionamento entre tabelas no modelo.

IF() → Criação de colunas condicionais (ex: índice de produtos).

🧠 Etapas Realizadas no Power BI

Power Query:

Criação e cópia de tabelas derivadas da Financials_origem;

Agrupamentos e filtros;

Padronização de tipos de dados.

Modelagem:

Definição dos relacionamentos entre tabelas;

Criação de chaves substitutas (SK_ID);

Organização visual do modelo em formato de estrela.

Visualização:

Geração de medidas e indicadores baseados em lucro, vendas e desconto.

🌟 Modelo em Estrela (Star Schema)

Tabelas envolvidas:

Fato: F_Vendas

Dimensões:

D_Produtos

D_Produtos_Detalhes

D_Descontos

D_Detalhes

D_Calendário

Relacionamentos principais:

D_Produtos[ID_Produto] → F_Vendas[ID_Produto]
D_Produtos_Detalhes[ID_Produto] → F_Vendas[ID_Produto]
D_Descontos[ID_Produto] → F_Vendas[ID_Produto]
D_Detalhes[SK_ID] → F_Vendas[SK_ID]
D_Calendário[Date] → F_Vendas[Date]

🗂️ Materiais no Repositório

Financials.pbix – Arquivo do Power BI com modelo dimensional;

modelo_estrela.png – Imagem do diagrama estrela;

README.md – Documentação do projeto;

data/ – Pasta opcional com a base Financial Sample original.

✅ Conclusão

O modelo em estrela foi construído com base na tabela Financial Sample;

Foram aplicadas boas práticas de modelagem dimensional, funções DAX e limpeza de dados;

A estrutura resultante é eficiente, escalável e otimizada para análise de vendas e lucros.

👨‍💻 Autor

Juliano Camargo Ferreira
Profissional de TI | Engenharia de Dados | Power BI & SQL
🔗 LinkedIn

💻 GitHub
