## Function Ordering

When a function is called, the EVM compares the method ID of the transaction to the method ID's present in the contract, with each comparison costing an additional 22 gas. These comparisons are performed in order from least to greatest byte value of method ID's.

For this reason, there is some value in renaming functions to be ordered based on the frequency you expect them to be used, saving average overall gas cost of interacting with your contract.

```
pragma solidity ^0.8.0;

// method ID: 0x1249c58b
mint()

// method ID: 0x0000b696
mint_Aci()
```

Useful tool: https://emn178.github.io/solidity-optimize-name/
