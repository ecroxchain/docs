---
description: >-
  This is a description of the End-of-Cycle flow that completes the Cycle and
  handles rewards and enforces the consensus
---

# End-of-Cycle Flow

BlockReward.reward is invoked every block, and upon the cycle's completion, it triggers the Consensus.cycle function. Consensus.cycle is responsible for various actions, with two critical tasks being:

1. Setting the boolean Consensus.ShouldEmitInitiateChange to true.
2. Invoking BlockReward.onCycleEnd, which in turn sets the boolean BlockReward.shouldEmitRewardedOnCycle to true.

The Ecrox-validator-app (a component within the Ecrox container on validator virtual machines) monitors the aforementioned booleans. When they are true, the following functions are called in separate transactions (one per function):

1. Consensus.emitInitiateChange
2. BlockReward.emitRewardedOnCycle

It's important to note that only one validator can successfully execute these calls, with others failing. However, since these are zero-gas transactions, the next validator in line to validate a block is usually the successful one.

These function calls emit corresponding events:

1. Consensus.InitiateChange
2. BlockReward.RewardedOnCycle

The bridge oracles ecroxoracle-initiate-change and ecroxoracle-rewarded-on-cycle are designed to listen for these events. These oracles should run on all validators and interact with the HomeBridgeNativeToErc contract on the Ecrox network by calling submitSignature. Each validator should submit a signature for each event.

Once a sufficient number of validators (a majority of the current validators) have submitted their signatures, the home bridge emits an event called CollectedSignatures (one event for each previous event mentioned).

The bridge oracle ecroxoracle-collected-signatures listens for CollectedSignature events, and all validators should receive it. The validator responsible for transmitting the transaction to the mainnet is the last one to submit the signature in section 7. Other validator oracles skip this event because the transmitting responsibility is clearly defined by the event details.

On the mainnet, two transactions should be observed at the ForeignBridgeNativeToErc contract each cycle: one updating the new validators and another minting Ecrox Coins generated during that cycle on the Ecrox Chain.

It's worth noting that if the new validator set transactions fail on the mainnet, there's a risk of the minting transaction failing too. This can occur if new validators submit their signatures promptly on the Ecrox Chain but aren't updated on the mainnet due to failed initial transactions, leading to invalid signatures from the mainnet perspective in the second transaction.

1. Consensus.emitInitiateChange transaction on Ecrox - [https://ecroxscan.com/tx/0x441e2cb5f4aa20948c51020ebd8f7fba7c33cf909e31c66d0aff4a11e79ce13d](https://ecroxscan.com/tx/0x441e2cb5f4aa20948c51020ebd8f7fba7c33cf909e31c66d0aff4a11e79ce13d)
2. BlockReward.emitRewardedOnCycle transaction on Ecrox - [https://ecroxscan.com/tx/0x34cf4ddfc8afa6154e8c0d5f1de3b7d756b1b0517e8f0efd5794bde40983ba64](https://ecroxscan.com/tx/0x34cf4ddfc8afa6154e8c0d5f1de3b7d756b1b0517e8f0efd5794bde40983ba64)
