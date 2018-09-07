## Blockchain Client

No special configuration required to run streembit-cli in "Blockchain Client" mode. All it take to execute blockchain
command is to properly compile such a command in command line. If you familiar with **Bitcoin**'s native *bitcoin-cli*
command line application you have an idea on how the client is working.
It executes one command at a time and displays output if the **Blockchain Server** sent such.

```json
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
see json tab
```

Here is the list of commands currently supported by streembit-cli running in Blockchain Client mode:

And the shell tab to the right contains and example usage of a command.
You must include **--rpcuser** and **--rpcpassword** flags and values of these must be equal to the corresponding ones
defined on server side.
We consider default Blockchain server port to be 32319. If you have your server running on different port, then please
use **--rpcport** flag that will provide the client with the correct port number.
All these RPC related flags are followed by a **command** and parameters if the command requires the parameters.

```json
node streembit --rpcuser=youruser --rpcpassword=yourpassword help
```
```shell
see json tab
```

You can also see a short *help* by entering:

Please, notice that running streembit-cli in Blockchain Client mode does not require **--pwd** flag (so, password)
