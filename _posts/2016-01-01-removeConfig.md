---
layout: post
title: removeConfig
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: removeconfig
---

This command will both stop the stream and remove the corresponding configuration entry. This command is the same as performing `shutdownStream permanently=1`.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|         id         |     true      |      *null*       | The configId of the configuration that needs to be removed. ConfigId’s can be obtained from the listConfig interface. Removing an inbound stream will also automatically remove all associated outbound streams. |
|     groupName      |     true      |      *null*       | The name of the group that needs to be removed (applicable to HLS, HDS and external processes). \*Mandatory only if the id parameter is not specified. |
| removeHlsHdsFiles  |     false     |     0 *false*     | If 1 (true) and the stream is HLS or HDS, the folder associated with it will be removed |

------

**Example:**

**API Call:**

``` 
removeConfig id=555
```

**JSON Response:**

``` 
{
"data":{
    *..remove details for clarity*
    },
    "description":"Configuration terminated",
    "status":"SUCCESS"
}
```

------

The JSON response contains the following details about the pull/push configuration:

- data – The data to parse.
  - configId – The identifier for the pullPushConfig.xml entry
  - Other fields present are dependent on stream type


- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not

-----

Note:

The config ID shown by the listConfig command is not the same as the stream ID shown by the listStreams command. The removeConfig command uses the config ID, not the stream ID.
