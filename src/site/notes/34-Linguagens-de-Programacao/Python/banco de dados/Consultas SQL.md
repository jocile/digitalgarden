---
{"dg-publish":true,"permalink":"/34-linguagens-de-programacao/python/banco-de-dados/consultas-sql/","noteIcon":1,"updated":"2025-07-02T16:28:43.339-03:00","dg-note-properties":{}}
---


![Consultas SQL-1751482986700.png](/img/user/34-Linguagens-de-Programacao/Python/banco%20de%20dados/Consultas%20SQL-1751482986700.png)

>[!note] 1- Comece pelo básico: SELECT 
> `SELECT nome, idade`
> `FROM clientes;`

>[!note] 2- Filtre dados com WHERE
> `SELECT * FROM pedidos`
> `WHERE status = 'entregue;`

>[!note] 3- Organize com ORDERBY
> `SELECT * FROM produtos`
> `ORDER BY preco DESC;`

>[!note] 4- Limite com LIMIT
> `SELECT * FROM usuarios`
> `LIMIT 10;`


>[!note] 5- Combine condições: AND & OR
> `SELECT * FROM vendas`
> `WHERE preco > 100`
> `AND data = = '2025-01-1';`

>[!caution] 6- Evite `SELECT *` em produção
> 🚫Use apenas as colunas necessârias para melhorar performance

>[!note] 7- Buscas parciais com LIKE
> `SELECT * FROM clientes`
> `WHERE nome LIKE 'JO%;`

>[!note] 8- Agrupe com GROUP BY
> `SELECT departamento,`
> `COUNT(*) FROM`
> `funcionarios GROUP`
> `BY departamento`
