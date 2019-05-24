### General

**1. What is GEO?**
GEO is an open-source base layer protocol for cost-efficient, lightweight and scalable value transfer, merging blockchain and traditional worlds together.

**2. What is GEO’s mission?**
GEO is on a mission to empower the Internet of Value by creating a universal value transfer ecosystem.

**3. What exactly do you build?**
We create a framework which enables businesses or developers to run their applications or launch new networks, as well as to connect to existing networks of other applications which use different value equivalents (blockchain assets, local currencies etc). The GEO Protocol ensures fast, free and secure transactions between the networks within the ecosystem. It enables users to exchange different equivalents and guarantees cyclic clearing of the transactions.

**4. What makes you different from competitors?**
GEO is an open-source, off-chain, blockchain agnostic value transfer protocol, that counts speed, cost-efficiency, safety and interoperability as its top priorities. GEO implements a different network topology than those of similar solutions, enabling advanced transaction routing, local consensus algorithm, and full transaction atomicity.

To read more, please read chapter 1.3 Related work in our [Whitepaper.](https://drive.google.com/file/d/14VxBQq6Gu_Y5mnkKxZPNL4EfPohoiArz/view)

**5. How GEO differs from Interledger Protocol, Lightning Network or Raiden Network?**
Several GEO Protocol features make it different from what ILP currently have to offer. They include:
- Strong protocol-defined atomicity rules, and operations finality/conflicts resolving flow;
- Multi-paths operations support: one operation might involve as many paths as it needs to succeed.
- Near real-time flow prediction for random pair of nodes.
- Strict 6-levels long paths routing.
- Real-time cyclic debts discovering and clearing.

An important thing to note is that ILP does not provide any guarantees on operations atomicity: both on the ILP nodes level, nor on the external environment level.

One of the goals of the GEO Protocol is to provide atomicity on both levels. Current BETA supports atomic operations on GEO Nodes level, and we have initial architecture design indicating how it should be implemented/proposed to the community for the external environment level.

In contrast to LN and Raiden, GEO strives to be platform-independent and provides an ability to process assets of different natures: FIAT equivalents, crypto-assets, custom equivalents (for attention economy, local currencies, etc). By contrast, LN relies hard on bitcoin and Raiden on Ethereum.

Another noticeable difference is the cryptography used: the GEO ecosystem goes out of use classic asymmetric cryptography (RSA/ECDSA) due to the quantum riskiness and replaces it with quantum-persistent Lamport signatures (when possible). In all other cases, the GEO Protocol tries to provide configurable alternatives for the end-users to make it possible for them to choose some features and automatization in the face of some trade-offs. The core functionality of the GEO Node is fully covered by the quantum-resistant crypto.

There are also great differences in low-level mechanics (routing/payments/cycles discovering) etc. 

Last but not least, GEO Protocol endeavours to provide a solution that would feasibly work even on a cellphone in dynamic routing networks.

**6. Who can use GEO?**
Any person with any device (even a mobile device in the nearest future) can become part of the ecosystem. However, GEO Protocol is created with developers and businesses in mind, so that they can potentially connect different applications or ecosystems to the [GEO Network.](http://geoexplorer.io/)

**7. How can I use GEO?**
To become a member of the GEO Network, you need to join the application or solution which is using GEO Protocol and is a part of the Network. This way is the easiest one, but you can also run a node following [instructions on the Github.](https://github.com/GEO-Protocol/Documentation/tree/master/client/tutorials)

**8. What would you recommend me to read first to have a birds-eye overview?**
You will gain a solid understanding of the GEO Protocol by watching this video, [“What is GEO Protocol for?”](https://www.youtube.com/watch?v=g82z5V4AIi4&t). Alternatively, by reading the article [“What Hair on Fire Problem Does the GEO Protocol Solve?”](https://medium.com/geoprotocol/what-hair-on-fire-problem-does-the-geo-protocol-solve-6b1a3d6a7378)

We would also recommend starting with a [short explanatory video](https://www.youtube.com/watch?v=mrDzMgdjTN0&t) about basic components and technologies used in GEO Ecosystem. 
In addition, it would be instructive to read the article [“GEO: infrastructure off-chain protocol for IoV (Internet of Value)”](https://medium.com/geoprotocol/introducing-geo-protocol-140e94ab5fba), which explains the contribution of GEO to the development of Internet of Value.

Lastly, feel free to explore and learn more about the project on our [Medium](https://medium.com/geoprotocol) and [YouTube](https://www.youtube.com/channel/UC3jEvQvZAmCUXa7dCoX9_Lg) channels. 


**9. What is GEO-Pay?**
[GEO-Pay](https://geo-pay.net/) is the first production usage of our technology. It is the first service that uses GEO Protocol as the main technical framework. Essentially, GEO-Pay is the decentralized credit network where people could establish trustlines between each other, or with different applications, and transfer value within the network.

**10. How big is your team?**
As of right now, there are 18 people in the core GEO team. However, we are constantly growing and looking for like-minded specialists. If you are a C++ developer, security analyst, cryptographers economist, or data scientist looking for your next exciting opportunity, feel free to reach out at [jobs@geoprotocol.io.](mailto:jobs@geoprotocol.io)


### Technology:

**1. What technology stands behind GEO Protocol?**
GEO Protocol uses 4 main algorithms:

1) Topology Collection Algorithm. It creates a topology map by obtaining information about the possible connections between the sending and receiving node, as well as overall payment capacity on intermediary nodes.

2) Payment Path Building (Routing) and Maximum Flow Prediction Algorithm. Considering the topology map, it calculates the maximum possible flow that may be transferred from one node to another. It also seeks the best route for the asset transfer.

3) Payment Algorithm. It is responsible for the actual transfer of funds.

4) Cyclic Clearing algorithm. It finds the debt cycles and closes them.

Another key technical feature, which we are planning to introduce in the next release, is the ability to connect nodes with composite channels.

**2. What is a composite channel?**
It is a type of connection between 2 nodes that includes trustline connection as well as state channel. For example, nodes A and B open a communication channel in BTC, with the capacity of 10 BTC. At the same time, they open multisig on Bitcoin’s blockchain with the capacity of 3 BTC. The other 7 BTC, just as with a normal trustline connection, are secured only by the trust between counterparties (or legal contract, for example).

**3. What is a trustline?**
Trustline is a connection between 2 nodes which allows the nodes to account and transfer values between each other. Please [see here](https://www.youtube.com/watch?v=ieZKustA2Hk&t) for more information.

**4. Why should I use trustlines?**
Trustlines are used to execute transactions between two independent registries. It should be noted that operations on trustlines do not necessarily change the data in registers (for example, when the registry is outside the GEO node). Rather, it records the transfer of values between them instead.

Examples: 
1) Communication between two users (to account finance relations).

2) Joining the user to the hub.

3) Interconnections between service providers (hubs, gateways, market makers, etc).

4) Accounting asset equivalents (for example, in IoT).


**5. What is a state channel?**
A state channel is a type of connection that allows for fast, safe and trustless offchain transactions between two nodes from one blockchain ecosystem. Cryptoasset is backed on the channel by onchain transactions.

**6. Why are you using non-common cryptography?**
GEO Node actively uses [Blake2B](https://blake2.net/) and, built on to it, [Lamport Scheme](https://en.wikipedia.org/wiki/Lamport_signature). It also uses [ChaCha20-Poly1305](https://tools.ietf.org/html/rfc7539) for traffic encryption. All of which are well-known and battle-tested cryptographic solutions. 

Lamport Signatures provide a formidable line of defence against quantum-base attacks due to their hash based nature, but are also significantly larger than classic asymmetric crypto-signatures, making them almost unusable in public blockchains implementation. However, it is acceptable for the GEO Protocol mechanics (see the [Twin Spark algo specs](https://github.com/GEO-Protocol/specs-protocol/blob/master/transactions/transactions.md) for the details).

**7. Can I transfer any physical assets within the network?**
GEO Protocol enables the free transfer of any equivalents in the network. Network participants can transfer both backed asset equivalents and credit obligations (IOU). These are not physical assets, but they could be backed by a custodian or state channels.

**8. How many transactions per second are supported?**
It really depends on the hardware configuration, Internet communication and the speed of the least powerful nodes involved in each operation (because at least 2 nodes are involved in each transaction, and operations have a sequential nature). In theory, the GEO node is able to perform up to several thousand concurrent operations with different nodes through the same trustlines/channels.

**9. What do you mean “concurrent operations”?**
GEO node implements the algorithm, which makes it possible to concurrently use the same trustline in many different operations, up to the moment when the trust line capacity would be exceeded. GEO Protocol is smart enough to reserve only part of trustline and to leave a free segment for other operations. In other words, making it possible to keep the liquidity of the network at a very high level.

**10. How your idea is similar to the original Ryan Fuger's idea?**
As a decentralized credit network, our protocol is the truly distributed realization of Ryan Fuger’s idea.


### Token Economy:

**1. Will there be a native token?**
There are 2 types of tokens designed in GEO Network:

1) GEO tokens are designed to be used by service providers as a way to signal their reliability and commitment to the ecosystem. They create economic incentives that drive quality and availability of services in the GEO network. The GEO Token is implemented on the Ethereum blockchain as an ERC-20 smart contract in the total amount of 100,000,000 GEO tokens.

2) Token Certificates (TC) is the Observer chain native token, with which GEO users can buy services from observers. The total supply of the certificates is unlimited, and a certain quantity is issued once per week to all observers, who may then sell them to users. Initially, the issuance quantity is restricted to 10,000 TCs per week, but it can be modified by the vote of the observers. Observers sell the issued TCs through marketplaces or individual agreements to users and application developers. Users and applications then use TC to buy services from observers when needed.

**2. What rights are granted to the token holders?**
GEO Token holders can use their tokens to vote for service providers (observers, state keepers, and hubs) to increase their ratings. Service providers, in turn, may remunerate the voters (delegators) with a share of their compensation. Considering TC, users and applications use them to buy services from observers when needed.

**3. What is the token flow within the ecosystem?**
You can find the token flow model [here.](https://drive.google.com/open?id=1AiISHweY_n3iR6yeKiutJ-vl9NrFUyAs) 


### Business Development:

**1. What are the most immediate use cases for GEO?**
Primarily, an implementation of the protocol could be divided in two different ways: 

1) The protocol allows large players and individual users alike to connect to the network, interact with each other, and gain access to all of the services available on the network. One of the use cases of such an approach is connecting cryptocurrency exchanges in one common network with shared liquidity. That provides benefits for the exchanges and their users, specifically entering new markets and gaining additional sources of liquidity, fast transactions between various exchanges making arbitrage opportunities.

2) Another way of using the protocol is to build a dApp from scratch. Considering the protocol features, it’s possible to develop the following solutions:
- Payment systems; 
- IoT solutions; 
- Cross-chain DEXs; 
- Local currencies; 
- Voting systems; 
- Clearing systems, etc.

**2. What kind of partners are you looking for?**
We are seeking partners that are able to develop the infrastructure of GEO Network, to start. This could include financial gateways, custodian services, liquidity providers (market makers). Also, we are actively communicating with integrators for each mentioned use case. Each business, solution, and dApp is valuable for the entire network because when someone joins, each existing participant can access its services and vice-versa.

**3. How can I become a partner?**
If you are interested in becoming a partner, feel free to [contact us](mailto:partners@geoprotocol.io)

**4. How can I start building on GEO ecosystem?**
To start building on GEO or to connect to the GEO Network, visit our [GitHub](https://github.com/GEO-Protocol/Documentation/tree/master/client/tutorials) or [contact the team](mailto:info@geoprotocol.io) 

**5. Do you have open source contributors?**
Anyone is able to contribute to the project. You can check the existing code on GitHub and propose your own solutions. For any other contribution, feel free to contact the team.

