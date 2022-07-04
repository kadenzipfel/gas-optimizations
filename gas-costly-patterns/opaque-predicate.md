## Opaque Predicate

The outcome of some conditions can be known without being executed and thus do not need to be evaluated.

```
pragma solidity ^0.8.0;

function opaquePredicate(uint x) public pure {
  if(x > 1) {
    // redundant
    if(x > 0) {
      return x;
    }
  }
}
```
