---
layout: post
title: enableService
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: enable_service
---

Enable or disable a service.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                   |
| :----------------: | :-----------: | :---------------: | --------------------------------- |
|         id         |     true      |      *null*       | The id of the service             |
|       enable       |     true      |      *null*       | 1 to enable, 0 to disable service |

An example of the enableService interface is:

``` 
enableService id=5 enable=0
```

This disables the service with an id of 5.

------

**Example:**

**API Call:**

``` 
enableService id=5 enable=0
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
        "id":5,
        "ip":"0.0.0.0",
        "port":6666,
        "protocol":"inboundLiveFlv",
        "sslCert":"",
        "sslKey":"",
        "waitForMetadata":true
    },
    "description":"Status changed",
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
  - sslCert – The SSL certificate
  - sslKey – The SSL certificate key
  - waitForMedia - 
  
- description – Describes the result of parsing/executing the command
  
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
  
  ​
