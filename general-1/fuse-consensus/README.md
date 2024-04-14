# Ecrox Consensus

Consensus plays a crucial role in blockchain systems by ensuring agreement on the network's single state. In the Ecrox network, we utilize a Delegated Proof of Stake (DPoS) consensus model, a variant of the Proof of Stake (PoS) mechanism. Here's a brief overview:

1. **Proof of Stake (PoS)**: In PoS, a group of validators is responsible for maintaining and validating the network's state. Validators take turns updating the state, with each validator having its designated slot in the rotation. When it's their turn, a validator updates the network's state, and other validators verify the update for validity.
2. **Delegated Proof of Stake (DPoS)**: DPoS introduces a delegation system where token holders can delegate their tokens to specific validators. These elected validators then perform the network validation tasks. DPoS aims to enhance scalability and efficiency by reducing the number of validators actively participating in the consensus process.

In the Ecrox network, DPoS ensures fault tolerance and efficient agreement on the network's state, contributing to the overall reliability and performance of the blockchain ecosystem.

<figure><img src="../../.gitbook/assets/spaces_4lx06BJBDdtE98Mhq7B8_uploads_git-blob-cd5bcb498a760ab32bce9d7d90c6c68a529a7029_image (3).png" alt=""><figcaption></figcaption></figure>

The Consensus contract plays a crucial role in managing the network's validators and delegators, maintaining an updated list of participants actively involved in securing the network.

The BlockReward contract is responsible for calculating the rewards distributed to validators and delegators during block validation. These rewards are proportionate to the validator's stake, incentivizing active participation and contribution to network security.

The Voting contract facilitates decision-making within the network, allowing validators to vote on proposed changes related to the Consensus, BlockReward, and other fundamental contracts. These contracts are proxied with implementations that handle their logic, ensuring transparency and security. Any changes to these implementations can only be made through the formal Voting process, ensuring democratic governance and consensus.

Additionally, the bridge serves as a vital link between the Ecrox and Ethereum networks, enabling seamless transfer of the native Ecrox token between the two platforms. This interoperability enhances accessibility and liquidity, fostering a connected and vibrant blockchain ecosystem.

## [Consensus - 0x2954AE5845B7Bb96e2147458926031a02D33C6E7](https://ecroxscan.com/address/0x2954AE5845B7Bb96e2147458926031a02D33C6E7)

This contract plays a crucial role in managing the network's Delegated Proof of Stake (DPoS) consensus mechanism. Its primary functions include storing the current set of validators and selecting a new validator set at the end of each cycle. The selection process for updating the validator set involves choosing a random snapshot from the snapshots captured during the cycle.

Furthermore, the contract is responsible for handling various actions related to staking, delegating, and withdrawing funds for validators. Here's a breakdown of its responsibilities:

1. **Validator Set Management**: The contract stores information about the current validators who participate in securing the network through staking and validating transactions.
2. **Cycle Updates**: At the end of each cycle, the contract updates the validator set by selecting a random snapshot from the snapshots taken during the cycle. This ensures a fair and decentralized process for validator selection.
3. **Snapshot Creation**: The contract captures snapshots of pending validators during the cycle. Pending validators are those who have staked an amount exceeding the minimum stake required to become a network validator.
4. **Staking**: Validators and delegators can stake their funds through this contract. The stake amount for a validator includes both the amount staked directly and the amount delegated to its address.
5. **Delegating**: Delegators can delegate their funds to validators of their choice. This allows for broader participation in the consensus mechanism and rewards distribution.
6. **Withdrawing Funds**: Validators and delegators can withdraw their staked or delegated funds when needed. This functionality ensures liquidity and flexibility for participants in the network.

Overall, this contract serves as a pivotal component in maintaining the integrity, decentralization, and efficiency of the network's DPoS consensus mechanism while facilitating stake management and delegation processes.

This contract is based on `non-reporting ValidatorSet` [described in Parity Wiki](https://wiki.parity.io/Validator-Set.html#non-reporting-contract).

{% hint style="info" %}
minimum stake amount = 100,000 Ecrox Coin

cycle duration blocks = 57600 (approximately 2 days)
{% endhint %}

## [Block Reward - 0x0dc0E5f77e75E54E4C18B438E6c867D11ea3cAD6](https://ecroxscan.com/address/0x0dc0E5f77e75E54E4C18B438E6c867D11ea3cAD6)

This contract is responsible for generating and distributing block rewards to the network validators according to the network specs (5% yearly inflation).

Another role of this contract is to call the snapshot/cycle logic on the Consensus contract

This contract is based on `BlockReward` [described in Parity Wiki](https://wiki.parity.io/Block-Reward-Contract).

## [Voting - 0x74942BD53217F7C59C2cC4e077DF4698a86E10eB](https://ecroxscan.com/address/0x74942BD53217F7C59C2cC4e077DF4698a86E10eB)

This contract is responsible for opening new ballots and voting to accept/reject them. Ballots are basically offers to change other network contracts implementation.

Only network validators can open new ballots, everyone can vote on them, but only validators votes count when the ballot is closed.

Ballots are opened/closed on cycle end.

{% hint style="info" %}
max number of open ballots = 5000

max number of open ballots per validator = 5000 / number of validators

minimum ballot duration (cycles) = 2

maximum ballot duration (cycles) = 14
{% endhint %}

## [Proxy Storage](https://ecroxscan.com/address/0x9b66D237552d25Bc7942eF67832663dc264c926B)

This contract is responsible for holding network contracts implementation addresses and upgrading them if necessary (via voting).
