---
layout: post
title: resetTotalFdCounters
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: resettotalfdcounters
---

Reset the cumulative totals from theConnection Counters.

This interface has no parameters.

------

**Example:**

**API Call:**

``` 
resetTotalFdCounters
```

**JSON Response:**

``` 
{
"data":null,
"description":"Total counters are cleared",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – Nothing to parse for this command
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
