# **Consultas SQL e Insights** 🧑‍💻💡

Abaixo estão as consultas SQL com explicações para extrair informações importantes de um banco de dados, como idade dos funcionários, contagem de clientes por país, produtos mais vendidos, e muito mais! 👇

---

## 1. **Idade dos Funcionários a Partir do Ano de Nascimento** 🎂

```sql
SELECT 
    FirstName,
    DATE_FORMAT(BirthDate, '%d/%m') AS aniversario,
    YEAR(CURDATE()) - YEAR(BirthDate) - 
    (DATE_FORMAT(CURDATE(), '%m%d') < DATE_FORMAT(BirthDate, '%m%d')) AS idade
FROM 
    Employees;
Explicação:
```
Esta consulta calcula a idade de cada funcionário com base na data de nascimento e também exibe o aniversário (dia e mês). 🎉

2. Contagem de Clientes por País 🌍
   
```sql
SELECT 
    'Total Geral' AS Paises,
    COUNT(*) AS quantidade
FROM 
    Customers

UNION ALL

SELECT 
    Country AS Categories,
    COUNT(*) AS quantidade
FROM 
    Customers
GROUP BY 
    Country;
```
Explicação:

Esta consulta traz o número total de clientes, além de contar quantos clientes existem por país. 🌎

3. Top 5 Produtos Mais Vendidos por Categoria 🛍️

```sql

SELECT 
    p.ProductName AS nome_produto,
    c.CategoryName AS nome_categoria,
    SUM(od.Quantity) AS quantidade_total,
    FORMAT(SUM(od.Quantity * p.Price), 2, 'de_DE') AS valor_total_reais
FROM 
    OrderDetails od
JOIN 
    Products p ON od.ProductID = p.ProductID
JOIN 
    Categories c ON p.CategoryID = c.CategoryID
GROUP BY 
    p.ProductName, c.CategoryName
ORDER BY 
    quantidade_total DESC, SUM(od.Quantity * p.Price) DESC
LIMIT 5;
```
Explicação:

Traz o valor total vendido e a quantidade total dos top 5 produtos por categoria. 💸

4. Top 5 Funcionários que Mais Venderam 🏆
   
```sql

SELECT 
    CONCAT(e.FirstName, ' ', e.LastName) AS nome_funcionario,
    FORMAT(SUM(od.Quantity * p.Price), 2, 'de_DE') AS total_vendas_reais
FROM 
    Employees e
JOIN 
    Orders o ON e.EmployeeID = o.EmployeeID
JOIN 
    OrderDetails od ON o.OrderID = od.OrderID
JOIN 
    Products p ON od.ProductID = p.ProductID
GROUP BY 
    e.EmployeeID, e.FirstName, e.LastName
ORDER BY 
    SUM(od.Quantity * p.Price) DESC
LIMIT 5;
```
Explicação:

Esta consulta traz os top 5 funcionários com base no valor total vendido. 🏅

5. Clientes que Mais Compraram 🛒
   
```sql

SELECT 
    c.ContactName AS nome_cliente,
    SUM(od.Quantity) AS quantidade_comprada,
    FORMAT(SUM(od.Quantity * p.Price), 2, 'de_DE') AS valor_total_reais
FROM 
    Customers c
JOIN 
    Orders o ON c.CustomerID = o.CustomerID
JOIN 
    OrderDetails od ON o.OrderID = od.OrderID
JOIN 
    Products p ON od.ProductID = p.ProductID
GROUP BY 
    c.CustomerID, c.ContactName
ORDER BY 
    SUM(od.Quantity * p.Price) DESC;
```
Explicação:

Lista os clientes com maior quantidade comprada e valor total gasto. 🛍️

# Insights de Vendas e Desempenho 📊
Aqui estão alguns insights adicionais que podem ser extraídos do banco de dados:

1. Vendas Mensais por Período 📅
```sql

SELECT 
    YEAR(o.OrderDate) AS ano,
    MONTHNAME(o.OrderDate) AS mes,
    SUM(od.Quantity * p.Price) AS total_vendas
FROM Orders o
JOIN OrderDetails od ON o.OrderID = od.OrderID
JOIN Products p ON od.ProductID = p.ProductID
GROUP BY YEAR(o.OrderDate), MONTH(o.OrderDate)
ORDER BY ano, MONTH(o.OrderDate);

```
Explicação:

Aqui, vemos as vendas mensais por ano e mês, com os nomes dos meses ao invés de números. 🗓️

2. Top 5 Produtos Mais Vendidos 🔝
   
```sql

SELECT 
    p.ProductName AS nome_produto,
    SUM(od.Quantity) AS quantidade_comprada,
    FORMAT(SUM(od.Quantity * p.Price), 2, 'de_DE') AS valor_total
FROM OrderDetails od
JOIN Products p ON od.ProductID = p.ProductID
GROUP BY p.ProductName
ORDER BY quantidade_comprada DESC
LIMIT 5;
```
Explicação:

Exibe os produtos mais vendidos com base na quantidade comprada e no valor total. 🛒

3. Gasto Médio por Cliente 💳

```sql

SELECT 
    c.CustomerName AS nome_cliente,
    FORMAT(AVG(od.Quantity * p.Price), 2 ,'de_DE') AS gasto_medio
FROM Customers c
JOIN Orders o ON c.CustomerID = o.CustomerID
JOIN OrderDetails od ON o.OrderID = od.OrderID
JOIN Products p ON od.ProductID = p.ProductID
GROUP BY c.CustomerID
ORDER BY AVG(od.Quantity * p.Price) DESC;
```
Explicação:

Calcula o gasto médio de cada cliente, ajudando a identificar os clientes mais rentáveis. 💰
# Conclusão 🎉
Com essas consultas SQL, podemos extrair dados valiosos sobre clientes, produtos, vendas e funcionários para tomar decisões mais informadas. Esses insights ajudam a entender o comportamento do consumidor, o desempenho de vendas e a otimização de estoque, promovendo um melhor planejamento estratégico! 📈

Feito com 💙 por Luis Felipe Pereira.





