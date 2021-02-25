# ElasticDAO.sol

The ElasticDAO contract outlines and defines all of the core functionality for an Elastic DAO. It also serves as the DAO's vault.

## Functionality

### List of Events

* [ControllerChanged](https://docs.elasticdao.org/contracts/elasticdao.sol#controllerchanged)
* [ElasticGovernanceTokenDeployed](https://docs.elasticdao.org/contracts/elasticdao.sol#elasticgovernancetokendeployed)
* [ExitDAO](https://docs.elasticdao.org/contracts/elasticdao.sol#exitdao)
* [JoinDAO](https://docs.elasticdao.org/contracts/elasticdao.sol#joindao)
* [MaxVotingLambdaChanged](https://docs.elasticdao.org/contracts/elasticdao.sol#maxvotinglambdachanged)
* [SeedDAO](https://docs.elasticdao.org/contracts/elasticdao.sol#seeddao)
* [SummonedDAO](https://docs.elasticdao.org/contracts/elasticdao.sol#summoneddao)

### List of Modifiers

* [onlyAfterSummoning](https://docs.elasticdao.org/contracts/elasticdao.sol#onlyaftersummoning)
* [onlyAfterTokenInitialized](https://docs.elasticdao.org/contracts/elasticdao.sol#onlyaftertokeninitialized)
* [onlyBeforeSummoning](https://docs.elasticdao.org/contracts/elasticdao.sol#onlybeforesummoning)
* [onlyController](https://docs.elasticdao.org/contracts/elasticdao.sol#onlycontroller)
* [onlyDeployer](https://docs.elasticdao.org/contracts/elasticdao.sol#onlydeployer)
* [onlySummoners](https://docs.elasticdao.org/contracts/elasticdao.sol#onlysummoners)
* [onlyWhenOpen](https://docs.elasticdao.org/contracts/elasticdao.sol#onlywhenopen)

### List of Functions

* [initialize](https://docs.elasticdao.org/contracts/elasticdao.sol#initialize)
* [initializeToken](https://docs.elasticdao.org/contracts/elasticdao.sol#initializetoken)
* [exit](https://docs.elasticdao.org/contracts/elasticdao.sol#exit)
* [join](https://docs.elasticdao.org/contracts/elasticdao.sol#join)
* [penalize](https://docs.elasticdao.org/contracts/elasticdao.sol#penalize)
* [reward](https://docs.elasticdao.org/contracts/elasticdao.sol#reward)
* [setController](https://docs.elasticdao.org/contracts/elasticdao.sol#setcontroller)
* [setMaxVotingLambda](https://docs.elasticdao.org/contracts/elasticdao.sol#setmaxvotinglambda)
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

### MaxVotingLambdaChanged

Emitted after a successful call to `setMaxVotingLambda`.

```text
event MaxVotingLambdaChanged(address indexed daoAddress, bytes32 settingName, uint256 value);event MaxVotingLambdaChanged(address indexed daoAddress, bytes32 settingName, uint256 value);
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

```text
function initialize(
  address _ecosystemModelAddress,
  address _controller,
  address[] memory _summoners,
  string memory _name,
  uint256 _maxVotingLambda
) external preventReentry { ... }
```

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

### initializeToken

Initializes the DAO's [ElasticGovernanceToken](https://docs.elasticdao.org/contracts/elasticgovernancetoken.sol), using the [Configurator](https://docs.elasticdao.org/contracts/elasticdao.sol/configurator.sol) contract.

Emits the [ElasticGovernanceTokenDeployed](https://docs.elasticdao.org/contracts/elasticdao.sol#elasticgovernancetokendeployed) event.

```text
function initializeToken(
  string memory _name,
  string memory _symbol,
  uint256 _eByL,
  uint256 _elasticity,
  uint256 _k,
  uint256 _maxLambdaPurchase
) external onlyBeforeSummoning onlyDeployer preventReentry { ... }
```

#### parameters

```text
@param _name - name of the token
@param _symbol - symbol of the token
@param _eByL -the amount of lambda a summoner gets(per ETH) during the seeding phase of the DAO
@param _elasticity the value by which the cost of entering the  DAO increases ( on every join )
@param _k - is the constant token multiplier
  it increases the number of tokens that each member of the DAO has with respect to their lambda
@param _maxLambdaPurchase - is the maximum amount of lambda that can be purchased per wallet
```

#### requirements

* Only the deployer of the DAO can initialize the Token

### exit

Allows a member to exit for their underlying ETH. The amount of EGT burned is expressed in it's lambda form as `_deltaLambda`.

```text
function exit(uint256 _deltaLambda) external onlyAfterSummoning preventReentry { ... }
```

#### formula

$$
ΔΛ / Λ * Ε
$$

#### parameters

```text
@param _deltaLambda - the amount of lambda the address exits with
```

#### requirements

* ETH transfer must be successful

### join

Allows a prospective or current member to join the DAO by minting lambda with ETH. An exact amount of ETH is necessary to successfully mint. Documentation and further math regarding `capitalDelta`, `deltaE`, and `mDash` can be found at [ElasticMath.sol](https://docs.elasticdao.org/contracts/elasticmath.sol).

Emits the [JoinDAO](https://docs.elasticdao.org/contracts/elasticdao.sol#joindao) event.

```text
function join(uint256 _deltaLambda)
  external
  payable
  onlyAfterSummoning
  onlyWhenOpen
  preventReentry
{ ... }
```

#### parameters

```text
@param _deltaLambda - the amount of lambda minted to the address
```

#### requirements

* The amount of shares being purchased has to be lower than [maxLambdaPurchase](https://docs.elasticdao.org/contracts/elasticdao.sol#parameters)
* The correct value of ETH, calculated via deltaE\(link\), must be sent with the transaction
* The token contract should be successfully be able to mint  `_deltaLambda`

### penalize

Penalizes `_addresses` with `_amounts` respectively.

```text
function penalize(address[] memory _addresses, uint256[] memory _amounts)
  external
  onlyController
  preventReentry
{ ... }
```

#### parameters

```text
@param _addresses - an array of addresses
@param _amounts - an array containing the amounts each address has to be penalized respectively
```

#### requirements

* Each address must have a corresponding amount to be penalized with.

### reward

Rewards `_addresses` with `_amounts` respectively.

```text
function reward(address[] memory _addresses, uint256[] memory _amounts)
  external
  onlyController
  preventReentry
{ ... }
```

#### parameters

```text
@param _addresses - an array of addresses
@param _amounts - an array containing the amounts each address has to be rewarded respectively
```

#### requirements

* Each address must have a corresponding amount to be rewarded with.

### setController

Sets the controller of the DAO. The controller of the DAO handles various responsibilities of the DAO, such as burning and minting tokens on behalf of the DAO.

Emits the [ControllerChanged](https://docs.elasticdao.org/contracts/elasticdao.sol#controllerchanged) event.

```text
function setController(address _controller) external onlyController preventReentry { ... }
```

#### parameters

```text
@param _controller - the new address of the controller of the DAO
```

#### requirements

* The controller must not be the 0 address
* The controller of the DAO should successfully be set as the burner of the tokens of the DAO
* The controller of the DAO should successfully be set as the minter of the tokens of the DAO

### setMaxVotingLambda

Sets the maxVotingLambda value for the DAO, which determines the maximum voting capability of a single wallet.

Emits the [MaxVotingLambdaChanged](https://docs.elasticdao.org/contracts/elasticdao.sol#maxvotinglambdachanged) event.

```text
function setMaxVotingLambda(uint256 _maxVotingLambda) external onlyController preventReentry { ... }
```

#### parameters

```text
@param _maxVotingLambda - the value of the maximum amount of lambda that can be used for voting
```

