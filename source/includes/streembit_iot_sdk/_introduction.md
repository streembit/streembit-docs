## Introduction

The Streembit IOT gateway developer kit allows qualified users to set up a Peer 2 Peer communication network that is secure and can control Home Automation Zigbee standard devices. This solution brings a high level of security which exists already within the Streembit communication network platform.

This documentation has been created to provide a guide to the ‘Developer’ user who has experience with programming and is familiar with the Raspberry Pi Eco system. However it is not beyond the scope of the casual user if they take extra time to follow the instructions and pay close attention to the detail and syntax of the documentation.

There are a number of specific configuration requirements and also instructions which should be followed to ensure the developer kit is operational following the set-up

There are resources available in this guide to assist with the set-up which shall be listed here, along with the required hardware components.

### Required Hardware

  * Raspberry - [Pi model 3B](http://zovolt.com/e-shop/pi-b)
  * SD card for [Raspberry Pi](http://zovolt.com/e-shop/pis)
  * Zovolt Gateway - [Streembit R-Pi hat / Expansion board](http://zovolt.com/e-shop/pis-hat)
  * Ethernet cable - recommended to connect R-Pi to router
  * A working Internet connection

  Optional items used to prepare unconfigured Zovolt Gateway Board are listed below

  * [FTDI](http://zovolt.com/e-shop/ftdi) - module to program Zigbee chip on Zovolt Board
  * Jumper wires connectors (man-female) for connecting FTDI module to Zovolt board
  * Mini-B - USB cable for connecting FTDI module to configuration Laptop


### Understanding the fundamentals of the Streembit platform

Before we start it is beneficial to familiarize yourself with the architecture and terminology of components both hardware and software to set up a working Streembit Network

**The Streembit P2P** (peer-2-peer)
Platform is made up a nodes, which can take on different roles depending on the ‘use’ case -  It is therefore important to ensure you follow the correct areas of the Readme documentation and config file examples in this repository for creating an Streembit IOT private network.

**The Streembit UI** (User Interface)
Can be run as an application or a web server.  Zovolt Ltd has made this available for IOT developers at [streembit.co](https://streembit.co) where you can create an account and complete the setup process, once the Streembit CLI - Command Line Interface node is set up on the Raspberry Pi.

**The Streembit CLI** (Command Line Interface)
This element of the Streembit network can be set up as a node to perform different roles within the Streembit network

The principle roles are

  * Seed node for Streembit P2P networking - Kademlia network
  * Client node
  * Blockchain node for operating as a contributing asset to the Streembit Blockchain performing validation of transactions
  * **IOT handler node - to allow command and control of remote devices of a private Streembit IOT network**

For this tutorial the Streembit IOT handler is our focus, so it is important to ensure that you read the correct sections and config file examples that are relevant to the CLI working in this role.

Once you have assembled the acquired hardware and are ready to set up the Streembit software with an internet connection, you as the developer can start the process of preparing the environment and also setting up the Zovolt (Xbee hat / expansion board) ready to work with the Streembit CLI application and connect Zigbee devices.

The following steps should allow the user to efficiently set up Streembit IOT

In the **initial step** please create an user account at [streembit.co](https://www.streembit.co) if you do not have one.  This is the user interface that you can use to quickly set up our IOT network.
