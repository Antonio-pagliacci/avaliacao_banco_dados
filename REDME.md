# README.md — Projeto de Banco de Dados: Loja de Peças

Este repositório apresenta um projeto completo de banco de dados relacional, desenvolvido para simular o funcionamento de uma loja de peças eletrônicas. O projeto foi elaborado com foco acadêmico, como parte da disciplina de Banco de Dados no curso de Análise e Desenvolvimento de Sistemas.

## 📌 Objetivo

Desenvolver um banco de dados funcional que:

- Armazene dados de clientes, funcionários, produtos e pedidos;
- Implemente integridade referencial e normalização até a 3ª Forma Normal (3FN);
- Permita a execução de consultas SQL complexas com junções, subconsultas e funções agregadas.

## 🛠️ Principais Ações no GitHub

Para editar e manter este repositório com um `README.md` bem estruturado, siga estas boas práticas:

### 1. 📥 Clonar o repositório

```bash
git clone https://github.com/seu-usuario/nome-do-repositorio.git
cd nome-do-repositorio
```

### 2. ✍️ Editar o README.md

Abra o arquivo `README.md` no editor de sua preferência (VS Code, Notepad++, etc.) e faça as alterações desejadas. Exemplo:

```bash
code README.md
```

### 3. 💾 Salvar e confirmar mudanças

```bash
git add README.md
git commit -m "Atualiza README com descrição do projeto"
```

### 4. ⬆️ Enviar para o GitHub

```bash
git push origin main
```

> Certifique-se de estar na branch correta, como `main` ou `master`.

## 🧱 Estrutura do Banco de Dados

### Entidades Principais

- **Clientes**: informações pessoais dos consumidores.
- **Funcionários**: colaboradores responsáveis pelos pedidos.
- **Produtos**: catálogo da loja com preços e estoque.
- **Pedidos**: histórico de compras associadas a clientes, funcionários e produtos.

### Relacionamentos

- Um cliente pode fazer vários pedidos.
- Um funcionário pode registrar vários pedidos.
- Um pedido está associado a apenas um produto, mas pode ser adaptado para múltiplos produtos em versões futuras.

### Modelo Físico

As tabelas possuem:

- **Chaves primárias** com `AUTO_INCREMENT`;
- **Chaves estrangeiras** com `FOREIGN KEY` para manter integridade entre as tabelas.

## 🧾 Scripts Disponíveis

- Criação do banco de dados (`CREATE DATABASE`);
- Criação das tabelas com definições de chaves primárias e estrangeiras;
- Inserção de dados fictícios (10 registros por tabela);
- Consultas SQL variadas:
  - Filtros com `LIKE`, `BETWEEN`, `IS NULL`, `NOT`;
  - Funções como `SUM()`, `AVG()`, `COUNT()`;
  - `JOINs` (`INNER`, `LEFT`, `RIGHT`, `CROSS`);
  - Subconsultas (`SELECT` aninhado);
  - Manipulação de datas com `CURDATE()`, `YEAR()`.

## 🧪 Exemplos de Consultas

### 1. Clientes cujo nome não começa com "A":

```sql
SELECT Nome FROM Clientes WHERE NOT Nome LIKE 'A%';
```

### 2. Produtos com preço acima da média dos pedidos:

```sql
SELECT Nome, Preco FROM Produtos WHERE Id_produto IN (
    SELECT Id_produto FROM Pedidos WHERE Preco > (
        SELECT AVG(Preco) FROM Pedidos
    )
);
```

### 3. Consulta geral com múltiplos JOINs:

```sql
SELECT
    ped.Id_pedido,
    ped.Data_pedido,
    cli.Nome AS NomeCliente,
    func.Nome AS NomeFuncionario,
    prod.Nome AS NomeProduto,
    ped.Quantidade,
    ped.Preco AS PrecoTotalItem
FROM Pedidos ped
JOIN Clientes cli ON ped.Id_cliente = cli.Id_cliente
JOIN Funcionarios func ON ped.Id_funcionario = func.Id_funcionario
JOIN Produtos prod ON ped.Id_produto = prod.Id_produto;
```

## 👨‍💻 Autor

**Antonio da Silva Pagliacci**\
Aluno de Análise e Desenvolvimento de Sistemas — Estácio\
📧 [contato.antoniopagliacci@gmail.com](mailto\:contato.antoniopagliacci@gmail.com)\
📱 (21) 98262-8025

---

> Projeto acadêmico com foco na prática de modelagem de dados, normalização e manipulação de dados via SQL no MySQL.

