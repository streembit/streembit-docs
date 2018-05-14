## Setup and configuration

### Create account

Human users and Internet of Things devices are identified by their account name on the Streembit network.

Click on the "New Account" button from the start screen.

Enter the account name. You will receive an error message if the account exists on the network. The account name must be between 6-20 characters and it can only contain alphanumeric characters (letters a-z, A-Z and numbers 0-9)

Enter the password key pair encryption password. Based on the password, the system generates a 256-bit AES key using PBKDF2 with a randomly generated 160-bit salt. The system protects the ECC public key pair with the 256-bit AES key. The password must be at least 8 characters, must not contain empty space, must contain at least one letter, one digit and one special character.


![alt text](./images/streembit/createaccount.png "Create account on Streembit.co")

### How to add contact?

Click on Contacts/Add contact in the menu bar, put the contact offer in the text box and click on the "Add/Update Contact" button.

![alt text](./images/streembit/addcontact.png "Add contact on Streembit.co")

### What is a contact offer?

Creating contact offer you encode your public key, connection details, account name. Then you can send this text to whom you want to communicate with. Click on "Contact/Create offline contact offer" in the menu bar. Clicking on "Copy clipboard" button you copy your contact offer and can use it.

![alt text](./images/streembit/contactoffer.png "Contact offer on Streembit.co")

### My contacts

If you want to see your contacts you can click on Contacts/My contacts on the menu bar or you can click on the “Contact List” button in the top right side of the page.

![alt text](./images/streembit/contactlist1.png "Contact list notifications")

Clicking on any contact in the contact bar will open the "Contact details" view, which will allow you to have a chat, video or audio call by clicking on corresponding button.

![alt text](./images/streembit/contactdetails.png "Contact actions on Streembit.co")

### IOT Devices

IOT devices are nonstandard computing devices that connect wirelessly to a network and have the ability to transmit data.

Streembit allows IoT application providers and context producers to register their IoT Objects on the decentralised Streembit network, and in turn allow context consumers to discover them in a secure and peer to peer manner.

![alt text](./images/streembit/device.png "Add device on Streembit.co")

### Add IOT Hub and My Devices

If you want to add the device click on IOT Devices/Create IoT Hub on the menu bar and fill in all required fields.

If you want to see your devices click on IOT Devices/My devices on the menu bar.

![alt text](./images/streembit/createdevices.png "Create device")

### Backup account

You can perform an account backup to save a local copy of your Streembit account data. The Streembit account can be restored from a backup using the “Restore account” function.

In order to backup the account the account must be initialized. Click on the Actions/Backup account on the menu bar to start backup your account.

Your account backup data is never saved on a central server by the Streembit application and the account backup file is saved to your Download directory.

__What is saved in the Backup file?__
The backup file contains your encrypted Streembit ECC public/private key pair. The backup data is base64 encoded. It starts with “---BEGIN Streembit KEY---“, and the file ends with “---END Streembit KEY---“

![alt text](./images/streembit/backup.png "Backup file")

### Restore account from backup file

**Why restore your account data?**
Your contacts identify your account and validate your identity using your PPK public key. The public/private key pair is created using a random entropy - once it is created then it cannot be changed. The public/private key pair isn’t deterministic and in order to communicate with your contacts, you must use the same public key which was published to the Streembit network and known to your contacts. The published public key can be restored from an account backup file.

You can restore your Streembit account data on any computer from a backup file.

Click on the Actions/Restore account on the menu bar or the Restore account to start restoring the account from a backup file.

### Streembit settings

Click on the Tools/Settings menu item to open the Settings screen.

__Network tab__
**TCP port:** Use this TCP port to communicate on the Streembit network. Port forwarding or the UPNP settings of your router must grant access to this port in order to send and receive data. If the transport is WebSocket (WS) then this settings is not used by the application.
**WebSocket port:** If the TCP port is not available then the connect to the WebSocket listener must listen on this port.
**Transport:** Transport protocol. The default is TCP. Select the WebSocket transport if the incoming TCP traffic is blocked by your router or firewall. If the WebSocket transport then make sure the WebSocket listener seed node is operational.
**Use WebSocket fallback:** Many firewalls and home network routers block incoming TCP communication and this is a fallback solution for users who are unable to use the TCP protocol. By enabling this configuration option the system will try to communicate on the WebSocket protocol when the generic TCP communication is blocked. Please note, WebSocket listeners run by community peers and the availability of WebSocket listeners is limited on the network. Try to run your own seed to support the network and Streembit community, and ensure the WebSocket listeners is available! Also, make sure the WebSocket listener is enabled in the seed nodes if you run a private Streembit network!

__Seeds tab__
**List of seed nodes:** The seed nodes assist in user and device discovery, and stores the users’ public key data in their distributed hash table (DHT) storage. Also, you can define here your seed nodes if you run a private Streembit network.

__Ice resolvers tab__
Complete decentralization is not possible in Internet communication. All decentralized systems like Bitcoin or Telehash must use some internet services for certain tasks. For instance, decentralized systems use DNS servers and services to resolve domain names. WebRTC video and audio chats clients use ICE servers to get information about their own IP address.

__Private network tab__
**Seed account, Seed port, Seed IP/domain name:** If the Seed account, Seed port and IP/domain name are defined then the software operates in private network mode. Please note, the seed node must be configured to run as a private network node as well. Remove these configuration settings if you want to connect to the public Streembit network.

__System tab__
**Log level:** Defines the log level. Debug: most detailed logging. Info: only important system events logged. Error: only application errors logged.
**Developer mode:** Software developers should select this option to resolve directories and develop the software from IDE such as Visual Studio.

### Account/Network info

If you want to see your account/network information click on the "Tools” in the menu bar and click “Account/Network info.

When you in the "Account/Network info" view you can see that the Private key and Mnemonic phrase are private. It means you should enter your password and after it, you can see your private key and mnemonic phrase. For it click on the "eye" icon next to these fields and enter your password.

![alt text](./images/streembit/accountnetwork.png "Account and network info")

### Log files

Your Streembit system provides vital information using an application log file. The log file is JSON file format and sits in the application /log directory. You can also open the log file by clicking on the "Tools/View Logs" in the menu bar. Configure the log to “Debug” log level to populate detailed debug messages from the application.

![alt text](./images/streembit/viewlogs.png "View application logs")

### Clear database

It is essential to clear the database if you are using Streembit on a public computer, for example in an internet café or airport.

You can remove all Streembit data from the computer by clicking on the "Tools/Clear database" in the menu bar. Once the deletion is confirmed all settings and data will be removed from the local database. Make sure you made a backup if you want to keep using your account.

![alt text](./images/streembit/cleardatabase.png "Clear DataBase")
