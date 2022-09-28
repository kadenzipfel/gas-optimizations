## Optimal Increment and Decrement Operators

Increment and decrement operators are used to either increment or decrement their operand by one. These incrementers/decrementers can either be presented as e.g. `i++` or `++i`, with the only difference being the order of operations being executed. `i++` will return `i`, then increment the value of `i`, whereas `++i` will increment before returning the value.

As a result of the variance in order of operations, `++i` will save two opcodes from being performed. Consider the following example:

```
pragma solidity ^0.8.0;

contract IPlusPlus {
    // 1996 gas
    function loop() external pure {
        for (uint256 i; i < 10; i++) {
            // do something
        }
    }
}

contract PlusPlusI {
    // 1946 gas
    function loop() external pure {
        for (uint256 i; i < 10; ++i) {
            // do something
        }
    }
}
```

Using `++i` above shaves off 5 gas per loop. This is because `i++` must handle the value of `i` both before and after the increment, in this case by executing a `DUPN` opcode (3 gas) and later cleaning up the stack by performing a `POP` (2 gas).
