---
layout: post
title: shutdownService
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: shutdownservice
---

Terminates a service

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**       |
| :----------------: | :-----------: | :---------------: | --------------------- |
|         id         |     true      |      *null*       | The id of the service |

An example of the shutdownService interface is:

``` 
shutdownService id=5
```

This shuts down the service with an id of 5.

------

**Example:**

**API Call:**

``` 
getBandwidth
```

**JSON Response:**

``` 
{
"data":{
    "acceptedConnectionsCount":0,
    "appId":1,
    "appName":"evostreamms",
    "clustering":true,
    "droppedConnectionsCount":0,
    "enabled":true,
    "id":5,
    "ip":"127.0.0.1",
    "port":1936,
    "protocol":"inboundRtmp",
    "sslCert":"",
    "sslKey":""
    },
"description":"Service 5 removed",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - acceptedConnectionsCount – Number of active connections
  - appId – ID of application using the service
  - appName – Application using the service
  - droppedConnectionsCount – Number of dropped connections
  - enabled - `true` if the service is enabled, `false` if not
  - id – ID of the service
  - ip – IP address used by the service
  - port – Port used by the service
  - protocol – Protocol used by the service
  - sslCert – SSL certificate
  - sslKey – SSL certificate key
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
