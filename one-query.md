# The one query to rule them all

```sql
SELECT *, avg(price) OVER (PARTITION BY family)
FROM products
```
