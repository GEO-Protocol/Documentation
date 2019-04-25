## Node communication
There are 3 possible ways to communicate to the GEO node:
1. [**Via low-level GEO Node protocol**](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-commands) <br/>
This is the most performant and the most flexible way of communication, but in the same time, the most complex one.
This communication channel should be used in production environments or embedded systems 
with maximum performance in mind, and to avoid addtional resource consupting layers of communication (for example, HTTP API).

1. **Via command-line interface** [comming soon] <br/> 
This interface provides ability to communicate with node from the console in mode "one command at a time". </br>
It is useful during development, but it should not be considered to be used in production environments, 
due to the limitations of concurent commands processing, and relatively high resouce usage per command execution.

1. [**Via JSON API**](https://github.com/GEO-Protocol/Documentation/tree/master/client/api-http) <br/>
This interface provides ability to communicate with node via HTTP API and to process more than one command at a time. 
It is useful during development, and also might be considered to be used in production environments, 
that are configured for communication with only one, or several nodes.
