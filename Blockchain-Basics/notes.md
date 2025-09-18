## 1. History and Evolution

**Web 1.0:**

Static, read-only web. Information only consumed, not edited. HTML pages, limited interactivity, basic hyperlinks.

**Web 2.0:**

Read-write web, user-generated content (social media, blogs, comments). Centralized platforms control data, more collaboration and interactivity.

**Web 3.0:**

In Web3, applications run on decentralized networks, empowering users to control their online identity, assets, and interactions without relying on intermediaries. Data is not centralized; users own, move, and monetize it individually. Web3 also features native digital assets (cryptocurrencies, NFTs), smart contracts for automated logic, and advanced privacy controls.

---

**Blockchain: Historical Timeline**

- 1982: David Chaum outlines a blockchain-like protocol for trusted transactions.
- 1991–92: Stuart Haber & W. Scott Stornetta invent secure timestamping with cryptographic chains; Merkle trees added for efficiency.
- 2008: Satoshi Nakamoto publishes the Bitcoin whitepaper, solving the "double-spending" problem with proof of work and peer-to-peer consensus.
- 2009: Bitcoin launches—first true decentralized blockchain network.

**Bitcoin & Satoshi's Whitepaper**

Goal: Peer-to-peer digital cash, removing intermediaries ("A Peer-to-Peer Electronic Cash System").

Tech: Blockchain ledger, proof-of-work consensus, immutable records, capped supply (21 million BTC).

Original papers:

- [Bitcoin Whitepaper PDF](https://bitcoin.org/bitcoin.pdf)
- [Alternate Bitcoin Whitepaper access](https://bitcoin.org/en/bitcoin-paper)

---

**Ethereum & Its Whitepaper**

Proposed by: Vitalik Buterin (2013), launched 2015.

Innovation: Decentralized computing (smart contracts, dApps), Turing-complete virtual machine, programmable trust.

Currency: ETH (Ether), fuels network "gas" for transactions and computations.

Original papers:

- [Ethereum Whitepaper](https://ethereum.org/whitepaper/)
- [Ethereum Whitepaper library](https://whitepaper.io/document/5/ethereum-whitepaper)

Common Terms :

1. **Blockchain**: In web3, a blockchain is a digital ledger that records transactions across many computers in a secure and decentralized manner. Each block contains a number of transactions, and every new block is linked to the previous one, forming a chain. This makes the data tamper-resistant. *Example*: Bitcoin's blockchain records all BTC transactions.
2. **Oracle**: Oracles in web3 are intermediaries that provide smart contracts with external data. They act as bridges between blockchains and the outside world, allowing smart contracts to execute based on real-world events and data. *Example*: A weather oracle provides data for a smart contract that triggers crop insurance payments based on rainfall data.
3. **Layer 2**: Layer 2 solutions in web3 are technologies built on top of a blockchain (Layer 1) to improve its scalability and efficiency. These solutions handle transactions off the main chain, reducing congestion and fees, and then settle the final state on the main chain. *Example*: The Lightning Network for Bitcoin.
4. **Dapp (Decentralized Application)**: A Dapp is an application that runs on a decentralized network, typically a blockchain. It is powered by smart contracts and operates without a central authority. Dapps can serve various purposes, from finance to gaming. *Example*: Uniswap, a decentralized finance application.
5. **Smart Contract**: In web3, a smart contract is a self-executing contract with the terms of the agreement directly written into code. They run on blockchains and automatically execute when predetermined conditions are met, without the need for intermediaries. *Example*: A smart contract for an escrow service.
6. **Hybrid Smart Contract**: Hybrid smart contracts combine on-chain code (running on a blockchain) with off-chain data and computations provided by oracles. This allows the contracts to interact with data and systems outside their native blockchain. *Example*: A smart contract for insurance that uses real-world data (like weather or flight delays) provided by oracles.
7. **Ethereum/EVM (Ethereum Virtual Machine)**: Ethereum is a blockchain platform known for its smart contract functionality. The Ethereum Virtual Machine (EVM) is its computation engine that executes smart contracts. Ethereum allows developers to build decentralized applications and is the basis for many web3 projects. *Example*: ERC-20 tokens, a standard for creating fungible tokens on Ethereum.


## 2. Smart Contracts

**Definition:**

Smart contracts are self-executing computer programs on a blockchain that automatically enforce and execute the terms of an agreement when predefined conditions are met, without the need for intermediaries. They follow simple "if/when...then" logic embedded in code.

**Key Features:**

- Automation: Executes actions automatically when conditions are satisfied.
- Transparency: Contract code and outcomes are visible and immutable on the blockchain.
- Security: Tamper-proof and irreversible transactions.
- Programmability: Supports complex conditional logic.
- Trustless: No need to trust a middleman or counterparty.

**Use Cases:**

Decentralized finance (loans, payments, exchanges), supply chain management, insurance claims automation, legal contracts and escrow services, digital identity and voting systems, NFT minting and gaming logic.

**Platforms:**

Ethereum, Solana, Polkadot, Avalanche, Hyperledger Fabric (enterprise), Binance Smart Chain, Cardano, Tezos.


## 3. Block-chain Fundamentals

**Cryptographic Hash Functions:**

- **Keccak-256 (Ethereum):** Part of SHA-3 family with sponge construction. More secure and flexible than SHA-256, supports variable outputs. Used for Ethereum addresses, transactions, and smart contract data.
- **SHA-256 (Bitcoin):** Merkle-Damgård structure, fixed 256-bit output. Widely adopted, used in Bitcoin mining and transaction verification.

**Block Structure:**

Each block contains:

- Block header with previous block hash (creating the chain)
- Nonce (number used once) - random number miners adjust to find valid hash
- Transaction data (merkle tree of all transactions)
- Timestamp and difficulty target
- Current block hash

**Genesis Block:**

- First block in any blockchain (Block 0 or Block 1)
- No reference to previous block - hardcoded into blockchain software
- Contains special messages (Bitcoin's: "The Times 03/Jan/2009 Chancellor on brink of second bailout for banks")
- Establishes foundation for entire blockchain

**Blockchain Immutability:**

Chain of blocks linked by cryptographic hashes. Changing one block requires recalculating all subsequent blocks, making tampering computationally infeasible across distributed network.

**Peer-to-Peer Network:**

Distributed nodes maintain copies of blockchain, validate transactions, and reach consensus without central authority.

**Mining and Node Rewards:**

- **Mining:** Process of solving cryptographic puzzles to create new blocks
- **Block Rewards:** Miners receive newly minted cryptocurrency + transaction fees for successfully mining blocks
- **Current Bitcoin reward:** 3.125 BTC (halved every ~4 years)
- **Purpose:** Incentivizes network security and transaction validation

**Node Types:**

- Full nodes: Store complete blockchain, validate all transactions
- Mining nodes: Compete to create new blocks and earn rewards
- Light nodes: Store partial blockchain data for efficiency

DIY blockchain on https://andersbrownworth.com/blockchain/blockchain


## 4. Public and Private Keys

- In blockchain, each wallet/address is secured by a cryptographic key pair: a public key and a private key.

**Secret Phrase (Seed/Recovery Phrase):**

- A seed phrase (usually 12 or 24 random English words) is a human-readable backup for a crypto wallet.
- The secret phrase is generated when you create a wallet. It’s the "master password"—all private keys for that wallet are derived from this phrase.
- If you lose your device, you can restore the entire wallet and all associated private keys/addresses using the seed phrase.
- **Keep it extremely secure and offline—anyone with this phrase can access all your wallet contents.**

**Private Key:**

- A unique string (usually 64 hexadecimal characters) that gives control over a specific blockchain address.
- Used to securely sign transactions and prove ownership of coins or tokens.
- Derived from the seed phrase. Each wallet may manage many private keys using one seed.
- Must be kept private; if lost, access is lost permanently. If leaked, funds can be stolen.

**Public Address:**

- Public-facing identifier, derived from the public key (which itself is derived from the private key).
- Used to receive funds—safe to share.
- Anyone can send crypto to this address, but only the holder of the matching private key (ultimately linked to your seed phrase) can spend or move those funds.

**Relationship Flow :**

- **Seed Phrase ⇒ generates ⇒ Private Key(s) ⇒ derives ⇒ Public Address(es)**

**How They Work Together :**

- A transaction is signed using the private key to prove ownership, without revealing the key itself.
- The network and participants use the corresponding public key to verify the digital signature, ensuring the sender is authentic.
- If the signature is valid, the transaction is accepted into the blockchain. Ownership of funds is always tied to control of the private key.


## 5. Signatures

A digital signature is a cryptographic technique used to verify the authenticity and integrity of digital messages or transactions on a blockchain. It ensures that the message was created by the owner of the private key and that it has not been altered since signing.

**How Digital Signature Works (Signing Process):**

1. **Hashing the Data:**
    
    The transaction or message is processed by a hash function (e.g., SHA-256) to generate a unique fixed-length digital fingerprint (hash). Even a slight change in original data will produce a completely different hash.
    
2. **Signing with Private Key:**
    
    The sender uses their private key to encrypt this hash, creating the digital signature unique to the data and the signer.
    
3. **Transmission:**
    
    The original message/transaction is sent along with the digital signature to the receiver or broadcasted to the blockchain network.
    

---

**How Verification Works:**

1. **Hashing Again:**
    
    The receiver or network node re-computes the hash of the received message.
    
2. **Decrypt Signature:**
    
    Using the sender’s public key, the digital signature is decrypted to obtain the original hash.
    
3. **Compare Hashes:**
    
    If the decrypted hash matches the newly computed hash, the signature is verified. This confirms:
    
    - The sender’s ownership of the private key (authentication)
    - Data integrity — the message wasn’t tampered with during transmission.

---

**Importance in Blockchain:**

- Digital signatures provide a secure mechanism to prevent forgery and unauthorized modifications of transactions.
- They replace the need for a central trusted authority by enabling peer-to-peer trust.
- All transactions on blockchains like Bitcoin and Ethereum are digitally signed to ensure validity and security.

**Example:**

- Alice wants to send coins to Bob. She signs the transaction hash with her private key. The network uses her public key to verify the signature before processing the transfer, ensuring Alice authorized this transaction.

**Key Algorithms:**

- ECDSA (Elliptic Curve Digital Signature Algorithm) is commonly used in blockchain systems, providing strong security with efficient key sizes.


## 6. Gas

Gas is a unit that measures the computational work required to perform operations on the Ethereum network. Every transaction, whether sending ETH or executing a smart contract, consumes gas proportional to the computational effort and storage used.


**Gas Units:**

- The smallest unit is **Wei**.
- 1,000,000,0001,000,000,0001,000,000,000 Wei = 1 Gwei (Gigawei)
- 1,000,000,0001,000,000,0001,000,000,000 Gwei = 1 ETH

Gas fees are paid in ETH but denominated in Gwei for user convenience.

**How Gas Works Internally:**

- Ethereum runs on the **Ethereum Virtual Machine (EVM)**, a decentralized virtual computer executing smart contract code.
- Each operation performed during transaction execution consumes a specific amount of gas based on its complexity. For example:
    - Simple ETH transfer requires 21,000 gas units.
    - More complex smart contract executions require more gas.
- Gas prevents costly or malicious computations from clogging the network by requiring prepayment for computational resources.

---

**Gas Fee Calculation:**

Transaction Fee=Gas Used×Gas Price\text{Transaction Fee} = \text{Gas Used} \times \text{Gas Price}

Transaction Fee=Gas Used×Gas Price

- **Gas Used:** Actual gas consumed by the transaction's computational steps.
- **Gas Price:** Cost per gas unit set by the user, consisting of two parts:
    - **Base Fee:** Dynamic, protocol-determined minimum fee (burnt after transaction).
    - **Priority Fee (Tip):** Optional tip to miners for transaction prioritization.


**Gas Limit:**

- The maximum amount of gas a user is willing to spend on their transaction.
- Protects users from runaway computations.
- Set before sending a transaction; if the transaction exceeds this limit, it fails but gas is still consumed.


**Base Fee and Its Dynamics:**

- Introduced in EIP-1559, replaces fixed gas prices with dynamic base fees.
- The base fee adjusts after each block based on how full the previous block was:
    - If a block is >50% full, base fee increases.
    - If a block is <50% full, base fee decreases.
- Base fee is **burnt**, removing ETH from circulation, helping control inflation and stabilize ETH's value.

---

**Transaction Lifecycle:**

- User specifies gas limit, max gas fee, and priority fee in the transaction.
- Miners include transactions based on fees offered (higher priority fees get faster inclusion).
- After execution, unused gas is refunded.
- Sufficient block confirmations validate and finalize the transaction.


**Importance of Gas:**

- Prevents network abuse and DoS attacks by attaching a cost to computation.
- Incentivizes miners/validators for processing transactions.
- Enables Ethereum's Turing-complete smart contracts to run autonomously and fairly without central control.

![gas.png](/home/rushhaabhhh/Downloads/gas-II1.png)

---