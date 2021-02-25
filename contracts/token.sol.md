# Token.sol

The **Token** contract is used for storing token data.

The **Token** contract inherits the **EternalModel**  contract. The **EternalModel**  contract is an implementation of the [Eternal Storage](https://fravoll.github.io/solidity-patterns/eternal_storage.html) pattern.

The **Token** contract consists of a struct of parameters that can be set while deploying the DAO

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

* uuid - the unique address of the Token
* name - The name of the Token
* symbol - The symbol of the Token
* counter - 
* eByL - During seeding phase, eByL is the value which determines how much shares or lambda\(λ\) a summoner gets. 

