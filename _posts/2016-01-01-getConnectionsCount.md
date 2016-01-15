---
layout: post
title: getConnectionsCount
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: get_connections_count
---

Returns the number of active connections.  This includes connections necessary for EMS operations (telnet, license manager, interface, etc.) and all connections opened by streams (RTSP-UDP-RTP ports).

This interface has no parameters.

------

**Example:**

**API Call:**

``` 
getConnectionsCount
```

**JSON Response:**

``` 
{
"data":{
    "count":3
},
"description":"Active connections count",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - count – The number of active connections
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
