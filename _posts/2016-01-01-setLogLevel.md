---
layout: post
title: setLogLevel
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: setloglevel
---

Change the log level for all log appenders. Default value in the system is set in the config.lua file, which is usually set to 6.

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**          |
| :----------------: | :-----------: | :---------------: | ------------------------ |
|       level        |     true      |      *null*       | A value between -1 and 6 |

Log Levels:

- 0 – Fatal   
- 1 – Error  
- 2 – Warning
- 3 – Info 
- 4– Debug
- 5 – Fine
- 6 – Finest

An example of the setLogLevel interface is:

``` 
setLogLevel level=1
```

This sets the log level to 1. It means it will only output the error logs.

------

**Example:**

**API Call:**

``` 
setLogLevel level=1
```

**JSON Response:**

``` 
{
"data":null,
"description":"Log level is set",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – Nothing to parse for this command
- description – Describes the result of parsing/executing the command


- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
