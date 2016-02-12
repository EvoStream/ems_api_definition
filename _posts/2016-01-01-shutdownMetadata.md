---
layout: post
title: shutdownMetadata
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: shutdownmetadata
---

Stops a metadata pseudo-stream. This command shuts down all multiple pull streams that were issued for a given localStreamName.

This function has the following parameter:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|  localStreamName   |     true      |      *null*       | Metadata associated with this incoming stream name |

------

**Example:**

**API Call:**

``` 
shutdownMetadata localStreamName=test
```

**JSON Response:**

``` 
{
"data":{
    "localStreamName":"test",
    "streamName":"test",
    "type":"vmf"
},
"description":"Shutdown Metadata Push Stream", 
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - localStreamName – Name of the stream to which the associated metadata will be sent
  - streamName – Name of the stream to which the associated metadata will be sent
  - type – The type of stream
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
