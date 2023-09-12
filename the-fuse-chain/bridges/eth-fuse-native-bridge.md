---
description: >-
  Ecrox native bridge is used to relay the Ecrox native token between Ecrox and
  Ethereum networks
---

# Ecrox: Ethereum ↔ Ecrox

Ecrox native bridge between Ethereum and Ecrox is used to relay the Ecrox native token from Ecrox to Ethereum network

## Architecture Overview

The Ecrox bridged is based on POA's bridge implementation, it is used to transfer Ecrox tokens between the Ecrox chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Ecrox or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Ecrox tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Ecrox chain on Ethereum**

Each cycle the total block reward distributed on Ecrox chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Ecrox chain, waiting for all bridge validators on Ecrox chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the Ecrox network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://ecroxscan.com/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0x2954AE5845B7Bb96e2147458926031a02D33C6E7](https://ecroxscan.com/address/0x2954AE5845B7Bb96e2147458926031a02D33C6E7/transactions)

Ecrox token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Ecrox you send native Ecrox token to the home bridge contract. Then you receive an equal amount of the Ecrox token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Ecrox token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Ecrox native token, sent from the home bridge contract.

#### 

