### General

**1. What is GEO?**
GEO is an open-source base layer protocol for cost-efficient, lightweight and almost infinitely scalable value transfer, merging blockchain and traditional worlds together.

**2. What is your goal?**
GEO is on a mission to empower Internet of Value by creating universal value transfer ecosystem 

**3. What is your product?**
The Protocol itself is our main product. We create a framework which enables businesses or developers to run their applications and ecosystems, as well as to connect to already existing networks of other applications which use different values (blockchains, local currency network etc). GEO Protocol is able to ensure secure, fast and cost-free transactions within the network. Moreover, it enables users to exchange with different cross-units (equivalents) and guarantees cyclic clearing.

**4. What problem does GEO solve?**
In the world of siloed networks competitive spirit oftentimes outweighs cooperation incentives. However, the success of any given network soon reaches its limit unless the network learns how to benefit from integration in the global ecosystem. Different value transfer networks need a universal solution that would provide a technological opportunity to interoperate, to lower the costs and to accommodate the growing number of transactions with no speed or safety sacrifices.

**5. How you differ from competitors?**
GEO is an open-source, off-chain, blockchain agnostic value transfer protocol, that places speed, cost-efficiency, safety and interoperability as its top priorities. GEO implements a different network topology than those of similar solutions, enabling advanced transaction routing, local consensus algorithm, and full transaction atomicity.

**6. How your idea is similar to the original Ryan Fuger's idea?**
As a decentralized credit network, our protocol is the truly distributed realization of Ryan Fuger’s idea.

**7. Who can use GEO?**
Any person with any device (even a mobile device in prospect) could become part of the ecosystem. However, GEO Protocol is made mainly for developers and businesses, because they could connect different applications or ecosystems which will be the part of [GEO Network.](http://geoexplorer.io/)

**8. How can I use GEO?**
If you are a developer or business owner you can use the following manual (will be published soon) to connect your application or device or server to the network. If you are a business owner -- you can read our docs about protocol advantages, but you still will need development skills to connect to the network. If you are not a developer or a business owner the only way for you to use GEO Protocol is to register or enter any application or ecosystem which is attached to the GEO Network.

**9. What would you recommend me to read first to have a birds-eye overview?**
We would recommend starting to explore the project from [this article.](https://medium.com/geoprotocol/what-hair-on-fire-problem-does-the-geo-protocol-solve-6b1a3d6a7378) Also, you should check this short [video](https://www.youtube.com/watch?v=mrDzMgdjTN0&t=3s), where chief architect of GEO Protocol, Dima Chizhevsky explains the basic components and technologies used in GEO Ecosystem.
Besides video, we also wrote an [article](https://medium.com/geoprotocol/introducing-geo-protocol-140e94ab5fba) where the concept of the Internet of Value is explained and the way GEO Protocol contribute in the development of this technology is overviewed.

Since the basic component in GEO Ecosystem is trustlines it might be useful to read this [article](https://medium.com/geoprotocol/trustlines-are-the-new-iou-5a10fde5881a) in order to understand what trustline is.

Afterward, you might be interested in the exact problem GEO solves. This [article](https://medium.com/geoprotocol/what-hair-on-fire-problem-does-the-geo-protocol-solve-6b1a3d6a7378) will help you to understand that.

Furthermore, there are also a few articles which describe the existing problems in crypto and fintech industry. This [article](https://hackernoon.com/how-off-chain-solutions-can-become-a-tcp-ip-for-the-internet-of-money-17a58922d93b) will show you how the existing finance industry is similar to the Internet in 1960th - 70th in terms of interoperability and fragmentation. And [this one](https://medium.com/geoprotocol/the-need-for-layer-3-on-the-internet-of-value-2a62f8e93160) will give you an understanding of what could be called “Layer 3 solutions”

**10. What is GEO-Pay?**
[GEO_Pay](https://geo-pay.net/) is the first production usage of our technology. It is the first service that uses GEO Protocol as the main technical framework. 

**11. Who is in your team?**
On GEO Protocol development are working 18 specialists - analytics, developers and marketers. However, our team is not yet totally formed. We seek for C++ developers, security analysts, cryptographers economists, and/or data scientists. If you are a hard-working and responsible person - feel free to write to us on jobs@geoprotocol.io.


### Technical:

**1. What technology stands behind GEO Protocol?**
GEO Protocol uses 4  main algorithms:
    
1. Topology Collection Algorithm. It creates a topology map by obtaining information about the possible connections between the sending and the receiving node as well as overall payment capacity on intermediary nodes.

2. Payment Path Building (Routing) and Maximum Flow Prediction Algorithm. Considering the topology map it calculates the maximum possible flow that may be transferred from one node to another. It also seeks for the best route through which the asset could be transferred.

3. Payment Algorithm. It is responsible for the actual transfer of funds
    
4. Cyclic Clearing algorithm. It seeks for any debt cycles and closes them
    
Another key technical feature, which we are planning to introduce in next release, is the ability to connect nodes with composite channels.


**2. What is a composite channel?**
It is a type of connection between 2 nodes when both trustlines and state channels are used. 

**3. What is a trustline?**
Trustline is a connection between 2 nodes which allows them to account and transfer values between each other. To get more information read our [article](https://medium.com/geoprotocol/trustlines-are-the-new-iou-5a10fde5881a) written by Max Demyan, or watch a [video](https://www.youtube.com/watch?v=ieZKustA2Hk) where Dima Chizhevsky explains the mechanics of trustlines.

**4. Why should I use trustlines?**
Trustlines is used to execute transactions between two independent registries. It should be noted that operations on trustlines do not necessarily change the data in registers (for example, when the registry is outside the GEO node). It records the transfer of values between them instead.

Examples:
1. Communication between two users (to account finance relations)

2. Joining the user to the hub

3. Interconnections between service providers (hubs, gateways, market makers, etc.)

4. Accounting asset equivalents (for example, in IoT).

**5. What is a state channel?**
State channel is a type of connection that allows making fast, safe and trustless offchain transactions between two accounts from common blockchain ecosystem. However, cryptoasset is backed on the channel by onchain transactions.

**6. How GEO differs from Lightning Network or Raiden Network?**
In contrast to LN and Raiden, GEO tries to be platform-independent and provides an ability to process assets of different nature: FIAT equivalents, crypto-assets, custom equivalents (for attention economy, local currencies, etc), when LN relates hard on bitcoin and Raiden on Ethereum.

Another noticeable difference is the cryptography used: GEO ecosystem goes out of use classic asymmetric cryptography (RSA/ECDSA) due to the quantum riskiness and replaces it with quantum-persistent Lamport signatures (when possible). In all other cases, GEO Protocol tries to provide configurable alternatives for the end-users to make them possible to chose some features and automatization in the face of some trade-offs present. The core functionality of the GEO Node is fully covered by the quantum-resistant crypto.

There are also great differences in low-level mechanics (routing/payments/cycles discovering) etc. 

The last but not least, GEO Protocol tries to provide a solution that would be possible to work even on a cell phone in dynamic routing networks.

**7. Why are you using non-common cryptography?**
GEO Node actively uses [Blake2B](https://blake2.net/) and built on to of it [Lamport Scheme](https://en.wikipedia.org/wiki/Lamport_signature). It also uses [ChaCha20-Poly1305](https://tools.ietf.org/html/rfc7539) for traffic encryption. All of that are well known and battle tested cryptographic solutions. 

Lamport Signatures are strong against quantum-base attacks due to their hash based nature, but in the same time are significantly larger than classic asymmetric crypto-signatures, that makes them almost unusable in public blockchains implementation, but is acceptable for the GEO Protocol mechanics (see the [Twin Spark algo specs](https://github.com/GEO-Protocol/specs-protocol/blob/master/transactions/transactions.md) for the details).

**8. Can I transfer any physical assets within the network?**
GEO Protocol enables free transfer of any assets or value in the network. Network participants can transfer both, backed asset equivalents and credit obligations (IOU). These are not physical assets, but they could be backed by custodian or state channels.

**9. How many transactions per second are supported?**
It really depends on the hardware configuration, Internet communication and speed of less powerful node of each one operation (because in each transaction are involved at least 2 nodes, and operations have sequential nature). In theory, GEO node is able to perform up to several thousands of *concurrent* operations with different nodes and on the same trustlines/channels

**10. What do you mean “concurrent operations”?**
GEO node implements the algorithm, that makes it possible to concurrently use the same trust line in many different operations, up to the moment, when the trust line capacity would be exceeded. GEO Protocol is smart enough to reserve only the part of trust line and to leave free segment for other operations, that makes it possible to keep liquidity of the network on a very high level.
