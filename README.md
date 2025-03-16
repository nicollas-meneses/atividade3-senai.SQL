# 📌 Consultas SQL - Ranking de Vendas e Produtos Descontinuados

## 📖 Descrição
Este projeto contém consultas SQL para analisar o faturamento por categorias de produtos, identificar os produtos mais vendidos e listar os países para onde produtos descontinuados foram enviados.

## 📌 Funcionalidades
- Gerar um ranking das categorias mais vendidas por faturamento.
- Listar os 3 produtos mais vendidos da história da empresa.
- Identificar os países onde produtos descontinuados foram vendidos.

## 🚀 Consultas SQL
### 1️⃣ Ranking das Categorias Mais Vendidas por Faturamento
```sql
SELECT CT.CategoryName AS CATEGORIAS, SUM(OD.Quantity) AS VENDAS 
FROM Categories CT
INNER JOIN Products P ON P.CategoryID = CT.CategoryID
INNER JOIN [Order Details] OD ON OD.ProductID = P.ProductID
GROUP BY CT.CategoryName
ORDER BY VENDAS DESC;
```
📌 **Explicação:**
- As categorias de produtos são agrupadas e somadas pela quantidade vendida.
- Os resultados são ordenados em ordem decrescente de vendas.

### 2️⃣ Top 3 Produtos Mais Vendidos
```sql
SELECT TOP 3 P.ProductName AS PRODUTO, SUM(OD.Quantity) AS VENDAS
FROM Products P
INNER JOIN [Order Details] OD ON  OD.ProductID = P.ProductID
GROUP BY P.ProductName
ORDER BY VENDAS DESC;
```
📌 **Explicação:**
- A consulta retorna os 3 produtos mais vendidos de toda a história da empresa.
- Os produtos são agrupados e ordenados pelo total de vendas.

### 3️⃣ Produtos Descontinuados e os Países de Venda
```sql
SELECT P.ProductName AS PRODUTOS, OD.Quantity AS VENDAS, 
       O.ShipCountry AS PAIS, O.OrderDate AS DATA_DA_VENDA
FROM Products P
INNER JOIN [Order Details] OD ON OD.ProductID = P.ProductID
INNER JOIN Orders O ON O.OrderID = OD.OrderID
WHERE P.Discontinued = 1;
```
📌 **Explicação:**
- A consulta identifica quais produtos descontinuados foram vendidos.
- Lista a quantidade vendida, o país de destino e a data da venda.

## 🛠 Tecnologias Utilizadas
- **Banco de Dados Relacional (SQL)**
- **SQL Server** (ou compatível, como MySQL, PostgreSQL)

## 📝 Como Utilizar
1. Certifique-se de ter um banco de dados compatível configurado.
2. Copie e cole as consultas em seu gerenciador SQL.
3. Execute as consultas e analise os resultados.

---
**© 2025 - Desenvolvido por Nicollas Meneses**

