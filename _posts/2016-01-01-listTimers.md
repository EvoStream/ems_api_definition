---
layout: post
title: listTimers
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: list_timers
---

This function lists currently active timers.

This function has no parameters.

------

**Example:**

**API Call:**

``` 
listTimers
```

**JSON Response:**

``` 
{
  "data":[
    {
      "timerId":8,
      "triggerCount":141,
      "value":10
    }
  ],
  "description":"List of armed timers",
  "status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse.
  - timerId – The ID of the timer added
  - triggerCount – The number of times the timer triggered since it was added
  - value – The time value for the timer (see parameter table above)
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
