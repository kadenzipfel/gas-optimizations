## Constants and Immutables

If a storage variable must be assigned at deployment and doesn't need to be reassigned, it should be marked as immutable.
Better yet, if it doesn't need to be assigned at deployment then it can be set as a constant.

```
contract ExpensiveStorageVar {
    uint256 MAX_SUPPLY = 10000;

    // 520 gas
    function getMaxSupply() external view returns (uint256) {
        return MAX_SUPPLY;
    }
}
```

```
// pragma solidity ^0.8.0;

contract CheapImmutable {
    uint256 immutable maxSupply;

    constructor(uint256 _maxSupply) {
        maxSupply = _maxSupply;
    }

    // 379 gas
    function getMaxSupply() external view returns (uint256) {
        return maxSupply;
    }
}
```

```
// pragma solidity ^0.8.0;

contract ExtraCheapConstant {
    uint256 constant MAX_SUPPLY = 10000;

    // 320 gas
    function getMaxSupply() external pure returns (uint256) {
        return MAX_SUPPLY;
    }
}
```
