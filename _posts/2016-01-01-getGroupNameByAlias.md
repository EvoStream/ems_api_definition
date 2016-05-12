---
layout: post
title: getGroupNameByAlias
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: getgroupnamebyalias
---

This command returns the group name given the alias name.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**         |
| :----------------: | :-----------: | :---------------: | ----------------------- |
|     aliasName      |     true      |      *null*       | The original group name |

------

**Example:**

**API Call:**

``` 
getGroupNameByAlias aliasName=TestGroupAlias
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
    "operation":"getGroupNameByAlias",
    "result":true,
    "uniqueRequestId":4
},
"description":"Group name",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – Provides the following information for the added group name alias
  
  - aliasName – The alias alternative to be added for the group name
  - cliProtocolId – For internal use
  - edges – the process IDs and stream IDs for all edge instances
  - edgesCount – The number of edge instances
  - groupName – The original group name
  - lastUpdate – Timestamp
  - operation – The command executed
  - result – `true` if the operation succeeded, `false` if not
  - uniqueRequestId – For internal use
  
- description – Describes the result of parsing/executing the command
  
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
  
  ​
