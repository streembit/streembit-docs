## Kademlia network

**Create a Kademlia network for test and development**

When do you need to execute this step and experiment with the Kademlia network?
* If you want to understand better how the Streembit Kademlia network works
* If you want to develop the UI and connect to a local Kademlia network

Do you need this for Streembit IoT module and to run the Streembit IoT module on a Raspberry PI? **No.**
If you want to run the Streembit IoT handler please skip this section and move to the "Streembit IOT Handler" section.

For test and development purposes to create a basic Kademlia network at least two nodes must exist on the network. To run multiple nodes on a computer, do the the following steps:

1) In step 1 we need to create a streembit-cli application, this will be seed No. 1, the first seed node of the Kademlia network.
The "port" of the config.json file can be default port 32321. The "host" field of the config.json file must be defined. For development purposes it should be your local IP like 192.168.xxx.xxx or even just 127.0.0.1.
The "account" field can be anything, such as "seed1".
The "seeds" field of the config is an empty array.

```json
see shell code
```
```shell
node streembit --pwd PASSWORD
// OR
node streembit --pwd=PASSWORD
```
Run the application, with

In a case you start a pm2 instance of the app you should also provide a valid password

The console and the log files should display a warning log "there are no seeds defined, the node is not connected to any seeds" which indicates there are no seeds defined.

2) In step 2, clone streembit-cli to an other directory (or copy the existing one). This will be the second seed of the Kademlia network. Set the port to 32322.
Since this is a TCP listening port it must be different than the port of seed 1 node.

```json
{
 "seeds": [
  {
      "host": "192.168.0.10",
      "port": 32321
  }
 ]
}
```
```shell
see json tab
```

Define the seeds array in the config file. The seed is the instance that is described at point No. 1. The seed config settings:

(The host is your machine's local IP so it might different than 192.168.0.10.)
Set the "account" field, it can be anything, but should be different than seed No. 1, like "seed2".

```bash
node streembit
```
```shell
see json tab
```

Run the application with

At this point seed No. 2 will try to connect to seed No. 1.
Upon successful connection you should see debug messages on the console as well as in the log files of seed No. 1. These are debug messages related to FIND_NODE Kademlia operations.
"*debug: received FIND_NODE from {'publickey': '...' }*"
The public key of the message is the public key of seed No. 2 that is logged to the console and log file during startup.
The FIND_NODE messages indicates that the Kademlia network is formed.

Once the Kademlia network is operational the Streembit UI application can connect to the network.

To run the CLI as an **IOT** node please refer to the [Software preparation](#software-preparation) found in the IOT SDK page"
