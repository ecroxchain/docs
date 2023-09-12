---
description: >-
  Steps to transfer/wrap ECROX20 tokens from Ethereum to Fusenet and back using
  smart contracts.
---

# Using the bridge with ECROX20 tokens directly through the contract

**Please use this tutorial at your own risk as it involves using Etherscan UI/Ecrox explorer to relay the tokens. This tutorial is applicable only for ECROX20 tokens other than ECROX. Do not use this tutorial to transfer ECROX.** 

We are going to have a UI soon so it would be good to wait for the bridge UI too.

Below are the important contract addresses: 

Ethereum Mediator: **0xf301d525da003e874DF574BCdd309a6BF0535bb6**

Fusenet Mediator : **0xc2220646E1E76D5fF3a441eDd9E8EFF0e4A8EF03**

In the below example we will consider USDT \(ECROX20\) and learn how to wrap USDT to Fusenet and relay it back to ECROX20.

**Step 1:** **Approving the USDT token contract**

This step basically is to approve your wallet to interact with the USDT token contract so that you can spend your tokens on Bridge contract.

Please go to USDT token contract on Etherscan via link below.

[https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7\#writeContract](https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7#writeContract) ![](../../.gitbook/assets/0%20%283%29.png)

![](../../.gitbook/assets/1%20%286%29.png)

Click on **“Connect to Web3”** and sign in to your wallet through Metamask.

**Step 2:** Go to **“approve”** and enter the details below to allow for the for the bridge mediator contract to move the funds

* spender \(address\) field: the mediator contract address on Ethereum \(0xf301d525da003e874DF574BCdd309a6BF0535bb6\)
* spender \(uint256\): the amount of tokens to transfer in wei \(Number of decimals should be 6\)

Click on **“Write”** and approve the transaction on your Metamask wallet and wait for the confirmation on-chain.

![](../../.gitbook/assets/2%20%286%29.png)

**Step 3:**

Navigate to mediator contract using the link below

[https://etherscan.io/address/0xf301d525da003e874df574bcdd309a6bf0535bb6\#code](https://etherscan.io/address/0xf301d525da003e874df574bcdd309a6bf0535bb6#code)

Click on **“Write as Proxy”** and then on **“Connect to Web3”.** Sign in through your Metamask wallet.

Enter the below details on **“Relay tokens”** and click on **“Write”**

* token \(address\) field: the USDT token contract address on Ethereum \(0xdac17f958d2ee523a2206206994597c13d831ec7\)
* \_value \(uint256\): the amount of tokens to transfer in wei \(Number of decimals should be 6\)

![](../../.gitbook/assets/3%20%285%29.png)

Once the transaction is confirmed on-chain we wait for 2 blocks to ensure security of transaction and then the USDT tokens should appear on your Ecrox address and have been swapped from Ethereum mainnet to Fusenet.

Now let’s learn how to transfer the wrapped ECROX20 tokens on Fusenet back to Ethereum mainnet.

**Step 1:** Approving the wrapped USDT token contract on Fusenet. 

This step basically is to approve your wallet to interact with the USDT token contract on Fusenet so that you can transfer the tokens to the Mediator contract.

Please go to token contract on Fusenet explorer via link below.

https://ecroxscan.com/address/0xFaDbBF8Ce7D5b7041bE672561bbA99f79c532e10/write\_proxy

![](../../.gitbook/assets/4%20%286%29.png)

Make sure that the network is ECROX network. If you have not added Ecrox network please follow the instructions [here](https://docs.ecroxscan.com/the-fuse-studio/getting-started/how-to-add-fuse-to-your-metamask).

Click on **“Connect to Metamask”** and sign in to your wallet through Metamask.

 **Step 2:** Go to **“approve”** and enter the details below

* spender \(address\) field: the mediator contract address on Fusenet \(0xc2220646E1E76D5fF3a441eDd9E8EFF0e4A8EF03\)
* spender \(uint256\): the amount of tokens to transfer in wei \(Number of decimals should be 18\)

Click on **“Write”** and approve the transaction on your Metamask wallet and wait for the confirmation on-chain.

![](../../.gitbook/assets/5%20%284%29.png)

**Step 3:**

Navigate to Migrator contract on Fusenet using the link below

[https://ecroxscan.com/address/0xc2220646E1E76D5fF3a441eDd9E8EFF0e4A8EF03/write\_proxy](https://ecroxscan.com/address/0xc2220646E1E76D5fF3a441eDd9E8EFF0e4A8EF03/write_proxy)

Click on **“Write as Proxy”** and then on **“Connect to Metamask”** \(If you have connected Metamask previously no need to connect again\). Sign in through your Metamask wallet.

Enter the below details on **“Relay tokens”** and click on **“Write”**

* token \(address\) field: the USDT token contract address on Fusenet \(0xFaDbBF8Ce7D5b7041bE672561bbA99f79c532e10\)
* \_value \(uint256\): the amount of tokens to transfer in wei \(Number of decimals should be 6\)

![](../../.gitbook/assets/6%20%285%29.png)

After the transaction is confirmed on Ecrox network, the bridge oracle will relay your tx on Ethereum. No need to wait for additional confirmations as Ecrox is PoS network. After sometime you should be able to see the successful transfer of the token on your ECROX20 address.

Note: Please do enter the decimals very carefully. If the decimals are entered incorrectly then the transaction might fail with an error or might cost you very high gas.

