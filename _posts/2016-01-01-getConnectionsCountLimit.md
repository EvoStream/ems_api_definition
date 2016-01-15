---
layout: post
title: getConnectionsCountLimit
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: get_connections_count_limit
---

Returns the limit of concurrent connections. This is the maximum number of connections an EMS instance will allow at one time.

This interface has no parameters.

------

**Example:**

**API Call:**

``` 
getConnectionsCountLimit
```

**JSON Response:**

``` 
{
"data":{
    “cuurent”:3
    "limit":0
},
"description":"Connection counters",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - current – The current number of concurrent connections
  - limit – The maximum number of concurrent connections
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
