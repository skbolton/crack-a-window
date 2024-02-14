# Real World - Transaction & Balances

We have a ledger of transactions and we want to show how each transaction affected the accounts balance.

```sql
SELECT *
FROM transactions
```

```sql
SELECT *, SUM(amount) OVER w
FROM transactions
WINDOW w AS (
  PARTITION BY account_id
  ORDER BY created_at
  ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
)
```
