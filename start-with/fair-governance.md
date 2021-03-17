# Governance

## Fair governance

ElasticDAO's governance approach limits a wallet's maximum influence. All participants have the same opportunities and privileges over the DAO's future, no matter their position, the time of entry, or the value they hold.

ElasticDAO launched fully decentralized and community-owned. The first voting module uses Snapshot to reach consensus while avoiding high gas fees and giving control of the organization to its token holders. This means that any updates regarding the development of the protocol can proceed only with the majority of the token holder's approval. 

Fair governance is achieved in two ways.

1. There is a limited governance power; and
2. a rewarding/penalizing model to encourage participants to vote.

### Voting Mechanism

ElasticDAO is controlled by EGT token holders who submit and vote on proposals to govern the ecosystem. As of today, the voting happens via a module integrated with snapshot, a popular off-chain voting solution. The votes are then ratified by a 9 member multisig.

{% hint style="info" %}
Snapshot has emerged as a popular solution driven by high gas costs. The original ElasticDAO voting modules were entirely on chain, resulting in a roughly $150 cost of casting a vote. A top priority of the core team is to develop additional voting modules on layer 2.
{% endhint %}

### Maximum voting power

There is a maximum number of tokens that someone can vote with. This value is set by the DAO at launch, increases as EGT rebases, and can be adjusted through a voting process should ElasticDAO members choose to adjust it.

{% hint style="info" %}
Example: The current maximum voting power is 1000 EGT.

Mary has 5000 EGT. She can vote with 1000 EGT. As Mary's EGT balance grows due to rewards or direct purchases, she will still be voting with 1000 EGT.

Nicolas has 500 EGT. He can vote with all of his EGT. As his EGT balance grows, he will have more voting power. This increase in voting power will continue until he, like Mary, has 1000 EGT or more. 
{% endhint %}

### Whitelist

Any wallet holding EGT in an amount which meets or exceeds the maximum voting power can create new proposals via the snapshot module. In our example above, Mary would be able to create a proposal, whereas Nicholas would not.

\(Maybe a PHOTO\)

## Process 

### Quorum

Before a proposal can pass, at least 50% of eligible EGT must vote. A proposal which has reached quorum is considered to have passed if 60% or more of the voting EGT votes to approve it. Both of these values are subject to change by proposal.

### Rewards

The individuals who vote, get rewarded regardless of their vote. There are three possible ways to vote your EGT, as a way to increase member participation. In each vote proposal, people can vote to approve a proposal, choose to abstain, or can vote to deny a proposal. A shareholder would choose to abstain because they are agnostic about a proposal or because they lack the in-depth knowledge needed to formulate a position. Rewards are granted regardless of the outcome of a proposal, including in cases where the proposal fails to reach quorum.

The participants get rewarded based on the number of EGT they vote with. The reward variable is set by the DAO and is currently 5%. This is subject to change via proposal. Taken in combination with the maximum voting power, this dynamic helps to increase the relative voting power of smaller EGT holders.

{% hint style="info" %}
Mary, who has 5000 EGT, votes with the maximum voting power of 1000 EGT on proposal 1 and is rewarded with 50 new EGT. Nicholas, who has 500 EGT, votes with his full balance and is rewarded with 25 EGT.

Mary, who now has 5050 EGT, creates and votes on proposal 2 with the maximum voting power of 1000 EGT and is rewarded with 50 EGT. Nicholas, who has 525 EGT, votes and is rewarded with 26.25 EGT.
{% endhint %}

### Penalty

If a proposal doesn't reach quorum, the member who created the proposal can request that multisig signers penalize the people who didn't participate in the previous vote, provided the vote was active for a minimum of 24 hours. The penalty rate is currently 10%.

Unlike rewards, penalties apply to the entire balance of a wallet, ensuring that regardless of the free rider's balance, their voting weight is impacted after any extended absence which has a negative impact on the operation of the DAO.

{% hint style="info" %}
After proposal 1 and 2, Mary has 5100 EGT. She stops paying attention and several proposals pass and fail without her participation. However, on proposal 21, quorum fails. The proposal is put back up as proposal 22 and once again fails. The author of the proposal requests that the multisig penalize non voters. Mary's EGT balance is reduced by 510 EGT. She now has 4590 EGT.
{% endhint %}

The purpose of penalties is not to punish free riders, but to remove them from being a quorum blocker through their inaction. Many existing platforms deal with this by decreasing the quorum requirement, which in turn signals to free riders that it is ok not to vote. ElasticDAO would prefer that the free rider become active again or sell their EGT to someone who will be.

### Multisig

At the creation of the DAO, the summoners also created and funded a multisig, the job of which is to enact the will of the community on chain. The multisig holders are responsible for:

1. Distributing rewards on a weekly basis
2. Executing smart contract calls required to fulfill the will of the community as expressed through passing proposals
3. Penalizing free riders
4. Minting and burning new EGT for the continued operation of the multisig itself

In exchange for their service, multisig members are provided a monthly stipend of EGT to be determined by the DAO. This stipend should be enough to, at a minimum, cover the gas costs of executing the community's will. If a multisig member fails to perform their duties for more than 2 weeks, they may be replaced by the other multisig members with another willing participant from the community.



