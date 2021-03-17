# An Elastic DAO

### The protocol

The Elastic DAO Protocol is a governance protocol focused on fairness. The protocol was created by a team of DeFi natives, is 100% bootstrapped, and community-owned since day one. It combines different features:

* A bonding curve 
* Rebasing
* Fair governance

At its core, Elastic DAO is an elastic governance protocol that expands supply in response to the market demand and activity. The protocol focuses on allowing DAOs deployed on it to reward active participation and penalize bad actors.

The Elastic DAO Protocol model is based on two rules:

1. When an Elastic DAO is in high demand, the value and the token price will increase. All current participants end up with more tokens via positive rebasing, and each token is worth more.
2. When work is happening inside the DAO, the value backing each token decreases.

{% hint style="info" %}
The first DAO deployed on the Elastic DAO Protocol, is named ElasticDAO. ElasticDAO exists to ensure the further development of the protocol. For the sake of eliminating confusion, the remainder of this documentation will talk about interacting with a single DAO, ElasticDAO. Everything discussed applies to any DAO deployed via the Elastic DAO Protocol.
{% endhint %}

### Entering the DAO 

Every time the join function of ElasticDAO is called, the amount of ETH backing each of its governance token \(**EGT**\) increases. All members end up with more value. The total supply flourishes and is distributed to the token holders in the form of a proportional increase in number of **tokens** \(rebase\) and a rise in the price of the token.

{% hint style="info" %}
Mary enters ElasticDAO via the join function \(link\). The amount of EGT held by each community member increases, and the amount of ETH each EGT can be redeemed for increases by 3% \(the **elasticity** value \(link\)\).
{% endhint %}

Check out the steps to join ElasticDAO \(link\).

It is also possible to buy EGT on a Sushiswap AMM. Anyone who does so does not trigger a rebase, but has entered ElasticDAO as a member. Rebasing happens only when new tokens are minted via the join function.

### Work inside the DAO

ElasticDAO uses its treasury to continue developing the Elastic DAO Protocol and related tools \(the platform\). Every time there is activity inside the DAO, people get rewarded for their work by the shared treasury. This decreases the backing value of each EGT, making it cheaper for new members to enter ElasticDAO. New entrants expand the number of participants in the DAO, thereby making the ecosystem more decentralized. Overall, good decisions made regarding the future of the protocol will have the effect of increasing the vault's total value.

Elasticity comes from the market driven balance between the volume of work performed and the perceived future value of the protocol. During the early periods, while work is happening inside the DAO, it's easier for new members to join. Later, once the majority of the work has been completed and new DAOs are forming, entering becomes more expensive. This creates a natural equilibrium between decentralization and price speculation.

{% hint style="info" %}
If Maria works in a marketing campaign to promote ElasticDAO, the DAO will reward Maria for her work by minting new EGT. She cashes those new tokens in for their underlying value or sells them on the open market. The value backing each existing EGT decreases, creating an opportunity for Nicolas to enter the DAO at a lower price.
{% endhint %}

### Exit the DAO

When people exit the DAO, they receive the amount of ETH backing each EGT burned. Burning EGT to redeem their value in ETH does not have a fee associated with it and can be done at any time. The value of the treasury and the total number of EGT outstanding decreases proportionally and is not associated with a negative rebase.

Furthermore,  token holders have the option to sell their tokens on the Sushiswap AMM. 

{% hint style="info" %}
Maria wants to exit the DAO. She calls the exit function \(link\) and specifies how many EGT she would like to burn \(as a lambda value \(link to maths\)\). Her EGT is burned and the vault sends her its corresponding value in ETH.

Nicolas, who took his opportunity to enter after the previous example, has not seen any change in his EGT balance or value.
{% endhint %}

