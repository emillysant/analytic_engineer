## Projeto dbt do banco Northwind

Este documento descreve a estrutura e as práticas recomendadas para o projeto de dbt (Data Build Tool) para o banco de dados Northwind. O projeto dbt consiste em transformar os dados brutos do banco Northwind em modelos dimensionais e fatos para análise.
Visão Geral do Projeto

O objetivo principal deste projeto dbt é fornecer um conjunto de modelos estruturados para facilitar a análise de dados do banco Northwind. O banco de dados Northwind contém informações sobre produtos, clientes, funcionários, pedidos, etc. O projeto dbt organiza esses dados em modelos dimensionais e fatos para permitir uma análise mais eficiente e significativa.
Fontes de Dados
Banco de Dados ERP

O banco de dados ERP é a fonte principal de dados para este projeto. Ele contém várias tabelas relevantes para análise, localizadas no esquema raw_northwind:

    product: Informações sobre produtos.
    category: Categorias de produtos.
    supplier: Fornecedores de produtos.
    _order_: Tabela de pedidos.
    orderdetail: Detalhes dos pedidos.
    employee: Informações sobre os funcionários.
    customer: Informações sobre os clientes.
    shipper: Informações sobre as transportadoras.

### Tabelas de Staging

As tabelas de staging representam os dados brutos extraídos do banco de dados ERP. Esses dados passarão por transformações e serão carregados em modelos dimensionais e fatos. As tabelas de staging incluem:

    stg_produtos: Dados brutos dos produtos.
    stg_fornecedores: Dados brutos dos fornecedores.
    stg_ordens: Dados brutos dos pedidos.
    stg_ordem_detalhes: Dados brutos dos detalhes dos pedidos.
    stg_funcionario: Dados brutos dos funcionários.
    stg_cliente: Dados brutos dos clientes.
    stg_transportadora: Dados brutos das transportadoras.

### Modelos Dimensionais

Os modelos dimensionais são estruturas que organizam os dados em torno de processos de negócios ou áreas de interesse. Eles são projetados para facilitar a análise e a consulta. Os modelos dimensionais incluídos neste projeto são:

    dim_produtos: Dimensão de produtos.
    dim_fornecedores: Dimensão de fornecedores.
    dim_funcionarios: Dimensão de funcionários.
    dim_clientes: Dimensão de clientes.
    dim_transportadoras: Dimensão de transportadoras.

### Modelo Fato

O modelo fato contém as medidas quantitativas que serão analisadas. Neste projeto, o modelo fato é:

    fct_vendas: Tabela de fatos de vendas.

### Rodando o projeto

- dbt run
- dbt build

### Rodando test
O teste de verificação de vendas em 2012 é uma consulta SQL que calcula o total bruto das vendas realizadas no ano de 2012 a partir do modelo fato fct_vendas. Este teste é importante para validar se os valores de vendas em 2012 estão corretos de acordo com as expectativas da equipe de contabilidade.

- dbt test -s total_vendas_2012

![image](https://github.com/emillysant/analytics_engineer-dbt_northwind/assets/70452464/ade47ab9-6961-4a09-838b-4ea1b94babef)

### Gerando documentação 

- dbt docs generate
