## Software Preparation

Follow the instructions to set up the CLI so that it can communicate securely with [https://www.streembit.co/](https://www.streembit.co/)  the user interface for IOT. It is important to understand that in order for the communication to function with the UI at the secure website of [https://www.streembit.co/](https://www.streembit.co/) we need to apply the SSL certificates into the root directory of the CLI and also make sure that the domain linked to the certificates is accurately referenced in the SSL module on the Config file.

Users control IoT end devices using the Streembit User Interface (UI) application and the IoT gateway. The IoT gateway acts as a bridge between the UI and the IoT end devices. That means the IoT gateway must provide an interface for incoming IoT requests. We do this via either the HTTP or HTTPS transport protocols, and the gateway listens for incoming connections using either HTTP or HTTPS.

**When should I use the HTTPS protocol?**
Currently, modern browsers increasingly enforce HTTPS. Many browser functionalities available only via the HTTPS protocol. HTTPS on the UI side means that the IoT Gateway must use a domain name and third-party SSL certificate (modern browsers don't support self-signed SSL certificates). Seeing the current trends, we feel the Gateway must support HTTPS connections. Also, many businesses and government organisations IT & security policies requires to use SSL certificates. We aim to enable the gateway to operations where the security policies requires SSL certificates.

**What are the requirements for the HTTPS configuration?**
HTTPS requires a domain name and a third party signed SSL certificate.

**Can I run the Gateway without a domain name and SSL certificate?**
Yes, the gateway can be configured using the HTTP protocol without an SSL certificate. We understand many home users cannot manage domain names and SSL certificates. Also, domain names and SSL certificates introduce an additional level of dependency on registrars and DNS service providers. Streembit aims to create a peer-to-peer connection between users and IoT devices. Relying on domain name registrars and DNS providers contradicts the P2P idea to a certain extent.

**Does the HTTP connection and lack of SSL certificate compromise security?**
It is not. The IoT Gateway is configured with a unique PKI key pair. The UI user must know and configure the Gateway on the UI using the unique public key of the gateway. The identity of the gateway is verified via the PKI public key. Therefore the lack of SSL certificate do not compromise security.
All transport packets are end-to-end encrypted on Streembit using PKI based ECDH or symmetric cryptoraphy. The symmetric end-to-end encryption is AES256 and it uses 512-bit strong cryptography keys. Using the combination of PKI Network sniffers or third party observers/intruders unable to decipher the end-to-end encrypted messages. Using tested, robust and strong cryprography methods we can achieve military grade security on a home IoT network without SSL certificates.

**So which configuration options should I use HTTP or HTTPS?**
It is entirely depending on the user policies, preferences and capabilities. Both options can secure IoT devices adequatelly.

*Options #1 and #2 of “step 1” below describe each configuration.*

In “step 3” you will notice this command
`$ node streembit --pwd=PASSWORD`
You may notice that instead of PASSWORD you will need to create your own password which is compliant in length and has upper, lower case letters and a number at least.

Adding the user public key from your account at [https://www.streembit.co/](https://www.streembit.co/) requires to follow the `user`  `add`  detailed in step 3 below.

```json
# having CMD set to true
{
  "database_name": "streembit",
  "cmdinput": true,
  "seeds": [
    {
      "host": "seed.streembit.uk",
      "port": 32319
    }
  ]
...
```
```shell
see json tab
```

JSON code to the right shows the config file - which needs the  CMD set to true before running streembit cli on the raspberry pi to allow you to enter commands such as adding a user.

<aside class="notice">
You can also use `--cmd` flag in command line. the app started this way (so, `$ node streembit --pwd=PASSWORD --cmd`) will always bring up command line interface, independently of value of the "cmdinput" flag
</aside>

*Fig 1*. - Shows the UI view showing the public key which is needed to set up the user account on the CLI.  The Public key is a long string of characters - in Fig 2 below it starts with 049085a5

![alt text](./images/ui_pub_key.png "Public key on UI")

Follow the instructions carefully on step 4.

*Fig 2*. - Once you have got the relevant data you can then set up the IOT hub at UI [https://www.streembit.co/](https://www.streembit.co/)

![alt text](./images/iot_hub.png "Setup IoT Hub on UI")

<aside class="notice">
**Points of note in the config file**
The config file is the most likely source of any issues preventing the creation of the Peer to Peer secure Streembit IOT network. Incorrect setting of the flags ***true/false*** or typo’s in the syntax will prevent the application either running or connecting.
</aside>

Below are some guidance notes on how to view and interpret the elements of the Config file and the consequences of inputting this data incorrectly.

### Setting the flags

JSON you see to the right shows how we are setting the flags

```json
...
{
           "name": "iot",
           "run": true,
           "serialport": "/dev/ttySO",
...
```
```shell
see json tab
```

Making sure the IOT module detailed above needs to be set to true on the config file.  Also the “serialport” needs to match the naming convention of the Raspberry Pi serial port, which is listed above.  On certain config file examples you may see it listed as “com 3”  which is correct syntax for windows machines

The other modules in the config file then need to be set to false except for the following

    * SSL = true
    * Client = true
    * NFC = true
    * Dns = true

### Setting the mac address of the Zovolt Board

The config file requires the personalization of the *Zovolt expansion board / Hat* which is connected to the Pi via the usual serial block connector. This is done through the use of the *mac* address of the board and linked to the Zigbee radio chip on the board.

```json
...
"devices": [
               {
                   "type": 1,
                   "protocol": "zigbee",
                   "mcu": "xbee",
                   "id": "MAC_ID",
                   "name": "My Hub",
                   "permission": 1,
                   "details": {
                       "manufacturername": "ZoVolt",
                       "modelidentifier": "ZOVOLT-P2PIOTHUB-01",
                       "hwversion": "0001",
                       "protocol": "Zigbee",
                       "security": "ECC PPKI",
                       "NFC": true,
                       "endpoint": 2
                   }
               }
           ]
...
```
```shell
see json tab
```

JSON you see to the right shows an example on the IOT module of the config is shown below

![alt text](./images/iot_module.png "Example of IoT module")

The key data item which need’s modifying on this config file for your specific board is

**“Id” : “0013a20041679c00”**,

The long string is the mac address of the board.
Key to this information is to use lower case letters when editing the file. We find that despite the labels using upper case letters, the code relating to these identifiers for the mac address of the chip/board is most often lower case lettering.  - creating a mismatch in upper and lower case lettering can create additional bugs and unpredictable operation of the CLI application.

### Step 1

*Option 1. With a domain and SSL certificates, via HTTPS.*
---

The connection between the UI and the gateway are WSS and HTTPS. Therefore SSL certificates must be deployed and configured on the gateway. The configuration must be saved in the config.json file.

First obtain an SSL certificate for your domain name from a third party certificate provider. Include the certificate files in the ssl folder.

**Required files**

 - CA: ssl/DOMAIN.ca-bundle.crt
 - Certificate: ssl/DOMAIN.crt
 - Key: ssl/DOMAIN.key

Adjust corresponding section in the configuration file to look like this:
```json
"transport": {
...
	"ssl": true,
	"ca": "ssl/DOMAIN.ca-bundle.crt",
    "cert": "ssl/DOMAIN.crt",
    "key": "ssl/DOMAIN.key"
}
```

*Option 2. Without SSL, via HTTP*

The transport section in config.json file must be configured the following:
```json
"transport": {
...
	"ssl": false
}
```

### Step 2

Make sure you modify your *config.json* to resemble example above

For IoT the node: the *transport.host* field can be one of the following:

   - IP address - type the valid public static IP address of your device. The Streembit UI will try to connect to the IoT node via this static public IP address.
   - Domain name - type a domain name which DNS services is configured. The Streembit UI will connect to the IoT node via this domain name.
   - "" - empty string. By configuring the device with this option and define an empty string i.e "", the application will try to resolve the external (public) IP address of the device. The Streembit UI will connect to the IoT node via this resolved public IP address.

Notice that we are using domain names instead of IP addresses for the ssl cert configuration. This is important. Also there must be at least one valid seed, as well as run value in Client and IOT modules set to "*true*".
Please also note that the mac address listed in this config file is an example. You will need to use the mac address which is defined on the Zovolt board ‘Zigbee’ Radio chip.

### Step 3

```json
see shell tab
```
```shell
# Start the app by entering
$ node streembit --pwd=PASSWORD
# or
$ node streembit --pwd=PASSWORD --cmd

# corresponding to a chosen way of initialization
# next, Enter
user
# then
add

# ... and follow the prompts you see on a screen
```

To allow connection to this IoT CLI instance, a user must be defined and saved in the CLI local database.
In order to do this, open your Streembit UI, open "Tools" > "Account/network info" and copy the public key value.
At the CLI to allow command prompt input set the "cmdinput" parameter to "true" or use "--cmd" flag.

<aside class="notice">
Public key is the only mandatory field and you should fill it with your PKI public key of your account set up which was copied from the Streembit UI.
</aside>

### Step 4

```json
see shell tab
```
```shell
# Restart the app with the following command
$ node streembit --pwd=PASSWORD --data
```

Once the user is successfully added, stop the cli app. Open config.json and change "cmdinput" to false.

Copy the value of the *BS58 public key* of the hub (must be the last string of the output, or close to the last).
At the Streembit UI you must add this Hub to your IoT Hub list. Click on the "IoT Devices" menu item and click on "Create IoT Hub". Enter the IoT device ID. This is usually the Zigbee MAC of your device that sits top on the Streembit-cli Raspberry Pi (such as the Zovolt Zigbee gateway). Enter the device name and copy the BS58 public key of the streembit-cli that you gathered in the previous step. Click on Save and the web application should connect to your streembit-cli IoT instance.
The created IoT Hub should appear on the devices view that is accessible from the "My devices" link.

```json
# Sample config file
{
   "database_name": "dbsql",
   "cmdinput": false,
   "seeds": [
		{
            "host": "seed.domain.se",
            "port": 32319
        }
   ],
   "transport": {
        "protocol": "http",
        "host": "",
        "port": 32319,
        "ws": {
            "port": 32320
        },
        "ssl": false,
        "ca": "PATH_TO/DOMAIN.ca-bundle.crt",
        "cert": "PATH_TO/DOMAIN.crt",
        "key": "PATH_TO/DOMAIN.key"
   },
   "limits": {
        "refresh": 3600,
        "replicate": 3600,
        "republish": 86400,
        "expire": 86405,
        "timeout": 5
   },
   "modules": [
       {
           "name": "seed",
           "run": false
       },
       {
           "name": "client",
           "run": true
       },
       {
           "name": "blockchain",
           "run": false
       },
       {
           "name": "iot",
           "run": true,
           "serialport": "/dev/ttySO",
           "protocols": [
               {
                   "name": "zigbee",
                   "chipset": "xbee"
               },
               {
                   "name": "zwave"
               },
               {
                   "name": "6lowpan"
               }
           ],
           "devices": [
               {
                   "type": 1,
                   "protocol": "zigbee",
                   "mcu": "xbee",
                   "id": "MAC_ID",
                   "name": "My Hub",
                   "permission": 1,
                   "details": {
                       "manufacturername": "ZoVolt",
                       "modelidentifier": "ZOVOLT-P2PIOTHUB-01",
                       "hwversion": "0001",
                       "protocol": "Zigbee",
                       "security": "ECC PPKI",
                       "NFC": true,
                       "endpoint": 2
                   }
               }
           ]
       },
       {
           "name": "dns",
           "run": true,
           "host": "IP_ADDRESS",
           "port": 8080
       }
   ],
   "log": {
       "level": "debug",
       "logs_dir": "logs"
   }
}
```
```shell
see json tab
```
