---
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: startWebRTC
---

# startWebRTC

Starts a WebRTC signalling client to an ERS (Evostream Rendezvous Server)

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|       ersip        |     true      |      *null*       | IP address (xx.yy.zz.xx) of ERS          |
|      ersport       |     true      |      *null*       | IP address (xx.yy.zz.xx) of ERS          |
|       roomId       |     true      |      *null*       | Unique room Identifier (string) within ERS that will be used by client browsers to connect to this EMS |

An example of the startwebrtc interface is:

``` 
startWebrtc ersip=52.6.14.61 ersport=3535 roomid=ThisIsATestRoomName
```

This will open port 3535 in IP 52.6.14.61 and will open doors for the room ID which can be accessed using the evowrtcclient.html

------

**Example:**

**API Call:**

``` 
startWebrtc ersip=52.6.14.61 ersport=3535 roomid=ThisIsATestRoomName 
```

**JSON Response:**

``` 
{
"data":{
    "configId":2,
    "ersip":"52.6.14.61",
    "ersport":3535,
    "keepAlive":true,
    "name":"evostreamms",
    "operationType":9,
    "roomid":"ThisIsATestRoomName",
    "sslCert":"..\/config\/server.cert",
    "sslKey":"..\/config\/server.key"
},
"description":"Started WebRTC Negotiation Service",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details.

- data – The data to parse.
  - configId - The configuration ID for this command
  - ersip – The IP address of the ERS
  - ersport – The port of the ERS
  - keepAlive - ??
  - name - ??
  - operationType – The type of operation
  - roomId – The room identifier
  - sslCert - The SSL certificate
  - sslKey - The SSL key certificate
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
