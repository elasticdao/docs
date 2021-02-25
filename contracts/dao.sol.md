# DAO.sol

The DAO contract is used to store the core data of the ElasticDAO. it inherits the **EternalModel**  contract. The **EternalModel**  contract is an implementation of the [Eternal Storage](https://fravoll.github.io/solidity-patterns/eternal_storage.html) pattern.

```text
struct Instance {
    address uuid;
    address[] summoners;
    bool summoned;
    string name;
    uint256 maxVotingLambda;
    uint256 numberOfSummoners;
    Ecosystem.Instance ecosystem;
  }
```

* uuid - is an address of the unique user ID
* summoners - stores an array of addresses of the summoners
* summoned - checks if summoned or not
* name - is a name of the unique user ID
* maxVotingLambda - is the maximum amount of lambda that can be used to vote in the DAO
* numberOfSummoners - is the number of summoners
* ecosystem - is the DAO ecosystem

## Functionality



### List of events:

* Serialized

### List of functions:

* deserialize
* exists
* getSummoner
* isSummoner
* serialize
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
function exists(address _uuid, Ecosystem.Instance memory) external view returns (bool) {...}
```

### getSummoner

Checks the index number of the summoner

```text
function getSummoner(Instance memory _dao, uint256 _index) external view returns (address) {...}
```

### isSummoner

Checks if the msg.sender is a summoner

```text
function isSummoner(Instance memory _dao, address _summonerAddress) external view returns (bool) {...}
```

### serialize

Translates the data from the concerned struct to key-value pairs

```text
function serialize(Instance memory _record) external preventReentry {...}
```

### \_exists

Checks if the address already exists in the DAO \(internally\)

```text
function _exists(address _uuid) internal view returns (bool) {...}
```

