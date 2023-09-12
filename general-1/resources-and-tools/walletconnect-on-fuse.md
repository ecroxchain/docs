# WalletConnect on Ecrox

[WalletConnect](https://walletconnect.com) is an **open-source protocol for data exchange between wallets and decentralized applications (dApps)**. The process takes place via a specialized server and the flow of data is encrypted in both directions.

From the user’s perspective, although the exact details may vary from wallet to wallet, there are two ways of using WalletConnect. In the mobile-to-mobile mode, the user opens the website of the dApp that they are interested in, clicks the “connect wallet” tab there and chooses their preferred wallet. The desktop-to-mobile approach involves using the Wallet Connect-enabled wallet on the mobile phone to scan the QR code of the dApp displayed in the desktop browser. After the session, the dApp may be disconnected, and users are even advised to disconnect dApps for security reasons.

For developers who wish to integrate the WalletConnect functionality into their dApps running on Ecrox, we recommend using [this library](https://www.npmjs.com/package/@fuseio/walletconnect-web3-provider).
