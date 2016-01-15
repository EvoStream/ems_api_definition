---
layout: post
title: listStreamsIds
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: list_streams_ids
---

Get a list of IDs for every active stream.

This function has no parameters.

**Example:**

**API Call:**

``` 
listStreamsIds
```

**JSON Response:**

``` 
{
"data":[205,206,207],
"description":"Available stream IDs",
"status":"SUCCESS"
}
```

------

A JSON message will be returned containing the IDs of the active streams:

- data – Contains an array of IDs (integers) for theactive streams


- description – Describes the result of parsing/executing the command


- status – `SUCCESS` if the command was parsed andexecuted successfully, `FAIL` if not
