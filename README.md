![Header](https://github.com/GEO-Protocol/Documentation/blob/master/resources/repo-header.png)
<br/>
<br/>


GEO Protocol is a decentralized p2p protocol for values exchange that uses state channels and trust lines technologies and implements its own routing algorithm as well. 
This is a protocol that is able to build a global decentralized P2P network which connects different ledgers.
The protocol uses off-chain solutions that provide scalability of the network. 
Our purpose is to make value exchange as simple as sending email. 
For more information visit our [Website](https://geoprotocol.io/)

<br/>
<br/>


### Community:
[![Telegram Chat](https://github.com/Patrolavia/telegram-badge/blob/master/chat.svg)](https://t.me/geocommunity)
[![Telegram Channel](https://github.com/Patrolavia/telegram-badge/blob/master/follow.svg)](https://t.me/geoprotocol)
[![Gitter Chatl](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/GEO_Protocol/Lobby#)

* [Medium](https://medium.com/geoprotocol)                                                                                             
* [Twitter](https://twitter.com/geo_protocol)                                                                                          
* [LinkedIn](https://www.linkedin.com/company/geoprotocol/) 
* [Facebook](https://www.facebook.com/GeoProtocol/)
* [YouTube](https://www.youtube.com/c/GEOProtocol)
<br/>
<br/>

# Useful links:
* [Website](https://geoprotocol.io/) 
* [FAQ](https://github.com/GEO-Protocol/Documentation/blob/master/GEO_FAQ.md)
<br/>
<br/>

# Documentation:
* [GEO Network Client Docs and HowTo](https://github.com/GEO-Protocol/Documentation/blob/master/node.md)
<br/>
<br/>

# Specs and formal description
* [Payment algorithm specification](https://github.com/GEO-Protocol/specs-protocol/blob/master/transactions/transactions.md)           
* [Trust lines algorithm specification](https://github.com/GEO-Protocol/specs-protocol/blob/master/trust_lines/trust_lines.md)         
* [GEO Service Registry (GSR)](https://github.com/GEO-Protocol/specs-gsr/blob/master/specs/gsr.md)
* [GEO Voting Service (GVS)](https://github.com/GEO-Protocol/specs-gsr/blob/master/specs/gvs.md)
<br/>
<br/>

# Repositories
* [Network Client](https://github.com/GEO-Protocol/GEO-network-client)
* [Observer](https://github.com/GEO-Protocol/Observer)
* [C++ implementation of Lamport One Time Signature](https://github.com/GEO-Protocol/lib-crypto-lamport)
<br/>
<br/>


# Updates

**_Update 18.10.2018_** /
We uploaded C++implementation of [Lamport Signature](https://en.wikipedia.org/wiki/Lamport_signature) on top of BLAKE2b. Now you can take a look or download it by clicking [here](https://github.com/GEO-Protocol/lib-crypto-lamport). We use such cryptographic sollution in [GEO Network client](https://github.com/GEO-Protocol/GEO-network-client) and [observers chain backend](https://github.com/GEO-Protocol/gns-observers-chain-back). 

**_Update 15.10.2018_** / 
We published [specification that describes the trust lines algorithm](https://github.com/GEO-Protocol/specs-protocol/blob/master/trust_lines/trust_lines.md) which called *Twin State*.
Proposed solution provides ability for 2 participants to share common state of a trust line / channel and syncronise it with quantum resistant proof of operations performed.

**_Update 12.10.2018_** /
We published [specification for payment algorithm](https://github.com/GEO-Protocol/specs-protocol/blob/master/transactions/transactions.md) which called *Twin Spark*.
Proposed solution provides ability for up to several hundreds participants to achieve 100% consensus via communications through potentially unstable and untrusted environment, under active fraud attempts of malicious participants.

### Specifications in progress:
**_Current section contain steps of further GEO Protocol develpment. Sorted by priority_**
1. *Completion of documentation related to payments*;
2. *Overview of used cryptographic solutions*;
3. *Tokenomy* (economic model, tokens circulation);
4. *Observers* (functions, connections, edge cases everview etc);
5. *Trust lines* (finalization);
6. *Ping/Pong* (the mechanism of notifications within the Protocol);
7. *Routing* (algorithm description, calculations);
8. *Cycles*

