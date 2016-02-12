---
layout: post
title: setConnectionsCountLimit
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: setconnectionscountlimit
---

This interface sets a limit on the number of concurrent connections the EMS will allow.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|       count        |     true      |      *null*       | The maximum number of connections allowed on this instance at one time. CLI connections are not affected |

An example of the setConnectionsCountLimit interface is:

``` 
setConnectionsCountLimit count=500
```

This sets the connection limit to 500.

------

**Example:**

**API Call:**

``` 
setConnectionsCountLimit count=500
```

**JSON Response:**

``` 
{
"data":{
    “cuurent”:3
    "limit":500
},
"description":"Connection counters",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to be parsed
  - current – The current bandwidths
  - max – The maximum bandwidths
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
