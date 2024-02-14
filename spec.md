# Window Functions

So what do they look like?

```sql
SELECT *, avg(price) over () --<= Window definition goes here
FROM products
```

You can also define it in the body of the query to keep the select statement clean.

```sql
SELECT *, avg(price) over my_window
FROM products
WINDOW my_window AS ()
```

You can also use several windows in a query. All aggregating and grouping data differently.
```sql
SELECT *, avg(price) over my_window, sum(price) over my_other_window
FROM products
WINDOW my_window AS (), my_other_window AS ()
```

## Full Spec

```sql
WINDOW (
  [PARTITION BY ...]
  [ORDER BY ...]
  [
    { RANGE | ROWS }
    { frame_start | BETWEEN frame_start AND frame_end }
  ]
) [AS ...]
```
