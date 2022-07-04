## Short Revert Strings

Keeping revert strings under 32-bytes prevents the string from being stored in more than one memory slot.

```
function expensiveRevertStrings() {
  require(a < b; "long revert string over 32 bytes");
}
```

Alternatively you can write comments to map short strings to longer ones in your contract, e.g.:

```
// a: long revert string over 32 bytes
function cheapRevertStrings() {
  require(a < b; "a");
}
```

Ideally, if you are using solidity >= 0.8.4, it is even better to use custom errors to further save on gas.

```
// pragma solidity ^0.8.0;

error CustomError();
contract CustomErrors {
  if (a < b) {
    revert CustomError();
  }
}
```
