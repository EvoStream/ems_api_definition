---
layout: post
title: removeStreamAlias
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: remove_stream_alias
---

Removes an alias of a stream.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**     |
| :----------------: | :-----------: | :---------------: | ------------------- |
|     aliasName      |     true      |      *null*       | The alias to delete |

An example of the removeStreamAlias interface is:

``` 
removeStreamAlias aliasName=video1
```

------

**Example:**

**API Call:**

``` 
removeStreamAlias aliasName=video1
```

**JSON Response:**

``` 
{
"data":{
	"aliasName":"video1",
}
"description":"Currently available aliases",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details.

- data – The data to parse
  - aliasName – The alias of the stream that was removed
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
