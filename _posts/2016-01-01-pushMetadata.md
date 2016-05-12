---
layout: post
title: pushMetadata
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: pushmetadata
---

Opens an outboundVmf TCP stream over which each modified JSON metadata object is sent.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|  localStreamName   |     true      |      *null*       | Name of the stream to which the associated metadata will be sent |
|        type        |     false     |        vmf        | Type of push stream                      |
|         ip         |     false     |     127.0.0.1     | IP address to push to                    |
|        port        |     false     |       8110        | Port to push to                          |

An example of the pushMetadata interface is:

``` 
pushMetadata localStreamName=test ip=127.0.0.1 port=8110
```

------

**Example:**

**API Call:**

``` 
pushMetadata localStreamName=test ip=127.0.0.1 port=8110
```

**JSON Response:**

``` 
{
   "data":{
      "applicationName":"evostreamms",
      "ip":"127.0.0.1",
      "keepAlive":true,
      "localStreamName":"test",
      "name":"evostreamms",
      "port":8110,
      "protocol":"outboundVmf",
      "streamName":"test",
      "type":"vmf"
   },
   "description":"Launched Metadata Push Stream",
   "status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse.
  - applicationName – The EMS (evostreamms)
  - ip – The IP address to push to
  - keepAlive – Indicates if it will be enabled after restart
  - localStreamName – Name of the stream to which the associated metadata will be sent
  - name – Name of the application (evostreamms)
  - port – The port to push to
  - protocol – The type of stream
  - streamName – Name of the stream to which the associated metadata will be sent
  - type – The type of stream
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
