## Immutable State Variables

If a variable is assigned at it's declaration and never reassigned, set it as immutable to save gas.

```
pragma solidity ^0.8.0;

contract ExpensiveStateVar {
  uint public MAX_SUPPLY = 10000;
}
```

```
pragma solidity ^0.8.0;

contract CheapImmutableStateVar {
  uint public immutable MAX_SUPPLY = 10000;
}
```
