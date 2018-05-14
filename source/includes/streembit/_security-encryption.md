## Security and Encryption

### Streembit security implementation and design summary

The cornerstone of Streembit security is elliptic curve public/private key cryptography infrastructure (PPKI). PPKI allows the implementation of robust security. We use PPKI to identify the entities of the system (based on their public key and PPKI signature), perform authentication, and ensure data integrity (using cryptography signatures). Using the public/private key cryptography infrastructure paves the way for the deployment of a robust, secure authentication and access control scheme. The parties are identified by their public key. The authenticity of messages and the identities of the actors are then verified using PPKI cryptography routines. Using a PPKI infrastructure based security scheme greatly simplifies the authentication, access control, and identity management aspects of Internet-of-Things security.

The basic premises of the Streembit security are…

  - Human users and Internet of Things devices use public/private key (PPK) infrastructure and PPK cryptography functions to secure messages
  - Each actor of the system must generate a public/private key pair. (Typically keys are generated prior to configuring the device and will be burned into the devices’ firmware).
  - The device or user publishes the public key to other users of the system.
  - The data integrity and authenticity of the messages is guaranteed with PPK signatures.
  - Each session between users is secured with strong symmetric cryptography keys.
  - All messages between users are secured with 128-bit and 256-bit AES symmetric encryption/decryption.
  - The system uses elliptic curve Diffie Hellman (ECDH) key exchange algorithms to facilitate the exchange of session keys.

### Protecting the ECC public/private key pair

The ultimate issue of all applications, systems, and devices that protect data with cryptography is the security of the symmetric key of the encryption or the private key of the public/private key pair. Similarly to the iPhone and PGP, which both use passcode to protect their keys, Streembit requires users have a passcode to protect their PPKI private key. The Streembit passcode that protects the user’s PPK key pair is relatively complex.

To protect real time communication, Streembit uses a randomly generated 256-bit AES session key and exchanged between peers with a randomly generated ECDH key pair. This means that real time communication, which is the main functionality of Streembit, is secure even from the brute force attacks of NSA super computers and large zombie computer clusters of cyber criminals.

### Mitigate the risk of Sybil attacks

A known issue with regards to peer-to-peer (P2P) networks and their practical limitation is that they are frequently subject to Sybil attacks. This means that malicious parties can compromise the network by generating and controlling large numbers of shadow identities. A malicious node may present multiple fake identities to a peer-to-peer network in order to appear and function as several distinct nodes.

A Sybil attack is most effective on anonymous and reputation systems where if the malicious nodes outnumber the honest nodes the outcome of the application could be compromised. For example, on a file sharing network a successful horizontal Sybil attack allows the attacker to sniff most of the control messages, hijack the system, and deliver bogus content. Contrarily, Streembit facilitates communication between contacts that you know, such as your family members, teammates, and business partners. You are also aware of the location and identity of your Internet of Things device(s) you control via Streembit, lessening the likelihood of a Sybil attack. Malicious nodes, regardless of their weight and presence on the network, are unable to change the public keys of your contacts (as the public key is based on the cryptographically secured PPK infrastructure).

Additionally, Streembit introduces another layer of security, private networks. Using private networks, the public keys of the contacts are loaded to the seed nodes manually; mitigating further the risk of a Sybil attack as well as a Man-in-the-middle attack (MITM). A Sybil attack, which generally speaking is a serious security issue for P2P networks such as file sharing applications, is much less of a problem for the Streembit P2P system.

### How secure the cryptography of Streembit?

Both 128-bit and 256-bit AES symmetric encryption, the cryptography schemes of the messages in the Streembit network, are safe from any brute force attacks. The following UML diagram describes the key exchange using ECDH and securing the message with 256-bit AES symmetric key between 'User A' and 'User B'.

![alt text](./images/streembit/secure1.png "Streembit cryptography explained")
