---
layout: post
title: addGroupNameAlias
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: addgroupnamealias
---

This command creates secondary name(s) for group names. Once an alias is created the group name cannot be used to request HTTP playback of that stream. Once an alias is used (requested by a client) the alias is removed. Aliases are designed to be used to protect/hide your source streams.

**Note:**	`hasGroupNameAliases` in webconfig.lua should be TRUE.



This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                         |
| :----------------: | :-----------: | :---------------: | --------------------------------------- |
|     groupName      |     true      |      *null*       | The original group name                 |
|     aliasName      |     true      |      *null*       | The alias alternative to the group name |

An example of the addGroupNameAlias interface is:

``` 
addGroupNameAlias groupName=MyGroup aliasName=mygroupalias
```

This sets “mygroupalias” as the alias alternative for the group name “mygroup”.

------

**Example:**

**API Call:**

``` 
addGroupNameAlias groupName=MyGroup aliasName=TestGroupAlias
```

**JSON Response:**

``` 
{
"data":{
    "aliasName":"TestGroupAlias",
    "cliProtocolId":97,
    "edges":[],
    "edgesCount":0,
    "groupName":"MyGroup",
    "lastUpdate":1442374870,
    "operation":"addGroupNameAlias",
    "result":true,
    "uniqueRequestId":2
},
"description":"Alias applied to group name",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – Provides the following information for the added group name alias
  
  - aliasName – The alias alternative to be added for the group name
  - cliProtocolId – For internal use only
  - edges – the process IDs and stream IDs for all edge instances
  - edgesCount – The number of edge instances
  - groupName – The original group name
  - lastUpdate – For internal use only
  - operation – The command executed
  - result – `true` if the operation succeeded, `false` if not
  - uniqueRequestId – For internal use only
  
- description – Describes the result of parsing/executing the command
  
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
  
  ​