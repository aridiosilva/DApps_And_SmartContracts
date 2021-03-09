# DApps_And_Smart Contracts

Distributed Applications and Smart Contracts - Based on Blockchain Technology

# The Blockchain Platform That Supports Distributed Applications

## Peer-to-Peer Network Architecture

Bitcoin is structured as a peer-to-peer network architecture on top of the internet. The term peer-to-peer, or P2P, means that the computers that participate in the network
are peers to each other, that they are all equal, that there are no “special” nodes,and that all nodes share the burden of providing network services. The network
nodes interconnect in a mesh network with a “flat” topology. There is no server, no centralized service, and no hierarchy within the network. Nodes in a P2P network
both provide and consume services at the same time with reciprocity acting as the incentive for participation. P2P networks are inherently resilient, decentralized, and 
open. A preeminent example of a P2P network architecture was the early internet itself, where nodes on the IP network were equal. Today’s internet architecture is
more hierarchical, but the Internet Protocol still retains its flat-topology essence.

Beyond bitcoin, the largest and most successful application of P2P technologies is file sharing, with Napster as the pioneer and BitTorrent as the most recent evolution of
the architecture. Bitcoin’s P2P network architecture is much more than a topology choice. Bitcoin is a P2P digital cash system by design, and the network architecture is both a reflection and a foundation of that core characteristic. Decentralization of control is a core design principle that can only be achieved and maintained by a flat, decentralized P2P consensus network.

The term “bitcoin network” refers to the collection of nodes running the bitcoin P2P protocol. In addition to the bitcoin P2P protocol, there are other protocols such as
Stratum that are used for mining and lightweight or mobile wallets. These additional protocols are provided by gateway routing servers that access the bitcoin network
using the bitcoin P2P protocol and then extend that network to nodes running other 171 protocols. For example, Stratum servers connect Stratum mining nodes via the Stratum
protocol to the main bitcoin network and bridge the Stratum protocol to the bitcoin P2P protocol. We use the term “extended bitcoin network” to refer to the overall
network that includes the bitcoin P2P protocol, pool-mining protocols, the Stratum protocol, and any other related protocols connecting the components of the bitcoin
system.

## Blockchain Platform - Node Types and Roles 

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20The%20extended%20bitcoin%20network%20with%20various%20node%20types%2C%20gateways%2C%20and%20protocols%20001.png)

Although nodes in the bitcoin P2P network are equal, they may take on different roles depending on the functionality they are supporting. 

A bitcoin node is a collection of functions: 

> - routing, 
> - the blockchain database, 
> -  mining, and 
> -  wallet services. 
 
A full node with all four of these functions is shown in Figure below:
 
![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20-%20A%20bitcoin%20network%20node%20with%20all%20four%20functions%2000801.png)




All nodes include the routing function to participate in the network and might include other functionality. All nodes validate and propagate transactions and blocks,
and discover and maintain connections to peers. In the full-node example in Figure 8-1, the routing function is indicated by an orange circle named “Network
Routing Node” or with the letter “N.” 

Some nodes, called full nodes, also maintain a complete and up-to-date copy of the blockchain. Full nodes can autonomously and authoritatively verify any transaction
without external reference. Some nodes maintain only a subset of the blockchain and verify transactions using a method called simpliied payment veriication, or SPV.
These nodes are known as SPV nodes or lightweight nodes. In the full-node example in the figure, the full-node blockchain database function is indicated by a blue circle
172 | Chapter 8: The Bitcoin Network called “Full Blockchain” or the letter “B.” In Figure 8-3, SPV nodes are drawn without the blue circle, showing that they do not have a full copy of the blockchain.

Mining nodes compete to create new blocks by running specialized hardware to solve the Proof-of-Work algorithm. Some mining nodes are also full nodes, maintaining a
full copy of the blockchain, while others are lightweight nodes participating in pool mining and depending on a pool server to maintain a full node. The mining function
is shown in the full node as a black circle called “Miner” or the letter “M.” User wallets might be part of a full node, as is usually the case with desktop bitcoin
clients. Increasingly, many user wallets, especially those running on resourceconstrained devices such as smartphones, are SPV nodes. The wallet function is shown in Figure 8-1 as a green circle called “Wallet” or the letter “W.” In addition to the main node types on the bitcoin P2P protocol, there are servers and nodes running other protocols, such as specialized mining pool protocols and lightweight client-access protocols

## Diferent types of nodes on the extended bitcoin network




# The Blockchain Data Structure

## Introduction

The blockchain data structure is an ordered, back-linked list of blocks of transactions. The blockchain can be stored as a flat file, or in a simple database. The Bitcoin Core client stores the blockchain metadata using Google’s LevelDB database. Blocks are linked “back,” each referring to the previous block in the chain. The blockchain is often visualized as a vertical stack, with blocks layered on top of each other and the first block serving as the foundation of the stack. The visualization of blocks stacked on top of each other results in the use of terms such as “height” to refer to the distance from the first block, and “top” or “tip” to refer to the most recently added block.

Each block within the blockchain is identified by a hash, generated using the SHA256 cryptographic hash algorithm on the header of the block. Each block also references a previous block, known as the parent block, through the “previous block hash” field in the block header. In other words, each block contains the hash of its parent inside its own header. The sequence of hashes linking each block to its parent creates a chain going back all the way to the first block ever created, known as the genesis block.

Although a block has just one parent, it can temporarily have multiple children. Each of the children refers to the same block as its parent and contains the same (parent) hash in the “previous block hash” field. Multiple children arise during a blockchain “fork,” a temporary situation that occurs when different blocks are discovered almost simultaneously by different miners (see Blockchain Forks). Eventually, only one child block becomes part of the blockchain and the “fork” is resolved. Even though a block may have more than one child, each block can have only one parent. This is because a block has one single “previous block hash” field referencing its single parent.

The “previous block hash” field is inside the block header and thereby affects the current block’s hash. The child’s own identity changes if the parent’s identity changes. When the parent is modified in any way, the parent’s hash changes. The parent’s changed hash necessitates a change in the “previous block hash” pointer of the child. This in turn causes the child’s hash to change, which requires a change in the pointer of the grandchild, which in turn changes the grandchild, and so on. This cascade effect ensures that once a block has many generations following it, it cannot be changed without forcing a recalculation of all subsequent blocks. Because such a recalculation would require enormous computation, the existence of a long chain of blocks makes the blockchain’s deep history immutable, which is a key feature of bitcoin’s security.

One way to think about the blockchain is like layers in a geological formation, or glacier core sample. The surface layers might change with the seasons, or even be blown away before they have time to settle. But once you go a few inches deep, geological layers become more and more stable. By the time you look a few hundred feet down, you are looking at a snapshot of the past that has remained undisturbed for millions of years. In the blockchain, the most recent few blocks might be revised if there is a chain recalculation due to a fork. The top six blocks are like a few inches of topsoil. But once you go more deeply into the blockchain, beyond six blocks, blocks are less and less likely to change. After 100 blocks back there is so much stability that the coinbase transaction—the transaction containing newly mined bitcoins—can be spent. A few thousand blocks back (a month) and the blockchain is settled history. It will never change.

## Structure of a Block

A block is a container data structure that aggregates transactions for inclusion in the public ledger, the blockchain. The block is made of a header, containing metadata, followed by a long list of transactions that make up the bulk of its size. The block header is 80 bytes, whereas the average transaction is at least 250 bytes and the average block contains more than 500 transactions. A complete block, with all transactions, is therefore 1,000 times larger than the block header. Table below describes the structure of a block.

![block structure](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Table%207-1.%20The%20structure%20of%20a%20block%20001.png)

## Block Header

The block header consists of three sets of block metadata. First, there is a reference to a previous block hash, which connects this block to the previous block in the blockchain. The second set of metadata, namely the difficulty, timestamp, and nonce, relate to the mining competition, as detailed in Chapter 8. The third piece of metadata is the merkle tree root, a data structure used to efficiently summarize all the transactions in the block. Table below describes the structure of a block header.

![Block Header](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Table%207-2.%20The%20structure%20of%20the%20block%20header%20002.png)

# Tools for Blockchain Development

## Solidity

Solidity is one of the most popular programming languages used in blockchain development. It supports an object-oriented paradigm and is used to write smart contracts. Ethereum dApps can also be coded with Solidity. Solidity is designed to target the Ethereum Virtual Machine (EVM). 

So, what makes Solidity so unique? First of all, it is used in one of the most popular blockchain solutions, i.e., Ethereum. Secondly, it can be used to smart contracts that open up a variety of use-cases, especially when it comes to crowdfunding, voting, and multi-signature wallets. 

As a blockchain developer, you can get started by going through [Solidity documentation](https://solidity.readthedocs.io/en/v0.5.10/).

## Cakeshop

Cakeshop is a set of tools and APIs for working with Ethereum, packaged as a Java web application archive (WAR) that gets you up and running quickly. Cakeshop can either start up a geth node, which you can then interact with using the Cakeshop front-end, or it can be connected to an Ethereum-like node, such as Quorum, that you already have running. A given Cakeshop instance connects with one node on the blockchain network you connect to. Cakeshop lets you manage a local blockchain node. It comes with APIs and tools that you can use to set up the cluster node, work with contracts, and explore the chain.

- [Cakeshop documentation site](https://docs.goquorum.consensys.net/en/stable/Concepts/Cakeshop/)

## Geth

Geth is Ethereum node implementation. It is created using the Go programming language. Geth is used in a variety of tasks on the Ethereum blockchain. It can be used to transfer tokens, mine Ether tokens, and create smart contracts. Furthermore, it can also be used to explore block history.  Geth is available in the three interfaces including:

- JSON-RPC server.
- Command-line.
- Interactive console.

As a blockchain developer, you can use Geth on Windows, Mac, and Linux. Once you install Geth, you need to either connect to an existing blockchain or create your own. To simplify things, Geth automatically connects to the Ethereum mainnet.

Warning: Geth downloads the whole Ethereum blockchain before you can start using it. Depending on your internet speed connection, it can take a while. We also recommend using an external hard disk to store the Ethereum blockchain.

- [Geth Ethereum Documentation](https://geth.ethereum.org/docs/getting-started)

## Blockchain Testnet

As a blockchain developer, you will always need a blockchain testnet.

It is an essential tool, as it lets you test your dApps before making them live. Each blockchain solution has its testnet, and we recommend that you use the respective testnet.

Testnets are especially useful, as it lets you test without spending real resources. Ethereum, for example, uses gas as the fuel for carrying out different actions. Developers can't spend gas every time they do a test run. This means spending thousands of dollars to test. It is not feasible.

A testnet lets blockchain developer iron out bugs without spending large amounts of cash. The choice of testnet depends on your dApp. You can use:

- public test, 
- private test, or 
- GanachiCLI — a customizable blockchain emulator.

## Blockchain-as-a-Service (BaaS)

Implementing a full end-to-end blockchain solution is not practical for any business out there. This gave rise to the Blockchain-as-a-Service (BaaS).

With BaaS, businesses can create and host their dApp solutions using a cloud infrastructure. They have to pay for using BaaS. Moreover, they also need to hire blockchain developers to take care of all the implementation processes.

As a blockchain developer, you should know how to work with BaaS. It can help you gain more trust and reputation. It is similar to Software as a Service(SaaS) model. A few examples of BaaS solutions that you should know include Azure, Microsoft, and SAP.



## Truffle

Truffle is an Ethereum blockchain framework. It offers an asset pipeline and development environment for Ethereum development. With Truffle, you can develop complex Ethereum dApps and smart contracts. It has a vast library that lets you tackle challenging requirements. The key features offered by Truffle include the following:

- Automate contract testing using Chai and Mocha.
- Do full smart contract development including linking, compilation, and deployment.
- Do custom build procedures with the configurable build pipeline.

[Truffle homepage](https://www.trufflesuite.com)

## Ether.js

Ether.js is a handy tool when it comes to developing client-side JavaScript wallets. It lets you interact with Ethereum blockchain. Initially, it was only used to work with ethers.io, but now, it is a full-fledged general-purpose library.

The key feature of Ether.js includes the following:

- Private keys safe in client.
- Easy connection to Ethereum nodes using MetaMask, Etherscan, and other tools.
- Small in size, 88kb compressed.
- Great documentation.
- Open-source (comes with MIT License).

## Remix IDE

Remix IDE is a popular IDE that runs from the browser. It lets you develop Solidity contracts from the browser. It is developed using JavaScript, which means that you can use any modern browser. You can also use it locally. It comes with module support that brings more functionality to the IDE. For example, you can use a file explorer module to save or load files from your computer. Other useful modules include plugin manager, solidity editor, terminal, and settings.

They also have excellent [documentation](https://remix-ide.readthedocs.io/en/latest/).

## Hyperledger Caliper

Hyperledger Caliper lets you check the blockchain performance.  It can determine blockchain performance using different parameters, including latency, success rate, resource consumption, and throughput.

- [Github Documentation of Hyperledger Caliper](https://github.com/hyperledger/caliper).
- [GEt Started with Hyperledger Caliper](https://hyperledger.github.io/caliper/v0.4.2/getting-started/).

## Solc

If you have used Solidity, you already know its syntax is similar to ECMAScript, as it is a loosely-typed language. However, the Ethereum Virtual Machine uses a slightly different format, which makes Solc a must-have tool for Ethereum related projects. Solc is a Solidity compiler that converts solidity script into a more readable format. Its popularity can also be gauged from the fact that it comes natively with most of the Ethereum nodes. Solc can also be used for offline compiling.

- [github link to JavaScript bindings for the Solidity compiler](https://github.com/ethereum/solc-js)

## dAppBoard

dAppBoard is an analytical platform used for Ethereum smart contracts. Moreover, it also comes with Ethereum blockchain explorer. dAppBoard is web-based and lets you monitor smart contracts running on Ethereum networks. It can give you information, such as the total number of users of a particular dApp or an overview of the whole Ethereum network.

- [link to the DappBoard Homepage](https://dappboard.com/?ref=cypherhunter)


