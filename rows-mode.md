# ROWS mode

`ROWS` mode makes it so that `CURRENT ROW` can only ever be an individual row.

```sql
SELECT *
FROM generate_series(1, 10) as f(x)
```

```sql
SELECT *, count(*) over w
FROM generate_series(1, 10) as f(x)
WINDOW w AS (
  ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
)
```
