## Using Mulmod Over Mul & Div

If you have to check whether a value obtained by dividing it by a number is exact(i.e. significant digits have not truncated during division), use `mulmod` instead of mul & div as it costs 8 gas. In contrast, `mul` and `div` cost 5 gas each.

- Gas inefficient method
```
    contract UsingMul&Div {
        error InExactDivision();

        function exactDivide(
            uint256 numerator,
            uint256 denominator,
            uint256 value
        ) public pure returns (uint256 newValue) {
            newValue = (value * numerator)/denominator;
            if(value != (newValue * denominator)/ numerator) {
                revert InExactDivision();
            }
        }
    }

```

- Gas efficient method

```
    contract UsingMulMod {
        error InExactDivision();

        function exactDivide(
            uint256 numerator,
            uint256 denominator,
            uint256 value
        ) public pure returns (uint256 newValue) {
            newValue = (value * numerator)/denominator;
            if(mulmod(value, numerator, denominator) != 0) {
                revert InExactDivision();
            }
        }
    }

```

- Gas efficient method(With Assembly)

```
    contract UsingMulModWithAssembly {
        error InExactDivision();

        function exactDivide(
            uint256 numerator,
            uint256 denominator,
            uint256 value
        ) public pure returns (uint256 newValue) {
            bool inexact;
            assembly {
                newValue := div(mul(value, numerator, denominator));
                inexact := iszero(iszero(mulmod(value, numerator, denominator)));
            }
            if(inexact) {
                revert InExactDivision();
            }
        }
    }

```