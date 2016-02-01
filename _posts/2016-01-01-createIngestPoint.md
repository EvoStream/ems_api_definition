---
layout: post
title: createIngestPoint
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: create_ingest_point
---

Creates an RTMP ingest point, which mandates that streams pushed into the EMS have a target stream name which matches one Ingest Point privateStreamName.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
| privateStreamName  |     true      |      *null*       | The name that RTMP Target Stream Names must match |
|  publicStreamName  |     True      |      *null*       | The name that is used to access the stream pushed to the `privateStreamName`. The `publicStreamName` becomes the streams `localStreamName` |

------

**Example:**

**API Call:**

``` 
createIngestPoint privateStreamName=theIngestPoint publicStreamName=useMeToViewStream
```

**JSON Response:**

``` 
{
"data":{
    "privateStreamName":"theIngestPoint",
    "publicStreamName":"useMeToViewStream"
},
"description":"Ingest point created",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - privateStreamName –The privateStreamName which was set.
  - publicStreamName – The publicStreamName which was set
- description – Describes the result of parsing/executing the command.


- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not