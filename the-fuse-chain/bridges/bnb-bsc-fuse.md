---
description: >-
  BNB inverse-native bridge is used to relay the BNB native token between
  Binance Smart Chain (BSC) and Ecrox networks
---

# BNB: BSC ↔ Ecrox

## Architecture Overview <a id="architecture-overview"></a>

This bridge is two layer bridge. In the base level the Arbitrary Message Bridge \(AMB\) is responsible for relaying messages between the networks. On top of the AMB, the pluggable mediators implement a contract logic of token relaying of various assets. More info [https://docs.tokenbridge.net/amb-bridge/about-amb-bridge](https://docs.tokenbridge.net/amb-bridge/about-amb-bridge)​‌

The contract is called an "inverse-native" bridge, because the home and foreign network are inversed. In that case Ecrox network is foreign and BSC is the home network.‌

## Contracts <a id="contracts"></a>

Home side of the bridge on the BSC network: [0x51849F05090b222FFc329DC8825de0D7e26F84A1](https://bscscan.com/address/0x51849F05090b222FFc329DC8825de0D7e26F84A1)​‌

Foreign side of the bridge on the Ecrox network: [0xA3C59198c10cB1ba9A3Ab924A23253072b393f25](https://ecroxscan.com/address/0xA3C59198c10cB1ba9A3Ab924A23253072b393f25)​‌

BNB token on the Ecrox network: [0x6acb34b1Df86E254b544189Ec32Cf737e2482058](https://ecroxscan.com/address/0x6acb34b1Df86E254b544189Ec32Cf737e2482058/transactions)​‌

Home side of the AMB bridge on the BSC network: [0x3A5A320a2f98a3Fe39c9040e7e3E9caA7F0D5bd6](https://bscscan.com/address/0x3A5A320a2f98a3Fe39c9040e7e3E9caA7F0D5bd6)​‌

Foreign side of the AMB bridge on the Ecrox network: [0x1ee6E3E3d2DE779858728E157B3B9C488bA7b706](https://ecroxscan.com/address/0x1ee6E3E3d2DE779858728E157B3B9C488bA7b706)​‌

## Source Code <a id="source-code"></a>

‌​[https://github.com/fuseio/tokenbridge-contracts](https://github.com/fuseio/tokenbridge-contracts)​‌

## How to use <a id="how-to-use"></a>

To send token from the BSC network:‌

Send native BNB token to the home bridge contract. Then you receive an equal amount of the BNB token on the Ecrox network, sent from the foreign bridge contract.‌

To send token from the Ecrox network:‌

1. Approve the "BNB on Ecrox" ECROX20 token to be spent by the Foreign bridge.
2. Call relayTokens function on the bridge contract

the `relayTokens` method will lock the ECROX20 tokens on the foreign bridge. After a couple of confirmations, an equal amount of the BNB native token will be released from the home bridge contract on BSC.

#### ​ <a id="undefined"></a>

[  
](https://app.gitbook.com/@fuse-1/s/fuse-dev-docs/~/drafts/-MdkekktVnuRGEokLu71/bridges/bridges/eth-fuse-erc20-bridge/@merged)

