# Token.sol

## A data storage for EGT \(Elastic Governance Token\)

The **Token** contract is used for storing token data.

The Token contract is used for storing token data, it inherits the **EternalModel**  contract. The **EternalModel**  contract is an implementation of the [Eternal Storage](https://fravoll.github.io/solidity-patterns/eternal_storage.html) pattern.

The **Token** contract inherits the **EternalModel**  contract. The **EternalModel**  contract is an implementation of the [Eternal Storage](https://fravoll.github.io/solidity-patterns/eternal_storage.html) pattern.

```text
struct Instance {
    address uuid;
    string name;
    string symbol;
    uint256 eByL;
    uint256 elasticity;
    uint256 k;
    uint256 lambda;
    uint256 m;
    uint256 maxLambdaPurchase;
    uint256 numberOfTokenHolders;
    Ecosystem.Instance ecosystem;
  }
```

The **Token** contract consists of a struct of parameters that can be set while deploying the DAO

* uuid - is an address of the unique user ID
* name - is the name of the token
* symbol - is the symbol of the token
* eByL - During the seeding phase, eByL is the value which determines how much shares or lambda\(λ\) a summoner gets.
* elasticity - is the value by which the cost of entering the DAO increases \( on every join \)
* k - is the constant token multiplier, it increases the number of tokens that each member of the DAO has with respect to their lambda
* lambda - is the total number of shares outstanding in the DAO currently
* m - is a lambda modifier it's value increases every time someone joins the DAO
* maxLambdaPurchase - is the maximum amount of lambda that can be purchased per wallet
* numberOfTokenHolders - is an index indicating the number of token holders
* ecosystem - is the DAO ecosystem

```text
struct Instance {
    address uuid;
    string name;
    string symbol; 
    uint256 eByL;
    uint256 elasticity;
    uint256 k;
    uint256 lambda;
    uint256 m;
    uint256 maxLambdaPurchase;
    uint256 numberOfTokenHolders;
    Ecosystem.Instance ecosystem;
  }
```

## Functionality

* uuid - the unique address of the Token
* name - The name of the Token
* symbol - The symbol of the Token
* counter - 
* eByL - During seeding phase, eByL is the value which determines how much shares or lambda\(λ\) a summoner gets. 



### List of events:

* Serialized

### List of functions:

* deserialize
* exists
* serialize
* updateNumberOfTokenHolders
* \_exists

### Functions

### deserialize

Translates the data from the key-value pairs to a struct

```text
function deserialize(address _uuid, Ecosystem.Instance memory _ecosystem) external view returns (Instance memory record) {...}
```

### exists

Checks if the address already exists in the DAO \(externally\)

```text
function exists(address _uuid, Ecosystem.Instance memory) external view returns (bool)
```

### serialize

Translates the data from the concerned struct to key-value pairs

```text
function serialize(Instance memory _record) external preventReentry {...}
```

### UpdateNumberOfTokenHolders

Updates the number of token holders

```text
function updateNumberOfTokenHolders(Instance memory _record, uint256 numberOfTokenHolders)
```

### \_exists

Checks if the address already exists in the DAO \(internally\)

```text
function _exists(address _uuid) internal view returns (bool) {...}
```

