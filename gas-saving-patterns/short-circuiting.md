## Short Circuiting

Short-circuiting is a strategy we can make use of when an operation makes use of either || or &&. This pattern works by ordering the lower-cost operation first so that the higher-cost operation may be skipped (short-circuited) if the first operation evaluates to true.

```
// f(x) is low cost
// g(y) is expensive

// Ordering should go as follows
f(x) || g(y)
f(x) && g(y)
```
