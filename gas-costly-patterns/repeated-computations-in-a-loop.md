## Repeated Computations in a Loop

If an expression in a loop produces the same outcome in each iteration, it can be moved out of the loop. This is especially important when the variables(s) used in the expression are stored in storage.

```
uint a = 4;
uint b = 5;
function repeatedComputations(uint x) public returns(uint) {
  uint sum = 0;
  for(uint i = 0; i <= x; i++) {
    sum = a + b;
  }
  return sum;
}
```
