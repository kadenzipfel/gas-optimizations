## Dead Code

Dead code is code that will never run because it’s evaluation is predicated on a condition that will always return false.

```
function deadCode(uint x) public pure {
  if(x < 1) {
    if(x > 2) {
      // this will never run
      return x;
    }
  }
}
```
