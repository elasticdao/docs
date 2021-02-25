# Ecosystem.sol

## The ecosystem for ElasticDAO

The ecosystem contract is used for storing core DAO data, it inherits the **EternalModel**  contract. The **EternalModel**  contract is an implementation of the [Eternal Storage](https://fravoll.github.io/solidity-patterns/eternal_storage.html) pattern. ElasticDAO network can read and/or write from this contract.

```text
struct Instance {
   address daoAddress;
   address daoModelAddress;
   address ecosystemModelAddress;
   address tokenHolderModelAddress;
   address tokenModelAddress;
   address configuratorAddress;
   address governanceTokenAddress;
 }
```

* daoAddress - is an address of unique user ID
* daoModelAddress - 
* ecosystemModelAddress - is an address of the ecosystem model
* tokenHolderModelAddress - is an address of the token holder
* tokenModelAddress - is an address of a token
* configuratorAddress - is an address of the DAO configurator
* governanceTokenAddress - is an address of the governance token

## Functionality

### List of events:

* Serialized

### List of functions:

* deserialize
* exists
* serialize
* \_exists

## Functions

### deserialize

Translates the data from the key-value pairs to a struct

```text
function deserialize(address _daoAddress) external view returns (Instance memory record) {...}
```

#### parameters

```text
@param _daoAddress - address of the unique user ID
```

### exists

Checks if the address already exists in the DAO \(externally\)

```text
function exists(address _daoAddress) external view returns (bool recordExists) {...}
```

#### parameters

```text
@param _daoAddress - address of the unique user ID
```

### serialize

Translates the data from the concerned struct to key-value pairs

```text
function serialize(Instance memory _record) external preventReentry {...}
```

#### parameters

```text
@param _record Instance
```

### \_exists

Checks if the address already exists in the DAO \(internally\)

```text
function _exists(address _daoAddress) internal view returns (bool recordExists) {...}
```

