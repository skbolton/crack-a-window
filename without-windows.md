# Solving without Window Functions

Perform the aggregation and in a separate query join onto the original rows to get full picture.

```sql
SELECT * from products product
JOIN (
  -- Aggregation query
  SELECT family, avg(price)
  FROM products 
  GROUP BY family
) count
ON count.family = product.family
```
