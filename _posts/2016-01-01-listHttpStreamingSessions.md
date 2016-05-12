---
layout: post
title: listHttpStreamingSessions
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: listhttpstreamingsessions
---

This command lists all currently active HTTP streaming sessions.

The function has no parameter.

------

**Example:**

**API Call:**

``` 
listHttpStreamingSessions
```

**JSON Response:**

``` 
{
  "data": [
    {
    "clientIP": "127.0.0.1",
    "elapsedTime": 33,
    "sessionId": 1,
    "startTime": "2014-12-17T18-31-13",
    "targetFolder": "C:\\xampp\\htdocs\\mss_group\\mystream"
    }
  ],
  "description":"Currently open HTTP streaming sessions",
  "status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – Provides the following information for each group name alias:
  - clientIP – The IP address of the connected client
  - sessionId – An internal ID for the session
  - startTime – The timestamp when the session started
  - elapsedTime – The number of seconds since the session started
  - targetFolder – The current folder used as the source for HTTP streaming
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
