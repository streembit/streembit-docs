## Dependencies**

```json
see shell code
```
```shell
npm install
```

Get the dependencies with

Windows note:
```json
see shell code
```
```shell
npm install leveldown --msvs_version=2015
```
In case of leveldown or any any node-gyp error provide a correct msvs_version build parameter e.g.

In order to run the application a configuration file config.json must exists in the root directory of the project.

A typical configuration file is the following:

```json
{
  "database_name": "streembitsql",
  "cmdinput": false,
  "seeds": [],
  "transport": {
    "protocol": "http",
    "host": "182.120.242.165",
    "port": 32321,
    "ws": {
      "port": 32318,
      "maxconn":  10000
    }
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
      "run": true
    },
    {
      "name": "client",
      "run": false,
      "account": "",
      "contacts": []
    },
    {
      "name": "blockchain",
      "run": false
    },
    {
      "name": "iot",
      "run": false,
      "serialport": "/dev/ttyS0",
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
          "id": "0013a20041679c00",
          "name": "Streembit Hub",
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
      "host": "srv.streembit.net",
      "port": 8080
    }
  ],
  "log": {
    "level": "debug",
    "logs_dir": "logs"
  }
}
````
```shell
see json tab
```
