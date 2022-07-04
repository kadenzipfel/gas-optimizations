## Storage Variable as Loop Length

Avoid using storage variables to set the length of a for loop.

```
pragma solidity ^0.8.0;

function expensiveLoopLength {
  for (uint i = 0; i < array.length; i++) {}
}
```

Instead assign it to a variable in memory to avoid unnecessary SLOADs.

```
pragma solidity ^0.8.0;

function cheapLoopLength {
  uint length = array.length;
  for (uint i = 0; i < length; i++) {}
}
```
