# ElasticGovernanceToken.sol

The amount of ethereum backing each EGT decreases. More EGT are minted and get liquidated for their underlying ethereum value.

## ERC-20

The **ElasticGovernanceToken** contract  is an implementation of our **IElasticToken** interface. The **IElasticToken**  is an implementation of the [ERC20 interface](https://eips.ethereum.org/EIPS/eip-20),  a standard interface for fungible tokens.

Bootstrapped and Community-owned since day1



## The token model

The **Token** contract is used for storing token data.

The **Token** contract inheirits the **EternalModel**  contract. The **EternalModel**  contract is an implementation of the [Eternal Storage](https://fravoll.github.io/solidity-patterns/eternal_storage.html) pattern.

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

$$
eByL = e/λ
$$

{% hint style="info" %}
Eg: If eByL = 0.1, and one of the summoners decides to seed the DAO with 2 eth.

Then  the shares that summoner recieves is given by :

λ = \( 2 \) / \( 0.1 \) = 20. 
{% endhint %}

* elasticity - 

## Functionality



### List of events:

* Approval
* Transfer

### List of functions:

* allowance
* approve
* balanceOf
* balanceOfInShares
* balanceOfAt
* balanceOfInSharesAt
* burn
* burnShares
* decimals
* decreaseAllowance
* increaseAllowance
* mint
* mintShares
* name
* numberOfTokenHolders
* symbol
* totalSupply
* totalSupplyInShares
* transfer
* transferFrom

### List of modifiers:

* onlyDAO



 **if a function refrences another function, event or modifier- link it, have a list of all the functions, events and modifiers and link it\)**

### Events

#### Approval

Emitted when the allowance of a  `_spender` for  `_owner` is set by a call to **approve,**

`_amount` is the new allowance.

```text
event Approval(address indexed _owner, address indexed _spender, uint256 _amount);
```

#### Transfer

Emitted when  `_amount` tokens are moved from the  `_from` account `_to` account

```text
event Transfer(address indexed _from, address indexed _to, uint256 _amount);
```

### 

### Functions

#### allowance

Returns the remaining number of tokens that  `_spender`  will be allowed to spend on behalf of`_owner`through **transferFrom**. This is zero by default.

```text
function allowance(address _owner, address _spender) external override view returns (uint256)
```

#### **approve**

Sets  `_amount` as the allowance of  `_spender` over the caller's tokens.

```text
function approve(address _spender, uint256 _amount) extrenal override returns (bool)
```

#### **balanceOf**

Returns the amount of tokens owned by`_account`.

```text
function balanceOf(address _account) external override view returns (uint256)
```

#### **balanceOfInShares**

Returns the amount of shares owned by`_account`.

```text
function balanceOfInShares(address _account) external override view returns (uint256 lambda)
```

#### **balanceOfAt**

Returns the amount of tokens owned by  `_account` at the specific `_blockNumber`

```text
function balanceOfAt(address _account, uint256 _blockNumber)
```

#### **balanceOfInSharesAt**

Returns the amount of shares owned by  `_account` at `_blockNumber`.

```text
function balanceOfInSharesAt(address _account, uint256 _blockNumber)
```

#### **burn**

Reduces the balance\(tokens\) of  `_account` by  `_amount`

```text
function burn(address _account, uint256 _amount) external override onlyDAO returns (bool)
```

**burnShares**

Reduces the balance\(shares\) of  `_account` by  `_amount`

```text
function burnShares(address _account, uint256 _amount) external override onlyDAO returns (bool)
```

#### **decimals**

Returns the number of decimals the token uses - e.g. `18`, means to divide the token amount by `1000000000000000000` to get its user representation.

```text
function decimals() public view returns (uint256)
```

#### **decreaseAllowance**

Decreases the allowance of `_spender` by  `_subtractedValue`

```text
function decreaseAllowance(address _spender, uint256 _subtractedValue) external returns (bool)
```

#### **increaseAllowance**

Increases the allowance of `_spender` by  `_addedValue`

```text
function increaseAllowance(address _spender, uint256 _addedValue) external returns (bool)
```

\*\*\*\*

#### **mint**

Mints  `_amount` tokens for  \_account.  Note the **onlyDAO** modifier.

```text
function mint(address _account, uint256 _amount) external onlyDAO returns (bool)
```

#### **mintShares**

Mints  `_amount` of shares for  `_account`

```text
function mintShares(address _account, uint256 _amount) external override returns (bool)
```

#### **name**

Returns the name of the token - e.g. `Elastic Governance Token`

```text
function name() public view returns (string memory)
```

#### **numberOfTokenHolders**

Returns the number of token holders currently

```text
function numberOfTokenHolders() external override view returns (uint256)
```

#### **symbol**

Returns the symbol of the token. E.g. `EGT`

```text
function symbol() external view returns (string memory)
```

#### **totalSupply**

Returns the total supply of the tokens in the DAO. Given by the equation:

$$
t = ( λ * m * k )
$$

> * t - the total number of the tokens in the DAO
> * λ \(lambda\) - the total number of shares outstanding in the DAO currently
> * m - current value of the share value modifier
> * k - constant

```text
function totalSupply() external override view returns (uint256)
```

\*\*\*\*

#### **totalSupplyInShares**

Returns the total supply of the shares\( λ \) in the DAO.

```text
function totalSupplyInShares() external override view returns (uint256)
```

####  **transfer**

Moves `_amount` tokens from the caller's account to  `_to` address using the allowance mechanism. `_amount` is then deducted from the caller's allowance. 

Returns a boolean value indicating whether the operation succeeded. Emits a **Transfer** event

```text
function transfer(address _to, uint256 _amount) external override returns (bool)
```

#### **transferFrom**

Moves `_amount` tokens from the `_from` address  to  `_to` address using the allowance mechanism. `_amount` is then deducted from the caller's allowance. 

Returns a boolean value indicating whether the operation succeeded. Emits a **Transfer** and **Approval** event.

```text
function transferFrom(
    address _from,
    address _to,
    uint256 _amount
  ) external override returns (bool)
```

 ****

### **Modifiers**

#### onlyDAO

To ensure only the DAO address can call functions on which this modifer is applied upon.

```text
modifier onlyDAO() {
    require(msg.sender == daoAddress, 'ElasticDAO: Not authorized.');
    _;
  }
```

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

### Shares v Token\(Math\)



### 







