---
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: getStreamsCount
---

# getStreamsCount

Returns the number of active streams.

This function has no parameters.

------

**Example:**

**API Call:**

``` 
getStreamsCount
```

**JSON Response:**

``` 
{
"data":{
  "streamCount":1
  },
  "description":"Active streams count",
  "status":"SUCCESS"
}

```

------

A JSON message will be returned giving the number of active streams:

- data – The data to parse
  - streamCount – The number of active streams
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
