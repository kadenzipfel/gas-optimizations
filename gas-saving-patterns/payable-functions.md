## Payable Functions

Functions that are not explicitly marked as payable require an initial check that msg.value == 0, which costs 21 gas. In the case that this check does not provide any benefit, it may be optimal to mark your function as payable.

**Note**: Do not use this pattern unless you understand the security trade-off being made.
