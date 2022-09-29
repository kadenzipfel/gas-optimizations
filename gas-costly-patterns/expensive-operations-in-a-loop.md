## Expensive Operations in a Loop

We should aim to keep logic in loops as cheap as possible.

For example, due to the expensive SLOAD and SSTORE opcodes, managing a variable in storage is much more expensive than managing variables in memory. For this reason, storage variables should be avoided in loops.

```
uint num = 0;

function expensiveLoop(uint x) public {
  for(uint i = 0; i < x; i++) {
    num += 1;
  }
}
```

The fix for this pattern would be to create a memory variable to represent the state variable and once the loop is complete, reassign the value of the temporary variable to the global variable.

```
uint num = 0;

function lessExpensiveLoop(uint x) public {
  uint temp = num;
  for(uint i = 0; i < x; i++) {
    temp += 1;
  }
  num = temp;
}
```
