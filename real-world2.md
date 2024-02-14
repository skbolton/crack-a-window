# Real World - Sales Reps


Given a list of sales transactions calculate the average sales made in a region along with how much a given rep sold in
that region.

Some reps sell in multiple regions so it would also be nice to see global averages and amounts for each rep.

```sql
SELECT *, AVG(amount) OVER by_region as region_average, SUM(amount) OVER by_rep_and_region rep_region_total, AVG(amount)
  OVER all_region global_average, SUM(amount) OVER by_rep rep_total
FROM sales
WINDOW by_region AS (
  PARTITION BY region
  RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
),
by_rep_and_region AS (
  PARTITION BY region
  ORDER BY rep_id
  RANGE BETWEEN CURRENT ROW AND CURRENT ROW
),
all_region AS (),
by_rep AS (
  PARTITION BY rep_id
)
```

