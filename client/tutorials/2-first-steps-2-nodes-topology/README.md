 
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
> sudo docker run -i -t geoprotocol/network-client-beta 172.17.0.2 # Node A

> sudo docker run -i -t geoprotocol/network-client-beta 172.17.0.3 # Node B
```

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/1.png">

  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/2.png">
</p>


Now we should ensure, that 2 containers are running in internal network:

```bash
> sudo docker network inspect bridge
```

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/3.png">
</p>

As we see, our 2 containers are running well and are allocating 2 internal IPv4 addresses: `172.17.0.2` and `172.17.0.3`. Please, pay attention which container is allocating which address. Your containers IDs are different from those in tutorial, so be patient!

**Warning:**
Please, ensure you are starting node `A` (`172.17.0.2`) first. 
Otherwise docker would assign it different address, and in this case yous should change the host parameter that is passed into the `run` command.

**Warning:**
In case if you docker environment uses different network subnet — ensure correct host parameter in `run` command.

<br/>

# Step 2: Opening communication channels

Communication channels are used by nodes to perform secure packets exchange. All trust lines operations require settled communication channel.

### Opening CC on node A

```bash
> curl -X POST "http://172.17.0.2:3000/api/v1/node/contractors/init-channel/?contractor_address=12-172.17.0.3:2000"
```

[`Open Communication Channel API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#open-communication-channel)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/4.png">
</p>

Node reports sucess as well as some additional parameters that are used for channel setup on the counterpart node: `channel_id` and `crypto_key`.

* `channel_id` — ID of the channel, that should be set up on the node `B`.
* `crypto_key` — **SECRET** key, that must be **securely sent** to the node `B`. This key will not be sent by the GEO Node through GEO Network. Please, be patient! Comprometing this key leads to traffic disclause and ability for third party to change operations flow!

</br>

### Opening CC on node B

```bash
> curl -X POST "http://172.17.0.3:3000/api/v1/node/contractors/init-channel/?contractor_address=12-172.17.0.2:2000&contractor_id=0&crypto_key=78b2e9736fbdd7b53931b998a42c1ae9f3c4caf3e1f864c93650d2167428a553" -i
```

[`Open Communication Channel API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#open-communication-channel)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/5.png">
</p>

As well as previous node, node `B` reports OK and it's internal CC details.
On this stage nodes has established secret channel for communication.

<br/>

# Step 3: Open Trust Line (A 100 -> B)

```bash
> curl -X POST "http://172.17.0.2:3000/api/v1/node/contractors/0/init-trust-line/1/" -i
```

[`Init Trust Line API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#open-trust-line-tl)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/6.png">
</p>

After this command, both nodes has an empty trust line with pre-shared public keys (1024, by default). 
Node `A` has sent it's own public keys to node `B`, and node `B` has sent it's public keys to the node `A`. You can refer to corresponding logs of the nodes (`/node/client/operations.log`) for the details about how keys exchange was done and how keys was transferred.

On this stage, the trust line is set to (Outgoing Trust Amount = 0, Incoming Trust Amount = 0, Balance = 0) on both nodes in `equivalent = 1`. We assume, that current `equivalent_id` of $ == 1. For more details, please refer to this video:

<p align="center">
  <a href="http://www.youtube.com/watch?feature=player_embedded&v=ieZKustA2Hk" target="_blank"><img src="http://img.youtube.com/vi/ieZKustA2Hk/0.jpg" 
  alt="GEO Protocol: Introduction to Trustlines by Dima Chizhevsky" width="720" height="480" border="10" /></a>
<p/>

Finaly, we need to set it equal to $100. <br/>
To be able to send even cents, we now need to open Trust Line for `$100 * 100 cents == 10000 cents`.

```bash
> curl -X PUT "http://172.17.0.2:3000/api/v1/node/contractors/0/trust-lines/1/?amount=10000" -i
```

[`Set Outgoing Trust Line API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#set-outgoing-trust-line)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/7.png">
</p>

Now we can check if Trust Line has been set correctly. <br/>
We can do the next command on node `A`:

```bash
curl -X GET "http://172.17.0.2:3000/api/v1/node/contractors/trust-lines/0/10/1/"
```

[`List Trust Lines API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#list-trust-lines)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/8.png">
</p>

And on the node `B`:

```bash
curl -X GET "http://172.17.0.3:3000/api/v1/node/contractors/trust-lines/0/10/1/"
```

[`List Trust Lines API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#list-trust-lines)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/9.png">
</p>

As we can see, both nodes are keeping valid trust line state.

<br/>

# Step 3: Payment B->A (10)

Now, when the trust line from node `A` to node `B` is open and ready to perform operations, node `B` is able to send payments to the node `A`. Let's send, for example, $50. 

First of all, let's be sure, how many assets we can transfer:

```bash
> curl -X GET "http://172.17.0.3:3000/api/v1/node/contractors/transactions/max/1/?contractor_address=12-172.17.0.2:2000"
```

[`Max Flows API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#max-flow-predicition)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/10.png">
</p>

As expected, max flow from node `B` to node `A` equals `10000`. <br/>
Now, let's send $50.

```bash
> curl -X POST "http://172.17.0.3:3000/api/v1/node/contractors/transactions/1/?contractor_address=12-172.17.0.2:2000&amount=5000"
```

[`Payment API Specs`](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http#payment)

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/2-first-steps-2-nodes-topology/resources/11.png">
</p>

