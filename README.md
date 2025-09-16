# Primeiro Projeto Logico de Banco de Dados ecommerce

  Projeto de modelagem de banco de dados para um sistema de e-commerce, desenvolvido em MySQL Workbench, contemplando clientes, produtos, pedidos, pagamentos, fornecedores e estoque.

## Sobre o Projeto

Este projeto foi desenvolvido como parte do curso da DIO.me utilizando MySQL Workbench, com o objetivo de criar um banco de dados relacional para um sistema de e-commerce. O banco de dados contempla funcionalidades de gestão de clientes, produtos, fornecedores, vendedores, pedidos, pagamentos e estoque.

## Funcionalidades

* Clientes: cadastro de pessoas físicas (PF) e jurídicas (PJ), com validação de CPF/CNPJ.

* Produtos: registro de produtos com categorias, classificação infantil, avaliação e tamanho.

* Pedidos (Orders): gerenciamento de pedidos, status, descrição e valores de frete.

* Pagamentos: controle de tipos de pagamento e limites disponíveis por cliente.

* Fornecedores e Vendedores: cadastro de fornecedores e vendedores com informações de contato e CNPJ/CPF.

* Estoque (ProductStorage): gerenciamento de estoque, localização de produtos e quantidade disponível.

* Relacionamentos: tabelas de associação entre produtos, fornecedores, vendedores e ordens de pedido.

* Consultas SQL: exemplos de queries para análises como total de clientes, pedidos por status, produtos infantis, estoque por categoria e valor médio de frete.

## Tabelas Principais

1. cliente

2. product

3. payments

4. orders

5. delivery

6. productStorage

7. supplier

8. seller

9. productseller

10. ProductOrder

11. storageLocation

12. productSupplier

## Queries de Exemplo

* Total de clientes cadastrados

* Clientes de determinado estado

* Pedidos confirmados

* Produtos infantis

* Estoque total por categoria

* Valor médio de frete de pedidos confirmados

## Tecnologias Utilizadas

* MySQL

* MySQL Workbench para modelagem e execução de queries

## Objetivo do Projeto

Este projeto visa demonstrar habilidades de modelagem relacional, criação de tabelas, relacionamentos e consultas SQL complexas, além de boas práticas como uso de enum, constraints, foreign keys e auto_increment.
