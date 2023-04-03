## Loop Fusion

Occasionally in smart contracts, you may find that there are two loops with the same parameters. In the case that the loop parameters are the same, they should be combined if possible.

```
 function loopFusion(uint x, uint y) public pure returns(uint) {
  for(uint i = 0; i < 100; i++) {
    x += 1;
  }
  for(uint i = 0; i < 100; i++) {
    y += 1;
  }
  return x + y;
}
```

Should be re-written as:

```
 function lessExpensiveLoopFusion(uint x, uint y) public pure returns(uint) {
  for(uint i = 0; i < 100; i++) {
    x += 1;
    y += 1;
  }
  return x + y;
}
```
