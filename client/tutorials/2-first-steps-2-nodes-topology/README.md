 
# First steps
### How to perform simple TL operations and payments

<br/>
<br/>

All operations in GEO Network are performed through the trust lines. <br/>
In this tutorial we would run 2 nodes in common network, connect them with a trust line, and perform several payment operations.

<br/>

## Nodes toplogy

The overall topology we are going to create looks like this:

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/topology.png">
</p>

In this topology, node `A` trusts node `B` **$100**, so node `B` is able to pay to node `A` up to $100. <br/>
In the same time, node `A` is not able to pay to node `B` because node `B` does not trust to the node `A`.

<br/>

## Step 1: Topology creation

Now we are going to launch the nodes into docker's internal network. <br/>
Please, refer to the [first tutorial](https://github.com/GEO-Protocol/Documentation/tree/master/client/tutorials/1-docker-initialisation) for the details how to run the container with a node.

Please, open 2 terminals and perform the next commands in each one:

```bash
> sudo docker run -i -t geoprotocol/network-client-beta 172.17.0.2

> sudo docker run -i -t geoprotocol/network-client-beta 172.17.0.3
```

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/1.png">

  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/2.png">
</p>
