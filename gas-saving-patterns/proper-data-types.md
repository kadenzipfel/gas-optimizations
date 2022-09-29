## Proper Data Types

In Solidity, some data types are more expensive than others. It’s valuable to know the most efficient type that can be used. Here are a few rules about data types.

- Type uint or bytes32 should be used in place of type string whenever possible.
- Type uint256 takes less gas to store than other uint types ([see why](https://ethereum.stackexchange.com/questions/3067/why-does-uint8-cost-more-gas-than-uint256)).
- Type bytes should be used over byte[].
- If the length of bytes can be limited, use the lowest amount possible from bytes1 to bytes32.
