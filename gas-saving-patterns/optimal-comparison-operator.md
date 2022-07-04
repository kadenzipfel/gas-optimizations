## Optimal Comparison Operator

When comparing uints, you can save gas costs by strategically picking the optimal operator.

For example, it is cheaper to use strict < or > operators over <= or >= operators. This is due to the additional EQ opcode which must be performed.

In the case of a conditional statement, it is further optimal to use != when possible.

```
// pragma solidity ^0.8.0;

// 149 gas
function a() external pure returns(bool) {
  return 1 > 0;
}

// 193 gas
function b() external pure returns(bool) {
  return 1 >= 0;
}

// 237 gas
function c() external pure returns(bool) {
  return 1 != 0;
}

// 164 gas
function d() external pure {
  require(1 > 0);
}

// 208 gas
function e() external pure {
  require(1 >= 0);
}

// 120 gas
function f() external pure {
  require(1 != 0);
}
```
