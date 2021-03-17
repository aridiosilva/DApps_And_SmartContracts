# DApps and Smart Contracts

Distributed Applications and Smart Contracts - Based on Blockchain Technology

## The Blockchain - Framework That Supports Distributed Applications

## Core Blockchain Architecture Components

> - **Node** - user or computer within the blockchain architecture (each has an independent copy of the whole blockchain ledger)
> - **Transaction** - smallest building block of a blockchain system (records, information, etc.) that serves as the purpose of blockchain
> - **Block** - a data structure used for keeping a set of transactions which is distributed to all nodes in the network
> - **Chain** - a sequence of blocks in a specific order
> - **Miners** - specific nodes which perform the block verification process before adding anything to the blockchain structure
> - **Consensus (consensus protocol)** - a set of rules and arrangements to carry out blockchain operations

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

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20The%20extended%20bitcoin%20network%20with%20various%20node%20types%2C%20gateways%2C%20and%20protocols%20001.png)

## Blockchain Platform - Node Types and Roles 

Although nodes in the bitcoin P2P network are equal, they may take on different roles depending on the functionality they are supporting. 

All nodes include the routing function to participate in the network and might include other functionality. All nodes validate and propagate transactions and blocks,
and discover and maintain connections to peers. 

A bitcoin node is a collection of functions: 

> - routing, 
> - the blockchain database, 
> -  mining, and 
> -  wallet services. 

Below we can see the four functions that can exist in one blockchain node:

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20-%20A%20bitcoin%20network%20node%20with%20all%20four%20functions%2000801.png)

A full node with all four of these functions is shown in image above. In the full-node example above, the routing function is indicated by an orange circle named “Network Routing Node” or with the letter “N.” Some nodes, called full nodes, also maintain a complete and up-to-date copy of the blockchain. Full nodes can autonomously and authoritatively verify any transaction without external reference. The full-node blockchain database function is indicated by a blue circle called “Full Blockchain” or the letter “B.”

Some nodes maintain only a subset of the blockchain and verify transactions using a method called **simplified payment verifrication**, or **SPV**. These nodes are known as SPV nodes or lightweight nodes.  In Figure 8-3, SPV nodes are drawn without the blue circle, showing that they do not have a full copy of the blockchain.

Mining nodes compete to create new blocks by running specialized hardware to solve the **Proof-of-Work (PoW) algorithm*.  Some mining nodes are also full nodes, maintaining a full copy of the blockchain, while others are lightweight nodes participating in pool mining and depending on a pool server to maintain a full node. The mining function is shown in the full node as a black circle called “Miner” or the letter “M.” User wallets might be part of a full node, as is usually the case with desktop bitcoin clients.

Increasingly, many user wallets, especially those running on resource constrained devices such as smartphones, are SPV nodes.  The wallet function is shown in images below as a green circle called “Wallet” or the letter “W.”  In addition to the main node types on the bitcoin P2P protocol, there are servers and nodes running other protocols, such as specialized mining pool protocols and lightweight client-access protocols.

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20-%20Reference%20Client%20-%20Bitcoing%20Core%20-%20001.jpg)

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20Full%20Blockchain%20Node%20002.png)

![Lightweight SPV nodes](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20Lightweight%20SPV%20Wallet%20Node%20004.png)

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20Lightweight%20SPV%20Stratum%20Wallet%20Node%20009.png)

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20Solo%20Miner%20Node%20003.png)

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20Pool%20Protocol%20Servers%20-Gateway%20Routers.jpg)

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure%20Mining%20Nodes%20007.png)

# The Blockchain Data Structure

## Introduction

The blockchain data structure is an ordered, back-linked list of blocks of transactions. 

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Chain_of_Blocks_Ordered%2CBack-Linked_list_Blockchain.jpg)

The blockchain can be stored as a flat file, or in a simple database. The Bitcoin Core client stores the blockchain metadata using Google’s LevelDB database. Blocks are linked “back,” each referring to the previous block in the chain. The blockchain is often visualized as a vertical stack, with blocks layered on top of each other and the first block serving as the foundation of the stack. The visualization of blocks stacked on top of each other results in the use of terms such as “height” to refer to the distance from the first block, and “top” or “tip” to refer to the most recently added block.

Each block within the blockchain is identified by a hash, generated using the SHA256 cryptographic hash algorithm on the header of the block. Each block also references a previous block, known as the parent block, through the “previous block hash” field in the block header. In other words, each block contains the hash of its parent inside its own header. The sequence of hashes linking each block to its parent creates a chain going back all the way to the first block ever created, known as the genesis block.

Although a block has just one parent, it can temporarily have multiple children. Each of the children refers to the same block as its parent and contains the same (parent) hash in the “previous block hash” field. Multiple children arise during a blockchain “fork,” a temporary situation that occurs when different blocks are discovered almost simultaneously by different miners (see Blockchain Forks). Eventually, only one child block becomes part of the blockchain and the “fork” is resolved. Even though a block may have more than one child, each block can have only one parent. This is because a block has one single “previous block hash” field referencing its single parent.

The “previous block hash” field is inside the block header and thereby affects the current block’s hash. The child’s own identity changes if the parent’s identity changes. When the parent is modified in any way, the parent’s hash changes. The parent’s changed hash necessitates a change in the “previous block hash” pointer of the child. This in turn causes the child’s hash to change, which requires a change in the pointer of the grandchild, which in turn changes the grandchild, and so on. This cascade effect ensures that once a block has many generations following it, it cannot be changed without forcing a recalculation of all subsequent blocks. Because such a recalculation would require enormous computation, the existence of a long chain of blocks makes the blockchain’s deep history immutable, which is a key feature of bitcoin’s security.

In the blockchain, the most recent few blocks might be revised if there is a chain recalculation due to a fork. But once you go more deeply into the blockchain, beyond six blocks, blocks are less and less likely to change. After 100 blocks back there is so much stability that the coinbase transaction—the transaction containing newly mined bitcoins—can be spent. A few thousand blocks back (a month) and the blockchain is settled history. It will never change.

## Structure of a Block

![](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Figure_block_strcuture_of_blockchain001.jpg)

A block is a container data structure that aggregates transactions for inclusion in the public ledger, the blockchain. The block is made of a header, containing metadata, followed by a long list of transactions that make up the bulk of its size. The block header is 80 bytes, whereas the average transaction is at least 250 bytes and the average block contains more than 500 transactions. A complete block, with all transactions, is therefore 1,000 times larger than the block header. Table below describes the structure of a block.

![block structure](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Table%207-1.%20The%20structure%20of%20a%20block%20001.png)

## Block Header

The block header consists of three sets of block metadata. First, there is a reference to a previous block hash, which connects this block to the previous block in the blockchain. The second set of metadata, namely the difficulty, timestamp, and nonce, relate to the mining competition, as detailed in Chapter 8. The third piece of metadata is the merkle tree root, a data structure used to efficiently summarize all the transactions in the block. Table below describes the structure of a block header.

![Block Header](https://github.com/aridiosilva/DApps_And_SmartContracts/blob/main/Table%207-2.%20The%20structure%20of%20the%20block%20header%20002.png)


## Block Identifiers: Block Header Hash and Block Height

The primary identifier of a block is its cryptographic hash, a digital fingerprint, made by hashing the block header twice through the SHA256 algorithm. The resulting 32-byte hash is called the block hash but is more accurately the block header hash, because only the block header is used to compute it. For example,

000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f 

is the block hash of the first bitcoin block ever created. The block hash identifies a block uniquely and unambiguously and can be independently derived by any node by simply hashing the block header.

Note that the block hash is not actually included inside the block’s data structure, neither when the block is transmitted on the network, nor when it is stored on a node’s persistence storage as part of the blockchain. Instead, the block’s hash is computed by each node as the block is received from the network. The block hash might be stored in a separate database table as part of the block’s metadata, to facilitate indexing and faster retrieval of blocks from disk.

A second way to identify a block is by its position in the blockchain, called the block height. The first block ever created is at block height 0 (zero) and is the same block that was previously referenced by the following block hash 000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f. A block can thus be identified two ways: by referencing the block hash or by referencing the block height. Each subsequent block added “on top” of that first block is one position “higher” in the blockchain, like boxes stacked one on top of the other. The block height on January 1, 2014, was approximately 278,000, meaning there were 278,000 blocks stacked on top of the first block created in January 2009.

Unlike the block hash, the block height is not a unique identifier. Although a single block will always have a specific and invariant block height, the reverse is not true—the block height does not always identify a single block. Two or more blocks might have the same block height, competing for the same position in the blockchain. This scenario is discussed in detail in the section Blockchain Forks. The block height is also not a part of the block’s data structure; it is not stored within the block. Each node dynamically identifies a block’s position (height) in the blockchain when it is received from the bitcoin network. The block height might also be stored as metadata in an indexed database table for faster retrieval.

Note: A block’s block hash always identifies a single block uniquely. A block also always has a specific block height. However, it is not always the case that a specific block height can identify a single block. Rather, two or more blocks might compete for a single position in the blockchain.

## The Genesis Block

The first block in the blockchain is called the genesis block and was created in 2009. It is the common ancestor of all the blocks in the blockchain, meaning that if you start at any block and follow the chain backward in time, you will eventually arrive at the genesis block.

Every node always starts with a blockchain of at least one block because the genesis block is statically encoded within the bitcoin client software, such that it cannot be altered. Every node always “knows” the genesis block’s hash and structure, the fixed time it was created, and even the single transaction within. Thus, every node has the starting point for the blockchain, a secure “root” from which to build a trusted blockchain.

## Linking Blocks in the Blockchain

Bitcoin full nodes maintain a local copy of the blockchain, starting at the genesis block. The local copy of the blockchain is constantly updated as new blocks are found and used to extend the chain. As a node receives incoming blocks from the network, it will validate these blocks and then link them to the existing blockchain. To establish a link, a node will examine the incoming block header and look for the “previous block hash.”

## Merkle Trees

Each block in the bitcoin blockchain contains a summary of all the transactions in the block, using a merkle tree.

A merkle tree, also known as a binary hash tree, is a data structure used for efficiently summarizing and verifying the integrity of large sets of data. Merkle trees are binary trees containing cryptographic hashes. The term “tree” is used in computer science to describe a branching data structure, but these trees are usually displayed upside down with the “root” at the top and the “leaves” at the bottom of a diagram, as you will see in the examples that follow.

Merkle trees are used in bitcoin to summarize all the transactions in a block, producing an overall digital fingerprint of the entire set of transactions, providing a very efficient process to verify whether a transaction is included in a block. A Merkle tree is constructed by recursively hashing pairs of nodes until there is only one hash, called the root, or merkle root. The cryptographic hash algorithm used in bitcoin’s merkle trees is SHA256 applied twice, also known as double-SHA256.

When N data elements are hashed and summarized in a merkle tree, you can check to see if any one data element is included in the tree with at most 2*log2(N) calculations, making this a very efficient data structure.

![](https://github.com/aridiosilva/Blockchain/blob/main/Blockchain_and_Merkle_Tree_figure001.jpg)

Example of C++ code below demonstrates the process of creating a merkle tree from the leaf-node hashes up to the root, using the libbitcoin library for some helper functions.

```c++
#include <bitcoin/bitcoin.hpp>

bc::hash_digest create_merkle(bc::hash_digest_list& merkle)
{
    // Stop if hash list is empty.
    if (merkle.empty())
        return bc::null_hash;
    else if (merkle.size() == 1)
        return merkle[0];

    // While there is more than 1 hash in the list, keep looping...
    while (merkle.size() > 1)
    {
        // If number of hashes is odd, duplicate last hash in the list.
        if (merkle.size() % 2 != 0)
            merkle.push_back(merkle.back());
        // List size is now even.
        assert(merkle.size() % 2 == 0);

        // New hash list.
        bc::hash_digest_list new_merkle;
        // Loop through hashes 2 at a time.
        for (auto it = merkle.begin(); it != merkle.end(); it += 2)
        {
            // Join both current hashes together (concatenate).
            bc::data_chunk concat_data(bc::hash_size * 2);
            auto concat = bc::make_serializer(concat_data.begin());
            concat.write_hash(*it);
            concat.write_hash(*(it + 1));
            assert(concat.iterator() == concat_data.end());
            // Hash both of the hashes.
            bc::hash_digest new_root = bc::bitcoin_hash(concat_data);
            // Add this to the new list.
            new_merkle.push_back(new_root);
        }
        // This is the new list.
        merkle = new_merkle;

        // DEBUG output -------------------------------------
        std::cout << "Current merkle hash list:" << std::endl;
        for (const auto& hash: merkle)
            std::cout << "  " << bc::encode_hex(hash) << std::endl;
        std::cout << std::endl;
        // --------------------------------------------------
    }
    // Finally we end up with a single item.
    return merkle[0];
}

int main()
{
    // Replace these hashes with ones from a block to reproduce the same merkle root.
    bc::hash_digest_list tx_hashes{{
        bc::decode_hash("0000000000000000000000000000000000000000000000000000000000000000"),
        bc::decode_hash("0000000000000000000000000000000000000000000000000000000000000011"),
        bc::decode_hash("0000000000000000000000000000000000000000000000000000000000000022"),
    }};
    const bc::hash_digest merkle_root = create_merkle(tx_hashes);
    std::cout << "Result: " << bc::encode_hex(merkle_root) << std::endl;
    return 0;
}
```
Below are the results of compiling and running the merkle example code above:

```shell
$ # Compile the merkle.cpp code
$ g++ -o merkle merkle.cpp $(pkg-config --cflags --libs libbitcoin)
$ # Run the merkle executable
$ ./merkle
Current merkle hash list:
  32650049a0418e4380db0af81788635d8b65424d397170b8499cdc28c4d27006
  30861db96905c8dc8b99398ca1cd5bd5b84ac3264a4e1b3e65afa1bcee7540c4

Current merkle hash list:
  d47780c084bad3830bcdaf6eace035e4c6cbf646d103795d22104fb105014ba3

Result: d47780c084bad3830bcdaf6eace035e4c6cbf646d103795d22104fb105014ba3
```

# Consensus

## Introduction

the rules that everyone must agree to for the system to operate in a decentralized, yet deterministic, manner. In computer science, the term consensus predates blockchains and is related to the broader problem of synchronizing state in distributed systems, such that different participants in a distributed system all (eventually) agree on a single system-wide state. This is called “reaching consensus.”

When it comes to the core function of decentralized record keeping and verification, it can become problematic to rely on trust alone to ensure that information derived from state updates is correct. This rather general challenge is particularly pronounced in decentralized networks because there is no central entity to decide what is true. The lack of a central decision-making entity is one of the main attractions of blockchain platforms, because of the resulting capacity to resist censorship and the lack of dependence on authority for permission to access information. However, these benefits come at a cost: without a trusted arbitrator, any disagreements, deceptions, or differences need to be reconciled using other means. Consensus algorithms are the mechanism used to reconcile security and decentralization.

In blockchains, consensus is a critical property of the system. Simply put, there is money at stake! So, in the context of blockchains, consensus is about being able to arrive at a common state, while maintaining decentralization. In other words, consensus is intended to produce a system of strict rules without rulers. There is no one person, organization, or group “in charge”; rather, power and control are diffused across a broad network of participants, whose self-interest is served by following the rules and behaving honestly. 

The ability to come to consensus across a distributed network, under adversarial conditions, without centralizing control is the core principle of all open public blockchains. To address this challenge and maintain the valued property of decentralization, the community continues to experiment with different models of consensus. This chapter explores these consensus models and their expected impact on smart contract blockchains such as Ethereum. 

NOTE:  While consensus algorithms are an important part of how blockchains work, they operate at a foundational layer, far below the abstraction of smart contracts. In other words, most of the details of consensus are hidden from the writers of smart contracts. You don’t need to know how they work to use Ethereum, any more than you need to know how routing works to use the internet.

## Consensus via Proof of Work (Pow)

The creator of the original blockchain, Bitcoin, invented a consensus algorithm called proof of work (PoW). Arguably, PoW is the most important invention underpinning Bitcoin. The colloquial term for PoW is “mining,” which creates a misunderstanding about the primary purpose of consensus. Often people assume that the purpose of mining is the creation of new currency, since the purpose of real-world mining is the extraction of precious metals or other resources. Rather, the real purpose of mining (and all other consensus models) is to secure the blockchain, while keeping control over the system decentralized and diffused across as many participants as possible. The reward of newly minted currency is an incentive to those who contribute to the security of the system: a means to an end. In that sense, the reward is the means and decentralized security is the end.
In PoW consensus there is also a corresponding “punishment,” which is the cost of energy required to participate in mining. If participants do not follow the rules and earn the reward, they risk the funds they have already spent on electricity to mine. Thus, PoW consensus is a careful balance of risk and reward that drives participants to behave honestly out of self-interest.

Ethereum is currently a PoW blockchain, in that it uses a PoW algorithm with the same basic incentive system for the same basic goal: securing the blockchain while decentralizing control. Ethereum’s PoW algorithm is slightly different than Bitcoin’s and is called Ethash. We will examine the function and design characteristics of the algorithm in “Ethash: Ethereum’s Proof-of-Work Algorithm”.

## Consensus via Proof of Stake (PoS)

Historically, proof of work was not the first consensus algorithm proposed. Preceding the introduction of proof of work, many researchers had proposed variations of consensus algorithms based on financial stake, now called proof of stake (PoS). In some respects, proof of work was invented as an alternative to proof of stake. Following the success of Bitcoin, many blockchains have emulated proof of work. Yet the explosion of research into consensus algorithms has also resurrected proof of stake, significantly advancing the state of the technology. From the beginning, Ethereum’s founders were hoping to eventually migrate its consensus algorithm to proof of stake. In fact, there is a deliberate
handicap on Ethereum’s proof of work called the difficulty bomb, intended to gradually make proof-of-work mining of Ethereum more and more difficult, thereby forcing the transition to proof of stake.

At the time of publication of this book, Ethereum is still using proof of work, but the ongoing research toward a proof-of-stake alternative is nearing completion. Ethereum’s planned PoS algorithm is called Casper. The introduction of Casper as a replacement for Ethash has been postponed several times over the past two years, necessitating interventions to defuse the difficulty bomb and postpone its forced obsolescence of proof of work.  

In general, a PoS algorithm works as follows. The blockchain keeps track of a set of validators, and anyone who holds the blockchain’s base cryptocurrency (in Ethereum’s case, ether) can become a validator by sending a special type of transaction that locks up their ether into a deposit. The validators take turns proposing and voting on the next valid block, and the weight of each validator’s vote depends on the size of its deposit (i.e., stake). Importantly, a validator risks losing their deposit if the block they staked it on is rejected by the majority of validators. Conversely, validators earn a small reward, proportional to their deposited stake, for every block that is accepted by the majority. Thus, PoS forces validators to act honestly and follow the consensus rules, by a system of reward and punishment. The major difference between PoS and PoW is that the punishment in PoS is intrinsic to the blockchain (e.g., loss of staked ether),
whereas in PoW the punishment is extrinsic (e.g., loss of funds spent on electricity).

## Principles of Consensus

The principles and assumptions of consensus algorithms can be more clearly understood by asking a few key questions:

> 1) Who can change the past, and how? (This is also known as immutability.)
> 1) Who can change the future, and how? (This is also known as finality.)
> 1) What is the cost to make such changes?
> 1) How decentralized is the power to make such changes?
> 1) Who will know if something has changed, and how will they know?
> 
Consensus algorithms are evolving rapidly, attempting to answer these questions in increasingly innovative ways.

## Controversy and Competition

At this point you might be wondering: Why do we need so many different consensus algorithms? Which one works better? The answer to the latter question is at the center of the most exciting area of research in distributed systems of the past decade. It all boils down to what you consider “better” — which in the context of computer science is about assumptions, goals, and the unavoidable trade-offs.

It is likely that no algorithm can optimize across all dimensions of the problem of decentralized consensus. When someone suggests that one consensus algorithm is “better” than the others, you should start asking questions that clarify: Better at what? Immutability, finality, decentralization, cost? There is no clear answer to these questions, at least not yet. Furthermore, the design of consensus algorithms is at the center of a multi-billion-dollar industry and generates enormous controversy and heated arguments. In the end, there might not be a “correct” answer, just as there might be different answers for different applications.

The entire blockchain industry is one giant experiment where these questions will be tested under adversarial conditions, with enormous monetary value at stake. In the end, history will answer the controversy.

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





