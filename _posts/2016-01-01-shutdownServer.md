---
layout: post
title: shutdownServer
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: shutdown_server
---

This function ends the server process, completely shutting down the EMS. This function must be called twice, once with a blank parameter, allowing you to obtain the shutdown key, and then a second time with the key, which actually causes the EMS to terminate.

| Parameter Name | Mandatory | Default Value | Description                              |
| :------------: | :-------: | :-----------: | ---------------------------------------- |
|      key       |   false   |    *null*     | The key to shutdown the server. shutdownServer must be called without the key to obtain the key and once again with the returned key to shutdown the server |

------

**Example:**

**API Call:**

``` 
shutdownServer
```

**JSON Response:**

``` 
{
"data":{
    "key":"GCY6IXniMf6NDOxY"
},
"description":"Call shutdownserver again with the provided key",
"status":"SUCCESS"
}
```

The JSON response contains the following details:

- data – The data to parse
  - key – The key that needs to be used in a subsequent call to shutdownServer
- description – Describes the result of parsing/executing the command.
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not

------

To shutdown the Server enter the same command with the key parameter given:

**Example:**

**API Call:**

``` 
shutdownServer key=GCY6IXniMf6NDOxY
```

**JSON Response:**

``` 
Connection to host lost.
```
