## Fields:**

Account: This is the account name stored in the local SQLITE database. The Streembit UI identifies this node by this account name

Password: To decrypt account information in the SQLITE database. For development purpose and make easy to develop the software define this password in the config file. In production, provide this password from the command line using the --pasword (or -s) command line switch. See "node streembit.js --help" for more command line arguments.

The "**database_name**" field: This is the SQLITE database name. Default value is "*streembitsql*". You may change it for production or for testing purpose. For using different databases in production or testing.

When the "**cmdinput**" field is true the application can recieve commands via the terminal. Also, when the "cmdinput" field is true the terminal logs are disabled and only file based log is enabled.

The "**transport**" field:

`protocol`: default value is "*http*".

`host`: IP address or domain name for the HTTP listener.
For seed node: Since The Kademlia contact is the composite of IP address and port, if the application run as a Kademlia seed node this field is required and must be an IP address.

`port`: Port for the http listener. Default value is 32321

`ws.port`: Port for the websocket listener. Default value is 32318.

`seeds`: Array of Streembit Kademlia seed nodes.

```json
[
    {
        "host": "192.168.0.10",
        "port": 32322
    }
]
```
The format is

The host and port where the seed node listen for connections.

The "**limits**" section of the configuration determines time interval values of various KAD operations.<br />
"Limits" intervals (values are in seconds):

`refresh`: Interval for performing router refresh, Default value is 3600

`replicate`: Interval for replicating local data, Default value is 3600

`republish`: Interval for republishing data, Default value is 86400

`expire`: Interval for expiring local data entries, Default value is 86405

`timeout`: Time to wait for RPC response, Default value is 5

**Modules**:
This section defines how the application will be executed. Whether it is seed, client, IoT node or a blockchain node.
The "*run*" flag of each module defines whether or not execute the module.
Both "seed" and "client" cannot be defined, it must be either "seed" or "client".

The role of the DNS module is to manage dynamic DNS updates for the domain name based host field. The DNS module defines the parameters of a dynamic DNS service. This module is used in case if you define a domain name at the transport.host field and network router uses DHCP.
Using DHCP the DNS A record of the doomain name (host) must be updated upon the start of this CLI application. By default the application uses *srv.streembit.net:8080*. Most CLI will define a static IP address at the host field.
**In case if an IP address is defined at the transport.host field then you must remove the DNS module from the configuration file.**

**log**: logger settings.
