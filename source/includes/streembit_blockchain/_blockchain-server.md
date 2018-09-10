## Blockchain Node

This is a part of streembit-cli application that listens for and processes messages from **Blockchain Client**.

```json
{
  "name": "blockchain",
  "run": true,
  "rpcuser": "bctest",
  "rpcpassword": "qawsed",
  "rpcallowip": [
     "127.0.0.1"
  ]
}
```
```shell
see json tab
```

To activate this mode you need to edit your configuration file. Refer to modules section
and then down to blockchain module. Turn run value to be "true" and add the following "*key:value*"
pairs to this section (see the example in json tab to the right).

Where,
*rpcuser* - username that will be compared to the corresponding values in a request from Blockchain client
*rpcpassword* - password that will be compared to the corresponding values in a request from Blockchain client  
*rpcallowip* - this is a list of IP address that we will consider as clients with with request privileges granted
