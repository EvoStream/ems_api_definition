---
layout: post
title: createService
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: create_service
---

Creates a new service.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                    |
| :----------------: | :-----------: | :---------------: | ---------------------------------- |
|         ip         |     true      |      *null*       | The IP address to bind on          |
|        port        |     true      |      *null*       | The port to bind on                |
|      protocol      |     true      |      *null*       | The protocol stack name to bind on |
|      sslCert       |     false     |      *null*       | The SSL certificate to be used     |
|       sslKey       |     false     |      *null*       | The SSL certificate key to be used |

An example of the setConnectionsLimit interface is:

``` 
createService ip=0.0.0.0 port=9556 protocol=inboundRtmp
```

This creates an acceptor for every hosted IP to accept inbound RTMP requests on port 9556.

------

**Example:**

**API Call:**

``` 
createService ip=0.0.0.0 port=9556 protocol=inboundRtmp
```

**JSON Response:**

``` 
{
"data":{
    "acceptedConnectionsCount":0,
    "appId":1,
    "appName":"evostreamms",
    "droppedConnectionsCount":0,
    "enabled":true,
    "id":974,
    "ip":"0.0.0.0",
    "port":1234,
    "protocol":"inboundRtmp"
    },
"description":"Service created",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - acceptedConnectionsCount – The number of active connections using the service
  - appId – The ID of the application using the service
  - appName – The name of the application using the service
  - droppedConnectionsCount – The number of dropped connections
  - enabled - `true` if the service is enabled, `false` if not
  - id = ID of the service
  - ip = The IP address bound to the service
  - port – The port bound to the service
  - protocol – The protocol bound to the service
- description – Describes the result of parsing/executing the command.
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not.
