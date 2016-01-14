---
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: removeIngestPoint
---

# removeIngestPoint

Removes an RTMP ingest point.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
| privateStreamName  |     true      |      *null*       | The Ingest Point is identified by the privateStreamName, so only that is required to delete it |

------

# **Example:**

**API Call:**

``` 
removeIngestPoint privateStreamName=theIngestPoint
```

**JSON Response:**

``` 
{
"data":{
    "privateStreamName":"theIngestPoint",
    "publicStreamName":"useMeToViewStream"
},
"description":"Ingest point created remvoed",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - privateStreamName – The privateStreamName of the deleted Ingest Point
  - publicStreamName – The publicStreamName of the deleted Ingest Point
- description – Describes the result of parsing/executing the command


- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not.
