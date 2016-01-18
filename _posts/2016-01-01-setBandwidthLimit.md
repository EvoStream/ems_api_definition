---
layout: post
title: setBandwidthLimit
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: set_bandwidth_limit
---

Enforces a limit on input and output bandwidth.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|         in         |     true      |      *null*       | Maximum input bandwidth. 0 means disabled. CLI connections are not affected |
|        out         |     true      |      *null*       | Maximum output bandwidth. 0 means disabled. CLI connections are not affected. |

An example of the setBandwidthLimit interface is:

``` 
setBandwidthLimit in=400000 out=300000
```

This sets the inbound bandwidth limit to 400,000, and the outbound bandwidth limit to 300,000 bytes/sec.

------

**Example:**

**API Call:**

``` 
setBandwidthLimit in=400000 out=300000
```

**JSON Response:**

``` 
{
"data":{
    "current":{
    "in":111880.0459,
    "out":147.8026
    },
    "max":{
    "in":400000.0000,
    "out":300000.0000
    }
},
"description":"Bandwidth in B\/s",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to be parsed
  - current – The current bandwidths
    - in – The inbound bandwidth
    - out – The outbound bandwidth
  - max – The maximum bandwidths
    - in – The inbound limit
    - out – The outbound limit
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
