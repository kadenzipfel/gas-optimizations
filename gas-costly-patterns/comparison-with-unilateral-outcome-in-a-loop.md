## Comparison with Unilateral Outcome in a Loop

When a comparison is executed in each iteration of a loop but the result is the same each time, it should be removed from the loop.

```
pragma solidity ^0.8.0;

function unilateralOutcome(uint x) public returns(uint) {
  uint sum = 0;
  for(uint i = 0; i <= 100; i++) {
    if(x > 1) {
      sum += 1;
    }
  }
  return sum;
}
```
