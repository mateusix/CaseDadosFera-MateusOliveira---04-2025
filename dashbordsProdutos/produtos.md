# Dashboard Produtos - SQLs Documentados

---

## Título do SQL

Produtos com maior número de avaliações negativas

---

## Código SQL

```sql
-- Produtos com maior número de avaliações negativas --
SELECT 
    p.title AS produto,
    COUNT(r.id) AS total_avaliacoes,
    SUM(CASE WHEN r.rating <= 2 THEN 1 ELSE 0 END) AS avaliacoes_ruins,
    ROUND((SUM(CASE WHEN r.rating <= 2 THEN 1 ELSE 0 END) * 100.0) / COUNT(r.id), 2) AS percentual_ruim
FROM products p
JOIN reviews r ON p.id = r.product_id
GROUP BY p.title
HAVING percentual_ruim >= 50
ORDER BY percentual_ruim DESC, total_avaliacoes DESC;






---

## Título do SQL

Produtos mais bem avaliados

---

## Código SQL

``sql
-- Produtos mais bem avaliados --
SELECT 
    p.title AS produto,
    ROUND(AVG(r.rating), 2) AS media_avaliacoes,
    COUNT(r.id) AS total_avaliacoes
FROM products p
JOIN reviews r ON p.id = r.product_id
GROUP BY p.title
HAVING media_avaliacoes >= 4
ORDER BY media_avaliacoes DESC, total_avaliacoes DESC;







---

## Título do SQL

Produtos mais vendidos por estado

---

## Código SQL

``sql
-- Produtos Mais Vendidos por Estado --
SELECT 
    p.state AS estado,
    pr.title AS produto,
    COUNT(o.id) AS quantidade_vendida
FROM people p
JOIN orders o ON p.id = o.user_id
JOIN products pr ON o.product_id = pr.id
GROUP BY estado, produto
ORDER BY estado, quantidade_vendida DESC;






---

## Título do SQL

Top 10 Produtos que menos venderam

---

## Código SQL

``sql
--top 10 Produtos encalhados (que menos venderam)--
SELECT 
    p.title AS produto,
    COUNT(o.id) AS quantidade_vendida
FROM products p
LEFT JOIN orders o ON o.product_id = p.id
GROUP BY produto
ORDER BY quantidade_vendida ASC
LIMIT 10;






---

## Título do SQL

Top 5 Produtos mais vendidos

---

## Código SQL

``sql
--Top 5 Produtos Mais Vendidos--
SELECT 
    p.title AS produto,
    COUNT(o.id) AS quantidade_vendida
FROM orders o
JOIN products p ON o.product_id = p.id
GROUP BY produto
ORDER BY quantidade_vendida DESC
LIMIT 5;









