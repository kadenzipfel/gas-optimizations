## Expensive Operations in a Loop

Due to the expensive SLOAD and SSTORE opcodes, managing a variable in storage is much more expensive than managing variables in memory. For this reason, storage variables should not be used in loops.

```
pragma solidity ^0.8.0;

uint num = 0;

function expensiveLoop(uint x) public {
  for(uint i = 0; i < x; i++) {
    num += 1;
  }
}
```

The fix for this pattern would be to create a temporary variable to represent the global variable and once the loop is complete, reassign the value of the temporary variable to the global variable.

```
pragma solidity ^0.8.0;

uint num = 0;

function lessExpensiveLoop(uint x) public {
  uint temp = num;
  for(uint i = 0; i < x; i++) {
    temp += 1;
  }
  num = temp;
}
```
