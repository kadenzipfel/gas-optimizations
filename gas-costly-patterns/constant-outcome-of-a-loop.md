## Constant Outcome of a Loop

If the outcome of a loop is a constant that can be inferred during compilation, it should not be used.

```
function constantOutcome() public pure returns(uint) {
  uint num = 0;
  for(uint i = 0; i < 100; i++) {
    num += 1;
  }
  return num;
}
```
