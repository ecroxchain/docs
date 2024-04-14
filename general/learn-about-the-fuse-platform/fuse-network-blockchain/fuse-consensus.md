# Ecrox Consensus

Consensus in blockchain networks involves nodes agreeing on which transactions should be included in the next block before they are permanently added to the chain. This process encompasses both the consensus mechanism for adding transactions to blocks and measures for Sybil protection and incentivizing validators.

**Sybil Protection and Incentives via Delegated Proof of Stake (dPoS)**: Ecrox implements delegated Proof of Stake (dPoS) to safeguard against Sybil attacks and align validator incentives. To participate in network consensus, a node operator must stake a minimum amount of ECROX Coins (currently set at 100,000 ECROX). Validator selection is permissionless, requiring only fulfillment of technical criteria. Staking ECROX prevents an entity from creating multiple validators without significant cost, ensuring Sybil protection. The network currently accommodates up to 5000 validators.

Validators earn rewards in newly minted ECROX Coins and transaction fees for publishing agreed-upon blocks. Their block-publishing frequency corresponds to their stake share, which can be increased through attracting more ECROX Coins from delegators. Violating consensus rules results in stake freezing, including contributions from delegators, incentivizing validators to comply.

**AuRa Consensus Model**: Ecrox utilizes Parity's AuRa (Authority Round) consensus model, also used by the xDAI blockchain, to append blocks. Validators rotate in signing blocks, which are broadcast to all validators for validation. A majority consensus validates a block, adding it to the chain every 5 seconds, regardless of transaction frequency.

While achieving transaction finality theoretically may take time, practically, a transaction on Ecrox is considered finalized after a single block confirmation, ensuring efficient and reliable transaction processing.

\\
