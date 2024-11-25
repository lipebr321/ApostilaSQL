# 📊 Tutorial: Comando `SELECT` em SQL

O comando `SELECT` é fundamental em SQL, usado para consultar e recuperar dados de tabelas em um banco de dados. Neste tutorial, você aprenderá a usar `SELECT` com exemplos que vão do básico ao avançado.

---

## 📝 Estrutura Básica do `SELECT`

### Sintaxe

```sql
SELECT coluna1, coluna2, ...
FROM nome_da_tabela
WHERE condicao;
```

SELECT: Especifica as colunas a serem exibidas.
FROM: Indica a tabela onde os dados serão buscados.
WHERE: Filtra os registros com base em uma condição (opcional).

📋 Exemplos Práticos
1. Selecionar Todas as Colunas de uma Tabela

```sql

SELECT * 
FROM Produtos;
```

O símbolo * indica que todas as colunas serão retornadas.
2. Selecionar Colunas Específicas
```sql

SELECT Nome, Preco 
FROM Produtos;
```

Retorna apenas as colunas Nome e Preco da tabela Produtos.
3. Filtrar Registros com WHERE

```sql

SELECT Nome, Estoque 
FROM Produtos
WHERE Estoque > 10;
```

Mostra produtos com mais de 10 unidades em estoque.

4. Utilizar AND e OR em Condições
```sql

SELECT Nome, Preco 
FROM Produtos
WHERE Preco > 1000 AND Estoque > 5;

```
Retorna produtos com preço acima de 1000 e mais de 5 unidades em estoque.
5. Ordenar Resultados com ORDER BY

```sql

SELECT Nome, Preco 
FROM Produtos
ORDER BY Preco DESC;
```

Ordena os produtos por preço em ordem decrescente. Use ASC para ordem crescente.
6. Pesquisar Textos com LIKE

```sql

SELECT Nome 
FROM Clientes
WHERE Nome LIKE 'A%';
```

Retorna nomes que começam com a letra A.
Wildcards:

%: Representa qualquer sequência de caracteres.
_: Representa um único caractere.

7. Limitar o Número de Resultados com LIMIT

```sql

SELECT Nome, Preco 
FROM Produtos
LIMIT 5;
```

Retorna apenas os primeiros 5 registros.
8. Usar DISTINCT para Eliminar Duplicatas

```sql

SELECT DISTINCT Categoria 
FROM Produtos;
```

Mostra as categorias de produtos, sem duplicar valores repetidos.
📊 Funções Agregadas
9. Contar Registros com COUNT

```sql

SELECT COUNT(*) AS TotalProdutos 
FROM Produtos;
```

Retorna o número total de produtos na tabela.
10. Calcular Média com AVG

```sql

SELECT AVG(Preco) AS PrecoMedio 
FROM Produtos;
```

Calcula o preço médio dos produtos.
11. Encontrar Valores Máximos e Mínimos

```sql

SELECT MAX(Preco) AS PrecoMaximo, MIN(Preco) AS PrecoMinimo 
FROM Produtos;
```

Retorna o maior e o menor preço entre os produtos.
12. Agrupar Dados com GROUP BY

```sql

SELECT Categoria, COUNT(*) AS TotalPorCategoria 
FROM Produtos
GROUP BY Categoria;
```

Agrupa os produtos por categoria e conta quantos existem em cada grupo.
13. Filtrar Grupos com HAVING

```sql

SELECT Categoria, AVG(Preco) AS PrecoMedio 
FROM Produtos
GROUP BY Categoria
HAVING AVG(Preco) > 100;
```

Mostra categorias onde o preço médio é maior que 100.
🌐 Joins: Combinando Tabelas
14. INNER JOIN

```sql

SELECT Clientes.Nome, Pedidos.DataPedido 
FROM Clientes
INNER JOIN Pedidos ON Clientes.ID = Pedidos.ClienteID;
```

Retorna dados que possuem correspondência em ambas as tabelas.
15. LEFT JOIN

```sql

SELECT Clientes.Nome, Pedidos.DataPedido 
FROM Clientes
LEFT JOIN Pedidos ON Clientes.ID = Pedidos.ClienteID;
```

Retorna todos os clientes, mesmo aqueles que não têm pedidos.

🚀 Exercícios Práticos
Selecione todos os produtos cujo preço seja maior que 500.
Liste o nome e o estoque dos produtos da categoria "Eletrônicos".
Mostre o total de produtos em cada categoria, ordenado do maior para o menor.
Selecione os 3 produtos mais caros da tabela.
Crie uma consulta que liste todos os pedidos feitos por um cliente específico (use JOIN).
🎓 Conclusão
O comando SELECT é o coração das consultas SQL. Este tutorial cobriu desde a recuperação simples de dados até o uso de funções agregadas e JOINs. Com prática, você poderá realizar consultas poderosas e extrair informações valiosas dos bancos de dados.

Feito com 💙 por Luis Felipe Pereira.
