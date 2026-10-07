# Normalização de Banco de Dados – 3FN

### Professora Ellen Martins Lopes da Silva - 28/09/2026

## 📚 Sobre o Projeto

Este projeto apresenta a normalização de um banco de dados de pedidos, aplicando as três primeiras formas normais (1FN, 2FN e 3FN).

O objetivo é organizar as informações, reduzir redundâncias e evitar anomalias de inserção, atualização e exclusão.

## 🎯 Objetivos da Atividade

* Identificar a chave candidata da estrutura original.
* Identificar as dependências funcionais.
* Apontar redundâncias e anomalias.
* Aplicar a Primeira Forma Normal (1FN).
* Aplicar a Segunda Forma Normal (2FN).
* Aplicar a Terceira Forma Normal (3FN).
* Construir o modelo relacional final.

## 🔑 Chave Candidata

A chave candidata da estrutura original é composta por:

* `PedidoID`
* `ProdutoID`

Essa combinação identifica cada produto dentro de um pedido.

## 🔗 Dependências Funcionais

* `ClienteID` → ClienteNome, ClienteTelefone, CEP, Numero
* `CEP` → Logradouro, Cidade
* `RestauranteID` → RestauranteNome, TelefoneRestaurante
* `ProdutoID` → ProdutoNome, PrecoProduto
* `EntregadorID` → EntregadorNome, NotaEntregador
* `PedidoID` → DataPedido, Observacao, ClienteID, RestauranteID, EntregadorID
* `(PedidoID, ProdutoID)` → Quantidade

## 📋 Formas Normais

### 1FN – Primeira Forma Normal

Cada campo deve conter apenas um valor, sem listas ou grupos de informações na mesma célula. Cada produto de um pedido é registrado individualmente, com sua respectiva quantidade.

### 2FN – Segunda Forma Normal

Elimina as dependências parciais, separando os dados que dependem apenas de parte da chave composta.

Os dados foram organizados nas tabelas `PEDIDO`, `PRODUTO` e `ITEM_PEDIDO`.

### 3FN – Terceira Forma Normal

Elimina as dependências transitivas.

A tabela `CEP` foi criada para armazenar o logradouro e a cidade, evitando a repetição dessas informações na tabela `CLIENTE`.

## 🗂️ Modelo Relacional Final

O modelo foi dividido em sete tabelas:

1. `CLIENTE`
2. `CEP`
3. `RESTAURANTE`
4. `PRODUTO`
5. `ENTREGADOR`
6. `PEDIDO`
7. `ITEM_PEDIDO`

### Principais Chaves

* **CLIENTE:** `ClienteID` (PK) e `CEP` (FK)
* **CEP:** `CEP` (PK)
* **RESTAURANTE:** `RestauranteID` (PK)
* **PRODUTO:** `ProdutoID` (PK)
* **ENTREGADOR:** `EntregadorID` (PK)
* **PEDIDO:** `PedidoID` (PK)
* **ITEM_PEDIDO:** `PedidoID` (PK/FK) e `ProdutoID` (PK/FK)

## ✅ Conclusão

A normalização organizou os dados em tabelas relacionadas por chaves primárias e estrangeiras, reduzindo repetições e melhorando a integridade e a consistência do banco de dados.

---
