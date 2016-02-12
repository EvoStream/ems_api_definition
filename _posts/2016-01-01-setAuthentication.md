---
layout: post
title: setAuthentication
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: setauthentication
---

Will enable/disable RTMP authentication. 

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|      enabled       |     true      |      *null*       | 1 to enable, 0 to disable authentication |

An example of the setAuthentication interface is:

``` 
setAuthentication enabled=1
```

This enables authentication.

------

**Example:**

**API Call:**

``` 
setAuthentication enabled=1
```

**JSON Response:**

``` 
{
"data":{
    "enabled":true
},
"description":"Authentication mode updated",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - enabled – \`true\` if authentication is enabled, \`false\` if not
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
