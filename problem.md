# The Problem


```sql
SELECT * 
FROM products
```

**What is the average price per product family?**

```sql
SELECT name, family, AVG(price)
FROM products
GROUP BY family, name
```

