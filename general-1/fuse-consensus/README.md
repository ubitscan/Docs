# Ubit Consensus

Consensus is a fault-tolerant mechanism that is used in blockchain systems to achieve the necessary agreement on the single state of the network. Ubit network is using a [Delegated Proof of Stake](https://en.bitcoinwiki.org/wiki/DPoS) (DPoS) consensus model. DPoS is a variation of [Proof of Stake](https://en.bitcoinwiki.org/wiki/Proof-of-stake) consensus. In PoS there are a set of validators that are responsible for keeping the network updated and validating the network's state. They do this in turns, every validator has their turn in line. On their turn the validator updates the network's state, and the rest of the validators check that the update is valid.

![](<../../.gitbook/assets/image (3).png>)

Consensus contract is used to manage the list of the network validators and delegators

BlockReward contract is calculates the reward amount that validators and delegators will receive on each block validation. The reward size is proportional to validator's stake.

With Voting contract validators are vote on various changes on these 3 base level contracts. All those contracts are proxied with implementation that handles the logic. The implementations can be changed only by the Voting process.&#x20;

The bridge is used to transfer the Ubit native token between Ubit and Ethereum networks.&#x20;

## [Consensus - 0x7eFA0D9149dcAcD0A15F265C0152842b6dBaEDED](https://ubitscan.com/address/0x7eFA0D9149dcAcD0A15F265C0152842b6dBaEDED)

This contract is responsible for handling the network DPos consensus. The contract stores the current validator set and chooses a new validator set at the end of each cycle. The logic for updating the validator set is to select a random snapshot from the snapshots taken during the cycle.

The snapshots are taken of pending validators, who are those which staked more than the minimum stake needed to become a network validator. Therefore the contract is also responsible for staking, delegating and withdrawing those funds.

Stake amount for a validator is the sum of staked and delegated amount to it's address.

This contract is based on `non-reporting ValidatorSet` [described in Parity Wiki](https://wiki.parity.io/Validator-Set.html#non-reporting-contract).

{% hint style="info" %}
minimum stake amount = 10,000 Ubit token

cycle duration blocks = 57600 (approximately 2 days)
{% endhint %}

## [Block Reward - 0x1132A6B3D704D00683112D2eA03862C64940d337](https://ubitscan.com/address/0x1132A6B3D704D00683112D2eA03862C64940d337)

This contract is responsible for generating and distributing block rewards to the network validators according to the network specs (5% yearly inflation).

Another role of this contract is to call the snapshot/cycle logic on the Consensus contract

This contract is based on `BlockReward` [described in Parity Wiki](https://wiki.parity.io/Block-Reward-Contract).

## [Voting - 0xD212f646A2C5ab586038568A9cfE5BD187fDe91D](https://ubitscan.com/address/0xD212f646A2C5ab586038568A9cfE5BD187fDe91D)

This contract is responsible for opening new ballots and voting to accept/reject them. Ballots are basically offers to change other network contracts implementation.

Only network validators can open new ballots, everyone can vote on them, but only validators votes count when the ballot is closed.

Ballots are opened/closed on cycle end.

{% hint style="info" %}
max number of open ballots = 100

max number of open ballots per validator = 100 / number of validators

minimum ballot duration (cycles) = 2

maximum ballot duration (cycles) = 14
{% endhint %}

## [Proxy Storage](https://ubitscan.com/address/0x258aAF236D185119e363b941d232F76bDbe9B61D)

This contract is responsible for holding network contracts implementation addresses and upgrading them if necessary (via voting).

