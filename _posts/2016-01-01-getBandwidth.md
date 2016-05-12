---
layout: post
title: getBandwidth
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: getbandwidth
---

Returns bandwidth information: currentvalues and limits.

This interface has no parameters.

------

**Example:**

**API Call:**

``` 
getBandwidth
```

**JSON Response:**

``` 
{
"data":{
    "current":{
    "in":111880.0459,
    "out":147.8026
	},
    "max":{
    "in":0.0000,
    "out":0.0000
    }
},
"description":"Bandwidth in B\/s",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - current – The current bandwidths
    - in – The inbound bandwidth
    - out – The outbound bandwidth
  - max – The maximum bandwidths
    - in – The inbound limit
    - out - The outbound limit
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
