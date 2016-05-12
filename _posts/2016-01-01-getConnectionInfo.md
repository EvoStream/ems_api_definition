---
layout: post
title: getConnectionInfo
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: getconnectioninfo
---

Returns a detailed set of information about a connection.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|         id         |     true      |      *null*       | The uniqueId of the connection. Usually a value returned by listConnectionsIds |

An example of the getConnectionInfo interface is:

``` 
getConnectionInfo id=144
```

This gets connection info about a connection with id of 144.

------

**Example:**

**API Call:**

``` 
getConnectionInfo id=144
```

**JSON Response:**

``` 
{
    "data":{
        "carrier":null,
        "stack":[
            {
                "applicationId":1,
                "creationTimestamp":1338633696196.6460,
                "id":144,
                "isEnqueueForDelete":false,
                "queryTimestamp":1338658491380.7349,
                "type":"TMR"
            }
        ]
    },
    "description":"Connection information",
    "status":"SUCCESS"
}
```

------

The JSON response contains the following details about one connection:

- data – The data to parse. See the `listConnections` command for a description of the fields
  - carrier - Details about the connection itself
  - stack - details about what internal resources are using the connection
    - applicationId - the ID of the internal application using the connection
    - creationTimeStamp - The time (in UNIX seconds) when the application started using the connection
    - Id - The unique ID for this stack relation
    - isEnqueForDelete - Internal flag used for cleanup
    - queryTimeStamp - The time (in UNIX seconds) when this data was populated
    - type - A descriptor for how the application is using the connection


- description – Describes the result of parsing/executing the command


- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not