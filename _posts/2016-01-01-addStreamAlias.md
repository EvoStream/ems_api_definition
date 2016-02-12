---
layout: post
title: addStreamAlias
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: addstreamalias
---

Allows you to create secondary name(s) for internal streams. Once an alias is created the localstreamname cannot be used to request playback of that stream. Once an alias is used (requested by a client) the alias is removed. Aliases are designed to be used to protect/hide your source streams.

***Note:*** 	***`hasStreamAliases` in config.lua should be TRUE.***

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|  localStreamName   |     true      |      *null*       | The original stream name                 |
|     aliasName      |     true      |      *null*       | The alias alternative to the localStreamName |
|    expirePeriod    |     false     | *-600 (10 mins)*  | The expiration period for this alias. Negative values will be treated as one-shot but no longer than the absolute positive value in seconds, **0** means it will not expire, positive values mean the alias can be used multiple times but expires after this many seconds. The default is **-600** (one-shot, 10 mins) |

An example of the addStreamAlias interface is:

``` 
addStreamAlias localStreamName=bunny aliasName=video1 expirePeriod=-300
```

Stream with bunny as localStreamName will have an alias of video1.

------

**Example:**

**API Call:**

``` 
addStreamAlias localStreamName=MyStream aliasName=video1 expirePeriod=-300
```

**JSON Response:**

``` 
{
"data":{
    "aliasName":"video1",
    "expirePeriod":-300,
    "localStreamName":"MyStream"
},
"description":"Alias applied",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - aliasName – The alias alternative to the localStreamName
  - expirePeriod – The expiration period for this alias
  - localStreamName – The original stream name


- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
