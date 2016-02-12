---
layout: post
title: clientsConnected
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: clientsconnected
---

Returns all the clients currently utilizing the EMS.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | :--------------------------------------- |
|  localStreamName   |     false     |      *null*       | The name of the particular stream. If this parameter is specified, the command will return the number of clients connected which use that stream |

------

**Example:**

**API Call:**

``` 
clientsConnected
```

**JSON Response:**

``` 
clientsConnected{
"data":{
    "outboundCount":3
},
"description":"EMS outbound client connections count",
"status":"SUCCESS"
}
```

**API Call:**

``` 
clientsConnected localStreamName=MyStream
```

**JSON Response:**

``` 
{
"data":{
		"outboundCount":0
},
"description":"EMS outbound client connections count for the corresponding localstreamname: MyStream",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - outboundCount – The number of client connections
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
