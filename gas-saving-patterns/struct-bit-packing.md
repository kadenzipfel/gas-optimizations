## Struct Bit Packing

Solidity's [storage layout](https://docs.soliditylang.org/en/v0.8.15/internals/layout_in_storage.html?highlight=storage%20layout) consists of 2\*\*256 32 byte slots, with reads and writes requiring a fixed cost per slot. As such, to reduce gas costs, we should aim to use as few slots as necessary.

When variables are stored, they are done so in a compact way such that multiple values sometimes use the same slot. Structs may contain multiple data types, of which will also be stored as compact as the data types allow. For example, the following struct will consume 3 slots:

```
struct ThreeSlots {
    uint256 firstSlot; // takes an entire slot because uint256 is 256 bits == 32 bytes
    uint256 secondSlot; // takes an entire slot because uint256 is 256 bits == 32 bytes
    address thirdSlot; // although addresses are 20 bytes, it will take the third slot since the first two are full
}
```

If however, we know for a fact our uints will have a low enough upper bound, we can reduce the size to pack variables into fewer slots. For example:

```
struct OneSlot {
    uint48 firstValue; // if the value will never exceed 2**48 we can do this to use just 48 bits == 6 bytes
    uint48 secondValue; // if the value will never exceed 2**48 we can do this to use just 48 bits == 6 bytes
    address thirdValue; // since we've only consumed 12 bytes we can fit our 20 byte address for a total of 32 bytes
}
```
