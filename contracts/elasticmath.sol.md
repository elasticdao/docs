# ElasticMath.sol

## Math of ElasticDAO

Provides functions for performing ElasticDAO specific math.

## Functionality

### List of functions:

* capitalDelta
* deltaE
* lambdaFromT
* mDash
* revamp
* t
* wmul
* wdiv



## Functions

### capitalDelta

Calculates the value of capitalDelta, the amount of ETH backing each governance token.

```text
function capitalDelta(uint256 totalEthValue, uint256 totalSupplyOfTokens)
    internal
    pure
    returns (uint256)
  {...}
```

#### parameters

```text
@param totalEthValue amount of ETH in the DAO contract
@param totalSupplyOfTokens number of tokens in existance
```

### deltaE

Calculates the value of deltaE, the amount of ETH required to mint deltaLambda.

```text
function deltaE(
    uint256 deltaLambda,
    uint256 capitalDeltaValue,
    uint256 k,
    uint256 elasticity,
    uint256 lambda,
    uint256 m
  ) internal pure returns (uint256) {...}
```

#### parameters

```text
@param deltaLambda = lambdaDash - lambda
@param capitalDeltaValue the ETH/token ratio; see capitalDelta(uint256, uint256)
@param k constant token multiplier - it increases the number of tokens that each member of the DAO has with respect to their lambda
@param elasticity the percentage by which capitalDelta (cost of entering the  DAO) should increase on every join
@param lambda outstanding shares
@param m - lambda modifier - it's value increases every time someone joins the DAO
```

### lambdaFromT

Calculates the lambda value given t, k, & m.

```text
function lambdaFromT(
    uint256 tokens,
    uint256 k,
    uint256 m
  ) internal pure returns (uint256) {...}
```

#### parameters

```text
@param tokens t value; number of tokens for which lambda should be calculated
@param k constant token multiplier - it increases the number of tokens that each member of the DAO has with respect to their lambda
@param m - lambda modifier - it's value increases every time someone joins the DAO
```

### mDash

Calculates the future share modifier given the future value of lambda \(lambdaDash\), the current value of lambda, and the current share modifier.

```text
function mDash(
    uint256 lambdaDash,
    uint256 lambda,
    uint256 m
  ) internal pure returns (uint256) {...}
```

#### parameters

```text
 @param m current share modifier
 @param lambda current outstanding shares
 @param lambdaDash future outstanding shares
```

### revamp

Calculates the value of revamp \(revamp = 1 + elasticity\).

```text
function revamp(uint256 elasticity) internal pure returns (uint256) {...}
```

#### parameters

```text
@param elasticity the percentage by which capitalDelta should increase
```

### t

Calculates the number of tokens represented by lambda given k & m.

```text
function t(
    uint256 lambda,
    uint256 k,
    uint256 m
  ) internal pure returns (uint256) {...}
```

#### parameters

```text
@param lambda shares
@param k a constant, initially set by the DAO
@param m share modifier
```

### wmul

Multiplies two float values, required since solidity does not handle floating-point values.

```text
function wmul(uint256 a, uint256 b) internal pure returns (uint256) {...}
```

### wdiv

Divides two float values, required since solidity does not handle floating-point values.

```text
function wdiv(uint256 a, uint256 b) internal pure returns (uint256) {...}
```

