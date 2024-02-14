# What are Window Functions?

## Postgres Docs Definition

> A window function performs a calculation across a set of table rows that are somehow related to the current row. This
> is comparable to the type of calculation that can be done with an aggregate function. **However, window functions do not
> cause rows to become grouped into a single output row like non-window aggregate calls would. Instead, the rows retain
> their separate identities**.

**What?**

```sql
SELECT family, avg(price)
FROM products
GROUP BY family
```

```
                                                                 ┌─[D&I]─────────────────────────────────────────────────┐
                                                                 │ Deploy & Inventory - Site License | D&I       | 25000 │   ┌──────────────────────────────────────────┐
                                                             ┌──►│ Deploy                            | D&I       |   750 ├──►│                   ....                   │
┌────────────────────────────────────────────────────────┐   │   │ Inventory                         | D&I       |   750 │   └──────────────────────────────────────────┘
│ Deploy & Inventory - Site License | D&I       | 25000  ├───┘   └───────────────────────────────────────────────────────┘
│ Deploy                            | D&I       |   750  │       ┌─[SIMPLEMDM]───────────────────────────────────────────┐   ┌──────────────────────────────────────────┐
│ Inventory                         | D&I       |   750  ├──────►│ Simple MDM - Monthly              | SIMPLEMDM |    50 ├──►│                   ....                   │
│ Simple MDM - Monthly              | SIMPLEMDM |    50  │       │ Simple MDM - Yearly               | SIMPLEMDM |   500 │   └──────────────────────────────────────────┘
│ Simple MDM - Yearly               | SIMPLEMDM |   500  ├───┐   └───────────────────────────────────────────────────────┘
│ Connect - Monthly                 | Connect   |    12  │   │   ┌─[Connect]─────────────────────────────────────────────┐   ┌──────────────────────────────────────────┐
│ Connect - Yearly                  | Connect   |   120  │   └──►│ Connect - Monthly                  | Connect   |   12 ├──►│                   ....                   │
│ Coda                              | Coda      |   100  ├───┐   │ Connect - Yearly                   | Connect   |  120 │   └──────────────────────────────────────────┘
└────────────────────────────────────────────────────────┘   │   └───────────────────────────────────────────────────────┘
                                                             │   ┌─[Coda]────────────────────────────────────────────────┐   ┌──────────────────────────────────────────┐
                                                             └──►│ Coda                               | Coda      | 100  ├──►│                   ....                   │
                                                                 └───────────────────────────────────────────────────────┘   └──────────────────────────────────────────┘
```

## My definition

> Window functions allow you to perform aggregation queries as part of the `SELECT` statement. The records we are
> selecting from are not influenced by the window. Each row maintains its identity.

Using window functions will never in a query gaining or losing additional rows. They are simply a way to add additional
columns to rows that are the result of performing an aggregation.


## Acknowledgements

[This](https://youtu.be/XO1WnmJs9RI) talk is amazing to learn windows. I am also stealing some of his material here to
get through this. Thanks Bruce!
