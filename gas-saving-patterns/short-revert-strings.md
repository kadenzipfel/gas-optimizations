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
