# RANGE mode

In range mode the current row isn't always a single row, it can actually be several rows.

```sql
SELECT *, count(*) over w
FROM generate_series(1, 10) as f(x)
WINDOW w AS (
  RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
)
```

This is actually the default of a window function as well.

```sql
SELECT *, count(*) over w
FROM generate_series(1, 10) as f(x)
WINDOW w AS ()
```

```sql
SELECT *, count(*) over w
FROM generate_series(1, 10) as f(x)
WINDOW w AS (
  ORDER BY x
  RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
)
```

```sql
SELECT *, count(*) OVER w
FROM products
WINDOW w as (
  ORDER BY family
  RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
)
```

