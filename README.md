# Projeto de Banco de Dados para Vendas 🛍️

Este repositório contém a implementação de um banco de dados relacional utilizando MySQL, com foco no gerenciamento de vendas, estoque e clientes. O projeto é projetado para ser executado dentro de containers Docker, garantindo uma configuração portátil e escalável. A solução inclui tabelas para **produtos**, **clientes**, **vendas**, e **movimentações de estoque**, além de **triggers**, **procedures** e **views** que automatizam processos e fornecem relatórios gerenciais.

## Funcionalidades ⚙️

O banco de dados foi estruturado para suportar um sistema de vendas completo, com as seguintes funcionalidades principais:

### **Tabelas 📊**

- **produtos**: Armazena informações sobre os produtos disponíveis para venda, incluindo nome, categoria, preço e quantidade em estoque.
- **clientes**: Armazena os dados dos clientes, como nome, email e telefone.
- **vendas**: Registra as vendas realizadas, incluindo o produto vendido, o cliente, a quantidade e a data da venda.
- **movimentacoes_estoque**: Controla as entradas e saídas de estoque de produtos, associando cada movimentação ao produto correspondente.

### **Triggers 🔄**

- **after_insert_venda**: Após a inserção de uma venda, a trigger é acionada para atualizar o estoque do produto vendido e registrar a movimentação de saída do estoque.

### **Procedures 📝**

- **registrar_venda**: Procedure que registra uma venda, verificando se há estoque suficiente para atender à quantidade solicitada. Caso o estoque seja insuficiente, a venda não é realizada e uma exceção é gerada.

### **Views 📅**

- **relatorio_vendas_mensais**: View que gera um relatório de vendas mensais, agrupando as vendas por mês e fornecendo métricas como total de vendas, quantidade de itens vendidos e receita gerada.

### **Metabase Integration 📊**

Este projeto inclui a configuração do [Metabase](https://www.metabase.com/), uma ferramenta de visualização de dados e criação de dashboards, para análise de vendas. O Metabase se conecta diretamente ao banco de dados MySQL para fornecer insights e relatórios visuais.

## Estrutura do Projeto 🗂️

A estrutura de diretórios do projeto é a seguinte:
### **docker-compose.yml** 🐳

Este arquivo configura os containers do Docker para o MySQL e o Metabase. O MySQL é configurado com um banco de dados `Estoque`, que contém todas as tabelas, triggers e procedures. O Metabase é configurado para rodar na porta `3000` e fornecer dashboards para o usuário.

### **init.sql** 🗃️

Este é o script SQL que cria o banco de dados e todas as tabelas necessárias, além de definir as triggers e procedures. Ele também popula as tabelas com dados de exemplo para testes.

### **sql-check.yml** ✅

Este arquivo é usado pelo GitHub Actions para automatizar testes SQL no banco de dados. Ele garante que o MySQL esteja funcionando corretamente sempre que há alterações no código.

## Como Rodar o Projeto Localmente 🖥️

### Requisitos 📝

- **Docker**: Para rodar os containers do MySQL e Metabase.
- **Docker Compose**: Para gerenciar os containers de forma simplificada.

### Passos para Execução 🔧

1. Clone o repositório:
   ```bash
   git clone https://github.com/Th-SoTi/projeto_sql.git
   cd projeto_sql

## 👤 Autor

Feito com ❤ por [SoTi](https://github.com/Th-SoTi). Sinta-se à vontade para contribuir e sugerir melhorias!
