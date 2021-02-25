# Configurator.sol

This contract is used to assist in the configuring of ElasticDAO contracts. It's primary reason for existing is to decrease the size of [ElasticDAO.sol](https://docs.elasticdao.org/contracts/elasticdao.sol).

## Functionality

### List of Functions

* buildDAO
* buildEcosystem
* buildToken

## Functions

### buildDAO

Creates a [DAO](https://docs.elasticdao.org/contracts/dao.sol).Instance record. Returns `true` when success.

```text
function buildDAO(
  address[] memory _summoners,
  string memory _name,
  uint256 _maxVotingLambda,
  Ecosystem.Instance memory _ecosystem
) external returns (bool) { ... }
```

#### parameters

```text
@param _summoners addresses of the summoners
@param _name name of the DAO
@param _ecosystem instance of Ecosystem the DAO uses
@param _maxVotingLambda - the maximum amount of lambda that can be used to vote in the DAO
```

### buildEcosystem

Deploys proxies leveraging the implementation contracts found on the default [Ecosystem](https://docs.elasticdao.org/contracts/ecosystem.sol).Instance record. Returns the [Ecosystem](https://docs.elasticdao.org/contracts/ecosystem.sol).Instance created when successful.

```text
function buildEcosystem(address _controller, Ecosystem.Instance memory _defaults)
  external
  returns (Ecosystem.Instance memory ecosystem)
{ ... }
```

#### parameters

```text
@param _controller the address which can control the core DAO functions
@param _defaults instance of Ecosystem with the implementation addresses
```

