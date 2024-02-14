# Partition By

Create a hard separation in rows so that they are aggregated seperately

```sql
SELECT *, count(*) OVER w
FROM products
WINDOW w as (
  PARTITION BY family
  RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
)
```

```
 id |               name                |  family   | price | count 
----+-----------------------------------+-----------+-------+-------
  8 | Coda                              | Coda      |   100 |     1
--------------------------------------------------------------------
  7 | Connect - Yearly                  | Connect   |   120 |     2
  6 | Connect - Monthly                 | Connect   |    12 |     2
--------------------------------------------------------------------
  1 | Deploy & Inventory - Site License | D&I       | 25000 |     3
  2 | Deploy                            | D&I       |   750 |     3
  3 | Inventory                         | D&I       |   750 |     3
--------------------------------------------------------------------
  5 | Simple MDM - Yearly               | SIMPLEMDM |   500 |     2
  4 | Simple MDM - Monthly              | SIMPLEMDM |    50 |     2
```

## The query to remember!

If there is one query to remember from this talk it is this. This is the one that will get you to experiment more with
Window Functions!

This is what I use 90% instead of `GROUP BY` queries.

```sql
SELECT *, AVG(price) OVER (PARTITION BY family)
FROM products
```

