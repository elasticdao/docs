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

## Modifiers

### onlyAfterSummoning

If the DAO has not yet been summoned, reverts the transaction with the message `ElasticDAO: DAO must be summoned`.

### onlyAfterTokenInitialized

Checks to make sure that an ElasticGovernanceToken has been created and initialized. If not, the transaction is reverted with the message `ElasticDAO: Please call initializeToken first`.

### onlyBeforeSummoning

If the DAO has been summoned, reverts the transaction with the message `ElasticDAO: DAO must not be summoned`.

### onlyController

Ensures that `msg.sender` is the controller address. If not, reverts the with the message `ElasticDAO: Only controller`.

### onlyDeployer

Ensures that `msg.sender` is the same address which called `initialize`. If not, the transaction is reverted with the message `ElasticDAO: Only deployer`.

### onlySummoners

Ensures that `msg.sender` is one of the summoner addresses passed when `initialize` was called. If not, reverts with the message `ElasticDAO: Only summoners`.

### onlyWhenOpen

Ensures that the DAO has some balance of ETH in it's vault. If not, reverts with the message `ElasticDAO: This DAO is closed`.

## Functions

### initialize

Initializes and builds the ElasticDAO struct by passing and initializing all the required parameters into the [Configurator](https://docs.elasticdao.org/contracts/elasticdao.sol/configurator.sol) contract.

#### parameters

```text
* @param _ecosystemModelAddress - the address of the ecosystem model
* @param _controller the address which can control the core DAO functions
* @param _summoners - an array containing the addresses of the summoners
* @param _name - the name of the DAO
* @param _maxVotingLambda - the maximum amount of lambda that can be used to vote in the DAO
```

#### requirements

* The DAO cannot already be initialized
* The ecosystem model address cannot be the zero address
* The DAO must have atleast one summoner to summon the DAO
* The configurator should be able to successfully build the DAO

