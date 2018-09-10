## Blockchain Client

No special configuration required to run streembit-cli in "Blockchain Client" mode. All it takes to execute blockchain
command is to properly write such a command in console/terminal.
If you familiar with **Bitcoin**'s native *bitcoin-cli* command line application you have an idea on how the client is working.
it sends one command at a time to the streembit-cli application running in **Blockchain Node** mode.
**Blockchain Node** in turn processes this command and sends back output that will be displayed on the client's side

```json
        'addmultisigaddress',
        'backupwallet',
        'createrawtransaction',
        'decoderawtransaction',
        'dumpprivkey',
        'dumpwallet',
        'encryptwallet',
        'getaccount',
        'getaccountaddress',
        'getaddressesbyaccount',
        'getbalance',
        'getblock',
        'getblockcount',
        'getblockhash',
        'getinfo',
        'getnewaddress',
        'getrawtransaction',
        'getreceivedbyaccount',
        'getreceivedbyaddress',
        'gettransaction',
        'gettxout',
        'importprivkey',
        'listaccounts',
        'listreceivedbyaccount',
        'listreceivedbyaddress',
        'listsinceblock',
        'listtransactions',
        'listunspent',
        'listlockunspent',
        'lockunspent',
        'sendfrom',
        'sendmany',
        'sendrawtransaction',
        'sendtoaddress',
        'setaccount',
        'settxfee',
        'signmessage',
        'signrawtransaction',
        'submitblock',
        'validateaddress',
        'verifymessage'
```
```shell
node streembit --rpcuser=youruser --rpcpassword=yourpassword COMMAND PARAM1 PARAM2 ...
```

Here in the json tab you can see the list of commands currently supported by streembit-cli running in **Blockchain Client** mode.

Shell tab to the right contains a template that you can use to compile a valid blockchain command

You must include **--rpcuser** and **--rpcpassword** flags and values of these must be equal to the corresponding ones
defined on Blockchain node side.

We consider default Blockchain node's port to be 32319. If you have your node running on different port, then please
use **--rpcport** flag that will provide the client with the correct port number.

All these RPC related flags are followed by a **command** and parameters if the command requires the parameters.



```json
see shell tab
```
```shell
node streembit --rpcuser=youruser --rpcpassword=yourpassword help
```

You can also see a short *help* by entering

Please, notice that running streembit-cli in Blockchain Client mode does not require **--pwd** flag (so, password)
