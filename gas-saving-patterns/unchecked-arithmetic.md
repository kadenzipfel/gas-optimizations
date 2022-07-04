## Unchecked Arithmetic

If using solidity >= 0.8.0, safe arithmetic is built-in. In situations that overflow/underflow checks are redundant, code should be wrapped in an unchecked block. For example, the for loop increment can be unchecked as follows:

```
// pragma solidity ^0.8.0;

for (uint i = 0; i < length; i = unchecked_inc(i)) {
    // do something that doesn't change the value of i
}

function unchecked_inc(uint i) returns (uint) {
    unchecked {
        return i + 1;
    }
}
```
