## Function Ordering
When a function is called, the EVM compares the method ID of the transaction to the method ID's present in the contract, with each comparison costing an additional 22 gas. These comparisons are performed in order from least to greatest byte value of method ID's (alphanumerically based on the method ID). This is done using binary search.

For this reason:
### 1. Have method name with IDs that have more 0s.
As with calldata, having a method name whose function selector has more 0s helps.
```
// method ID: 0x6a761202
execTransaction()

// method ID: 0x00000081
execTransaction32785586()
```
This saves 192 bytes of data.

### 2. Reorder methods based on call frequency
there is some value in renaming functions to be ordered based on the frequency you expect them to be used, saving average overall gas cost of interacting with your contract.

```
// method ID: 0x1249c58b
mint()

// method ID: 0x0000b696
mint_Aci()
```

Useful tool: https://emn178.github.io/solidity-optimize-name/
