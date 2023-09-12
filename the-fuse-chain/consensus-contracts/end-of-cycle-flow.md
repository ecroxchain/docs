---
description: >-
  This is a description of the End-of-Cycle flow that completes the Cycle and
  handles rewards and enforces the consensus
---

# End-of-Cycle flow

1. BlockReward.reward is called every block and when the cycle ends calls the Consensus.cycle
2. Consensus.cycle is responsible for several functions. Eventually does the following two actions:
   1. Sets the boolean Consensus.ShouldEmitInitiateChange to true
   2. Calls BlockReward.onCycleEnd which sets the boolean BlockReward.shouldEmitRewardedOnCycle to true as well
3. The fuse-validator-app \(fuseapp container on validator vms\) checks the value of the above two booleans and when true calls the following two functions \(two separate transactions\):
   1. Consensus.emitInitiateChange
   2. BlockReward.emitRewardedOnCycle

Note that only one validator can make this call successfully so the 1st one succeeds and all others fail. But it’s ok because those are 0-gas transactions. So actually the validator who is the next one to validate a block is the one who is successful in making those calls.

1. The above calls emit the following events:
   1. Consensus.InitiateChange
   2. BlockReward.RewardedOnCycle
2. The bridge oracles fuseoracle-initiate-change and fuseoracle-rewarded-on-cycle are responsible for listening to above events.
3. Those oracles should run on all validators and call submitSignature on the HomeBridgeNativeToErc contract in fuse network - each validator should submit the signature for each of the oracles \(events\).
4. Once enough validators have submitted their signatures \(majority of the current validators\), an event CollectedSignatures is emitted by the home bridge \(again one event for each one of the previous events in section 4\).
5. The bridge oracle fuseoracle-collected-sigantures is responsible for listening to the CollectedSignature events and all validators should get it. The validator responsible for transmitting the transaction to mainnet is actually the last one to submit the signature in section 7 and its address is part of the event details so other validator oracles “know” it’s not their turn and skip the event. If a validator is down or out of money or infura is deaf - the next one in line \(in the ValidatorSet\) is responsible for transmitting to mainnet.
6. Eventually on mainnet we are supposed to see two transactions to the ForeignBridgeNativeToErc each cycle - one updating the new validators and one minting the fuse tokens which were created during this cycle on fuse.

Note that if the new validator set transactions fail on mainnet there’s a chance the minting will fails as well, because before transmitting it checks if all signatures are valid and there can be a situation where new validators were added on a cycle and were fast enough to submit their signatures on fuse end-of-cycle transactions but weren’t updated on mainnet due to failure of the 1st transactions so the 2nd one will actually contain “invalid” signatures from the mainnet perspective.  
  


Example for a successful flow \(from 7/6/2020\)

1. Consensus.emitInitiateChange transaction on fuse - [https://ecroxscan.com/tx/0x441e2cb5f4aa20948c51020ebd8f7fba7c33cf909e31c66d0aff4a11e79ce13d](https://ecroxscan.com/tx/0x441e2cb5f4aa20948c51020ebd8f7fba7c33cf909e31c66d0aff4a11e79ce13d)
2. BlockReward.emitRewardedOnCycle transaction on fuse - [https://ecroxscan.com/tx/0x34cf4ddfc8afa6154e8c0d5f1de3b7d756b1b0517e8f0efd5794bde40983ba64](https://ecroxscan.com/tx/0x34cf4ddfc8afa6154e8c0d5f1de3b7d756b1b0517e8f0efd5794bde40983ba64)
3. Successful validators update transaction on mainnet - [https://etherscan.io/tx/0xf43b2abebd64537dbd7d834c9ac7a42ce8a925da5cb5278002ce0687187c8882](https://etherscan.io/tx/0xf43b2abebd64537dbd7d834c9ac7a42ce8a925da5cb5278002ce0687187c8882)
4. Successful fuse minting transaction on mainnet - [https://etherscan.io/tx/0x2bd70ecbff6e84c18306701eb380e558a7340fab61aadf1af7690021aeeef5ce](https://etherscan.io/tx/0x2bd70ecbff6e84c18306701eb380e558a7340fab61aadf1af7690021aeeef5ce)

  


