---
layout: post
title: httpClientsConnected
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: httpclientsconnected
---

Returns all the clients which are currently utilizing the EWS.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|     groupName      |     false     |      *null*       | The name of the particular group. If this parameter is specified, the command will return the number of clients connected which are playing streams falling under that group |

------

**Example:**

**API Call:**

``` 
httpClientsConnected
```

**JSON Response:**

``` 
{
"data":{
    "groupName":"",
    "httpStreamingSessionsCount":2
},
"description":"Number of clients connected to Evostream Web Server",
"status":"SUCCESS"
} 
```

**API Call:**

``` 
httpClientsConnected
```

**JSON Response:**

``` 
{
"data":{
    "groupName":"",
    "httpStreamingSessionsCount":2
},
"description":"Number of clients connected to Evostream Web Server under groupname: MyGroupStream",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - groupName – The group name to which the clients are connected to
  - httpStreamingSessionsCount – The number of client connections
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
