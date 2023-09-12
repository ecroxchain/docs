---
description: >-
  Ecrox <-> BSC ECROX20 bridge is used to relay the ECROX20 tokens between Ecrox and
  Binance Smart Chain networks.
---

# Multi ECROX20: BSC ↔ Ecrox

## Architecture Overview <a id="architecture-overview"></a>

This bridge is two layer bridge. In the base level the Arbitrary Message Bridge \(AMB\) is responsible for relaying messages between the networks. On top of the AMB, the pluggable mediators implement a contract logic of token relaying of various assets. More info [https://docs.tokenbridge.net/amb-bridge/about-amb-bridge](https://docs.tokenbridge.net/amb-bridge/about-amb-bridge).‌

The BSC bridge is a restricted bridge, meaning that only the Ecrox team can add new tokens to the bridge. This is done because the new tokens needs to get associated manually with the tokens on the Ecrox network.‌

## Contracts <a id="contracts"></a>

Home side of the bridge on the Ecrox network: [0x93B477BA32092F5Db932003639DD5d875B2EfC94](https://ecroxscan.com/address/0x93B477BA32092F5Db932003639DD5d875B2EfC94/transactions)​‌

Foreign side of the bridge on the BSC network: [0xc461e59276a2B03B9ebb1289C2c9Cd020677c3A9](https://bscscan.com/address/0xc461e59276a2B03B9ebb1289C2c9Cd020677c3A9)​‌

Home side of the AMB bridge on the Ecrox network: [0x1ee6E3E3d2DE779858728E157B3B9C488bA7b706](https://ecroxscan.com/address/0x1ee6E3E3d2DE779858728E157B3B9C488bA7b706/transactions)​‌

Foreign side of the AMB bridge on the BSC network: [0x3A5A320a2f98a3Fe39c9040e7e3E9caA7F0D5bd6](https://bscscan.com/address/0x3A5A320a2f98a3Fe39c9040e7e3E9caA7F0D5bd6)​‌

## Source Code <a id="source-code"></a>

[https://github.com/fuseio/tokenbridge-contracts](https://github.com/fuseio/tokenbridge-contracts)

## How to use <a id="how-to-use"></a>

Currently only WETH is supported for that bridge, more tokens are coming soon.‌

To send token from the BSC network:‌

1. Approve the ECROX20 tokens to be spent by the Foreign ECROX20 bridge.
2. Call relayTokens function on the bridge contract

The `relayTokens` method will lock the ECROX20 tokens on the foreign bridge. Then an equal amount of the Ecrox ECROX20 token will be sent from the home bridge contract.‌

To send tokens from Ecrox network‌

1. Approve the ECROX20 tokens to be spent by the Home ECROX20 bridge.
2. Call `relayTokens` function on the bridge contract

the `relayTokens` method will lock the bridged tokens on the home bridge. Then, an equal amount of the paired ECROX20 token will be sent from the foreign bridge contract.[PreviousBSC ↔ Ecrox Native](https://app.gitbook.com/@fuse-1/s/fuse-dev-docs/~/drafts/-MdkekktVnuRGEokLu71/bridges/bridges/bsc-fuse-native/@merged)[  
](https://app.gitbook.com/@fuse-1/s/fuse-dev-docs/~/drafts/-MdkekktVnuRGEokLu71/bridges/bridges/eth-fuse-native-bridge/@merged)

