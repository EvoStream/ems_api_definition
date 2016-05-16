---
layout: post
title: isStreamRunning
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: isstreamrunning
---

Checks a specific stream if it is running or not.

Select either to check by `id` or by `localStreamName`.

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                      |
| :----------------: | :-----------: | :---------------: | ------------------------------------ |
|         id         |     false     |     0 *false*     | The unique id of the stream to check |
|  localStreamName   |     false     |     0 *false*     | The name of the stream to check      |



------

**Example:**

**API Call:**

``` 
isStreamRunning id=1
```

``` 
isStreamRunning localStreamName=testStream
```

**JSON Response:**

``` 
"data":{
"Running":true
},
"description":"Stream status:",
"status":"SUCCESS"
```

``` 
"data":{
"Running":false
},
"description":"Stream status:",
"status":"SUCCESS"
```

------

The JSON response contains the following details about each stream:

- data – The data to parse.
  - Running - tells whether the stream is active (`true`) or not (`false`)
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not