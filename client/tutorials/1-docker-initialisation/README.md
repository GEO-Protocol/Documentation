

# How to setup docker image of GEO Node

This tutorial provides step-by-step instructions for installing GEO Node from docker hub.
Please, follow it carefully because this instructions are used as a base phase for all other tutorials provided.

<br/>

# Step 1: Installing docker
First of all, you should install docker on your host machine.
Usually it is provided as OS package for most popular Linux Distributions.
Here are several useful links, that might be helpful in case if your host OS is Linux:

* [How To Install and Use Docker on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)
* [Get Docker CE for CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)
* [Get Docker CE for Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)

<br/>

In case if your host OS is Windows:
* [Install Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/)

<br/>

In case if your host OS is MacOS:
* [Install Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/index.html)

<br/>

# Step 2: Pulling the image
At the moment of writing this docs, only BETA release of GEO Node is available in docker hub.

```bash
> sudo docker image pull geoprotocol/network-client-beta
```

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/1-docker-initialisation/resources/1.png">
</p>

In our case the image is already pulled so docker will only checks it and reports success.
In your case, it is most probable, that docker would pull sevaral images and will build the final one, but the final result would be the same.

Current image contains configured node and it's HTTP API wrapper, so no additional configuration is needed.

**Please, note: your docker conf. might not require using sudo!**

For Windows/Mac instructions please, refer to the [docker documentation](https://docs.docker.com/).

<br/>

# Step 3: Running the container

```bash
> sudo docker run -i -t geoprotocol/network-client-beta 0.0.0.0
```

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/1-docker-initialisation/resources/2.png">
</p>

**Please, note the last paramter: `0.0.0.0`!** <br/>
This argument specififes the interface on which the node should be available. <br/>
You should specify this parameter in accordance to your internal network topology. <br/>
The recommended value for this parameter is `172.17.0.0` if you are planning to run the node in docker's internal network.

In case if there is no host address specififed - the entrypoint script would report an error.

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/1-docker-initialisation/resources/3.png">
</p>

<br/>

# Step 4: Internal container structure

After successfull container launching, the bash session is launched for the development purposes.
You can use this session to examine internal container filesystem, change some configurations, accessing node's logs, etc.

The node itself aswell as it's HTTP API wrapper is located in `/node/` volume.

The node's logs are located under `/node/client/`.

<p align="center">
  <img src="https://github.com/GEO-Protocol/Documentation/blob/master/client/tutorials/1-docker-initialisation/resources/5.png">
</p>

* `/node/entrypoint.sh` — [script](https://github.com/GEO-Protocol/docker-client/blob/master/node/entrypoint.sh) that initializes the container.
* `/node/interface` — CLI / [HTTP API](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http) Interface ([repo](https://github.com/GEO-Protocol/GEO-node-CLI)).
* `/node/operations.log` — log of HTTP API Interface.

<br/>

* `/node/client/conf.json` — configuration of the node.
* `/node/client/client` — network client executable.
* `/node/client/operations.log` — network client's log.
* `/node/client/fifo/` — directory with FIFO files used to transfer commands and receive responses.
* `/node/client/io/` — directory with internal node's data files.
* `/node/client/pid` — PID-file. Present only if node was launched at least once.
