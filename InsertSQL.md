# 📥 Tutorial Completo: Comando `INSERT` em SQL

## O comando `INSERT` é usado para adicionar novos registros (linhas) em uma tabela de banco de dados. Neste tutorial, você aprenderá como utilizar o `INSERT` com exemplos detalhados para diferentes situações.

---

## 📚 Estrutura Básica do Comando `INSERT`

### Sintaxe Simples
```sql
INSERT INTO NomeDaTabela (Coluna1, Coluna2, Coluna3)
VALUES (Valor1, Valor2, Valor3);
```
 NomeDaTabela: Nome da tabela onde os dados serão inseridos.
 Coluna1, Coluna2, Coluna3: Nomes das colunas que receberão os valores.

 VALUES: Palavra-chave que indica os valores a serem inseridos.
 Valor1, Valor2, Valor3: Os valores correspondentes às colunas especificadas.

# 🛠️ Exemplos Práticos
## Exemplo 1: Inserir um Registro Simples

```

```sql
INSERT INTO Produtos (Nome, Preco, Estoque)
VALUES ('Notebook', 3500.00, 10);

```

 Aqui estamos inserindo um produto chamado "Notebook" com preço de R$ 3500.00 e estoque de 10 unidades.

## Exemplo 2: Inserir Múltiplos Registros ao Mesmo Tempo


```sql

INSERT INTO Produtos (Nome, Preco, Estoque)
VALUES
('Smartphone', 1200.00, 50),
('Teclado', 150.00, 30),
('Monitor', 850.00, 20);

```
 Adicionamos três produtos de uma vez: um Smartphone, um Teclado e um Monitor.

## Exemplo 3: Inserir Valores em Todas as Colunas
### Se você deseja inserir valores em todas as colunas, não é necessário especificá-las:

```sql

INSERT INTO Produtos
VALUES (1, 'Mouse', 50.00, 100);
```

#⚠️ Atenção: Certifique-se de que os valores estão na mesma ordem definida ao criar a tabela.

## Exemplo 4: Inserir Valores Parciais com Colunas Opcionais

 Se algumas colunas têm valores padrão ou permitem NULL, você pode omiti-las:

```sql

INSERT INTO Produtos (Nome, Preco)
VALUES ('Cadeira Gamer', 750.00);
```

 O campo Estoque será preenchido com o valor padrão (se definido) ou ficará nulo.

## Exemplo 5: Inserir Dados com Subconsultas

 É possível inserir dados de outra tabela:

```sql

INSERT INTO Produtos (Nome, Preco, Estoque)
SELECT Nome, Preco, Estoque
FROM ProdutosAntigos
WHERE Estoque > 0;

```

 Aqui copiamos produtos de uma tabela antiga para a nova, apenas se tiverem estoque maior que zero.

# 🎨 Usando Variáveis e Funções no INSERT

## Exemplo 6: Inserir Data Atual com Funções

```sql

INSERT INTO Vendas (ProdutoID, Quantidade, DataVenda)
VALUES (1, 2, CURRENT_DATE);
```

 CURRENT_DATE insere a data atual.


# 🧩 Cenários Específicos

## Exemplo 7: Inserir Dados com Identificador Automático
 Se sua tabela possui uma coluna com AUTO_INCREMENT, você pode omitir essa coluna no INSERT:

```sql

CREATE TABLE Clientes (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Nome VARCHAR(100),
    Email VARCHAR(100)
);
```

```sql
INSERT INTO Clientes (Nome, Email)
VALUES ('Luis Felipe', 'luis.felipe@email.com');
```

 O campo ID será gerado automaticamente.

## Exemplo 8: Inserir Dados em Tabelas Relacionadas
 Quando tabelas possuem chaves estrangeiras, insira os dados na ordem correta para evitar erros:

```sql

CREATE TABLE Clientes (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Nome VARCHAR(100)
);
```
```sql

CREATE TABLE Pedidos (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    ClienteID INT,
    DataPedido DATE,
    FOREIGN KEY (ClienteID) REFERENCES Clientes(ID)
);

```

 -- Primeiro insira o cliente
 INSERT INTO Clientes (Nome)
 VALUES ('Maria Silva');

 -- Depois insira o pedido, usando o ID do cliente

```sql
INSERT INTO Pedidos (ClienteID, DataPedido)
VALUES (1, '2024-11-17');
```


# 🛑 Tratando Erros Comuns no INSERT
 Erro de tipos incompatíveis: Certifique-se de que os valores inseridos correspondem aos tipos definidos nas colunas.

```sql

-- Exemplo de erro:
INSERT INTO Produtos (Nome, Preco, Estoque)
VALUES ('Mesa', 'Cem Reais', 5); -- Preco deve ser numérico.
Violação de chave primária ou única:
```
```sql

INSERT INTO Clientes (ID, Nome)
VALUES (1, 'João Souza'); -- ID 1 já pode estar em uso.
Colunas obrigatórias sem valor:
```
```sql

INSERT INTO Produtos (Nome)
VALUES (NULL); -- Nome não pode ser nulo.

```

# 🚀 Exercícios Práticos
 Crie uma tabela chamada Funcionarios com as colunas ID, Nome, Cargo, Salario e DataContratacao. Insira 3 funcionários diferentes.

 Crie uma tabela chamada Estoque com colunas para ProdutoID, NomeProduto e Quantidade. Insira 5 produtos e simule um aumento de estoque.

 Crie um banco de dados para uma biblioteca, com tabelas para Livros, Autores e Emprestimos, e insira dados que reflitam uma operação de empréstimo.


# 🎉 Conclusão
 O comando INSERT é uma das operações mais fundamentais em SQL, permitindo adicionar dados às tabelas de forma simples ou avançada. Com prática, você será capaz de lidar com qualquer situação, desde inserções básicas até cenários complexos com tabelas relacionadas.

Feito com 💙 por Luis Felipe Pereira.
