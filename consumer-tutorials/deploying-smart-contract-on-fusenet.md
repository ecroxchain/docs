---
description: Steps on deploying a smart contract on Fusenet through Remix.
---

# Deploying smart contract on Fusenet

Ecrox is an EVM compatible network, every tool for Ethereum can be used for the Ecrox network too.

Remix is a powerful, open source tool that helps you write Solidity contracts straight from the browser. Written in JavaScript, Remix supports both usage in the browser and locally.

Remix also supports testing, debugging and deploying of smart contracts and much more.

 **Pre-requisites:**

Since we interact with remix using Metamask, you need to change the network to Ecrox network by adding a custom RPC. Please follow the steps in [this tutorial](https://docs.ecroxscan.com/the-fuse-studio/getting-started/how-to-add-fuse-to-your-metamask) to do that.

You need to have a small balance of ECROX on the Fusenet wallet you are using which will be used as Gas for the transactions.

 **Step 1:**

Navigate to remix.ethereum.org and you should select the environment as **“Solidity”**.

![](../.gitbook/assets/0%20%288%29.png)

**Step 2:**

Next step is **creating/importing** the contract. You can write the contract using **“Create”** or you can import the contract from various options like Gist, Github, Swarm etc.

In the below example I will be creating a new sample contract.

![](../.gitbook/assets/1%20%2811%29.png)

![](../.gitbook/assets/2%20%2811%29.png)

 **Step 3:**

We will now compile the contract created using the Solidity compiler which you can find on the left hand side. You can choose the version of compiler you want using the drop down.

![](../.gitbook/assets/3%20%2810%29.png)

**Step 4:**

Once compiled you should see a tick mark next to the compiler and we are good to deploy the contract into Fusenet. Please click on **“Deploy and run transaction”** below the compiler option. Select **“Injected Web3”** from the drop down of Environment and adjust the gas value and click on **“Deploy”.** You should confirm the transaction on your Metamask and wait for the transaction to be confirmed on-chain.

![](../.gitbook/assets/4%20%2810%29.png)

 **Step 5:**

Wait for a few seconds and you can see that your smart contract is deployed and you should be able to interact with it.

![](../.gitbook/assets/5%20%287%29.png)

