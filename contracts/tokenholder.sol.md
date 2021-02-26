# TokenHolder.sol

## A data storage for Token holders

The ****tokenHolder ****contract is used for storing an array of token holders in the DAO.

The tokenHolder ****contract inherits the **EternalModel**  contract. The **EternalModel**  contract is an implementation of the [Eternal Storage](https://fravoll.github.io/solidity-patterns/eternal_storage.html) pattern.

The tokenHolder contract consists of a struct of parameters that can be set while deploying the DAO.

```bash
struct Instance {
    address account;
    uint256 lambda;
    Ecosystem.Instance ecosystem;
    Token.Instance token;
  }
```

* account - an account of the token holder
* lambda - the total number of shares outstanding in the DAO currently
* ecosystem - the DAO ecosystem
* token - token of the DAO

## Functionality

### List of events:

* [Serialized](https://app.gitbook.com/@elasticdao/s/docs/~/drafts/-MUUNkCuPjp2572zw0OD/contracts/tokenholder.sol#serialize)

### List of functions:

* [deserialize](https://app.gitbook.com/@elasticdao/s/docs/~/drafts/-MUUNkCuPjp2572zw0OD/contracts/tokenholder.sol#deserialize)
* [exists](https://app.gitbook.com/@elasticdao/s/docs/~/drafts/-MUUNkCuPjp2572zw0OD/contracts/tokenholder.sol#exists)
* [serialize](https://app.gitbook.com/@elasticdao/s/docs/~/drafts/-MUUNkCuPjp2572zw0OD/contracts/tokenholder.sol#serialize)
* [\_exists](https://app.gitbook.com/@elasticdao/s/docs/~/drafts/-MUUNkCuPjp2572zw0OD/contracts/tokenholder.sol#_exists)

## Events

### Serialize

```text
  event Serialized(address indexed account, address indexed token);
```

## Functions

### deserialize

Translates the data from the key-value pairs to a struct

```text
function deserialize(address _account, Ecosystem.Instance memory _ecosystem, Token.Instance memory _token) external view returns (Instance memory record) {...}
```

### exists

Checks if the address already exists in the DAO \(externally\)

```text
function exists(address _account, Token.Instance memory _token) external view returns (bool) {...}
```

### serialize

Translates the data from the concerned struct to key-value pairs

```text
function serialize(Instance memory _record) external preventReentry {...}
```

### \_exists

Checks if the address already exists in the DAO \(internally\)

```text
function _exists(address _account, Token.Instance memory _token) internal view returns (bool) {...}
```

