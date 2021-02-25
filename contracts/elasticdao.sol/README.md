# ElasticDAO.sol

The ElasticDAO contract outlines and defines all of the core functionality for an Elastic DAO. It also serves as the DAO's vault.

## Functionality

### List of Events

* ControllerChanged
* ElasticGovernanceTokenDeployed
* ExitDAO
* JoinDAO
* MaxVotingLambdaChanged
* SeedDAO
* SummonedDAO

### List of Modifiers

* onlyAfterSummoning
* onlyAfterTokenInitialized
* onlyBeforeSummoning
* onlyController
* onlyDeployer
* onlySummoners
* onlyWhenOpen

### List of Functions

* initialize
* initializeToken
* exit
* join
* penalize
* reward
* setController
* setMaxVotingLambda
* seedSummoning
* summon
* getDAO
* getEcosystem

## Events

### ControllerChanged

Emitted after a successful call to `setController`. 

```text
event ControllerChanged(address indexed daoAddress, bytes32 settingName, address value);
```

### ElasticGovernanceTokenDeployed

Emitted after a successful call to `initializeToken`.

```text
  event ElasticGovernanceTokenDeployed(address indexed tokenAddress);
```

### ExitDAO

Emitted after a successful call to `exit`.

```text
event ExitDAO(
  address indexed daoAddress,
  address indexed memberAddress,
  uint256 shareAmount,
  uint256 ethAmount
);
```

### JoinDAO

Emitted after a successful call to `join`.

```text
event JoinDAO(
  address indexed daoAddress,
  address indexed memberAddress,
  uint256 shareAmount,
  uint256 ethAmount
);
```

### SeedDAO

Emitted after a successful call to `seedSummoning`.

```text
event SeedDAO(address indexed daoAddress, address indexed summonerAddress, uint256 amount);
```

### SummonedDAO

Emitted after a successful call to `summon`.

```text
event SummonedDAO(address indexed daoAddress, address indexed summonedBy);
```



