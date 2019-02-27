
# GEO Network Client documentation
<br/>
<br/>

# How to run
### Installation
1. Download/Build last node version from the [repo](https://github.com/GEO-Protocol/GEO-network-client); <br/>
You can follow the links provided in [releases changelogs](https://github.com/GEO-Protocol/GEO-network-client/blob/develop/RELEASES.md) to get desired version of the node build.

1. Move `geo_network_client` to the desired FS location. <br/>
The default location for the node in provided WM images is `~/node/`, but you are free to chose any other location.

1. Prepeare the configuration. <br/>
Please, follow instructions from a section "Configuration".

1. Start the node: `./geo_network_client` <br/>
In case of successfull fly node should report core and required subsystems initialisation and observers current block.

### Configuration
Configuration contains network interfaces that should be used by the node and reported to the rest of the network, 
as well as addresses of the observers, that are expected to be present in the network.

**Note: Beta 1 release supports only static, publicly available IPv4 addresses.** <br/>
So, in case if you are planning to try to launch several nodes and perform some operations between them, - 
please, ensure, that all of them would be able to communicate to each other via `UDP/IPv4` interface.

**Note: Beta 1 release supports only statically listed observers list** <br/>
The protocol itself is expected to support dynamically formed observers list, provided by the GSR [#todo link to GSR description].
</br>
</br>

Configuration file is named `conf.json`. <br/> 
It is required to be located on the same FS level as an executional file. </br>
Example configuration for the BETA 1 Test net. is the next:

```
{
  "addresses":
  [
    {
      "type":"ipv4",
      "address":"127.0.0.1:2000"
    }
  ],
	"observers":
  [
    {
      "address":"68.183.146.232:4000",
      "type":"ipv4"
    },													
    {
      "address":"46.101.51.158:4000",
      "type":"ipv4"
    },
    {
      "address":"206.189.84.116:4000",
      "type":"ipv4"
    },
    {
      "address":"159.89.115.33:4000",
      "type":"ipv4"
    }
  ]
}
```
</br>
</br>

# How to read command results
1. Move to the node directory: `cd ~/node` </br>
1. Open `./fifo/results.fifo` for reading via, for example, `cat` </br> 
`cat ./fifo/results.fifo` </br>
1. Start the node: `./geo_network_client` </br>
</br>
</br>

# How to use the node
## Network topology
Node represents _an account_ in GEO Network. <br/>
_It is assumed, each one participant of the GEO Network would access the network via it's own node_. <br/>
In contrast to some other decentralized networks, GEO Network does not delegate calculations to the miners, 
but assumes network participants would take part (only) in transactions, in which them are involved.

GEO Network Client implements such a node and provides low-level API 
for operations processing: assets transfers, trust-lines/channels accounting, etc.
</br>
</br>

## Node communication
There are 3 possible ways to communicate to the GEO node:
1. **Via low-level GEO Node protocol** <br/>
This is the most performant and the most flexible way of communication, but in the same time, the most complex one.
This communication channel should be used in production environments or embedded systems 
with maximum performance in mind, and to avoid addtional resource consupting layers of communication (for example, HTTP API).

1. **Via command-line interface** [comming soon] <br/> 
This interface provides ability to communicate with node from the console in mode "one command at a time". </br>
It is useful during development, but it should not be considered to be used in production environments, 
due to the limitations of concurent commands processing, and relatively high resouce usage per command execution.

1. **Via JSON API** [comming soon] <br/>
This interface provides ability to communicate with node via HTTP API and to process more than one command at a time. 
It is useful during development, and also might be considered to be used in production environments, 
that are configured for communication with only one, or several nodes.
