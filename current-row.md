# Current Row

The hardest concept with windows is the concept of the "CURRENT ROW".

It's a contextual value that can change based on the context it is used.

> Javascript devs know the pain of the `this` keyword

Think of the "CURRENT ROW" as an anchor point

```
┌────────────────────────────────────────────────────────┐
│ Deploy & Inventory - Site License | D&I       | 25000  │ <-- What value do I put here?
│ Deploy                            | D&I       |   750  │   <-- and here?
│ Inventory                         | D&I       |   750  │     <-- and here?  
│ Simple MDM - Monthly              | SIMPLEMDM |    50  │
│ Simple MDM - Yearly               | SIMPLEMDM |   500  │
│ Connect - Monthly                 | Connect   |    12  │
│ Connect - Yearly                  | Connect   |   120  │
│ Coda                              | Coda      |   100  │
└────────────────────────────────────────────────────────┘
```

