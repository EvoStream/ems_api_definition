---
layout: post
title: removeTimer
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: removetimer
---

This function removes a previously armed timer.

This function has the following parameter:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                   |
| :----------------: | :-----------: | :---------------: | --------------------------------- |
|         id         |     true      |      *null*       | The ID of the timer to be removed |

------

**Example:**

**API Call:**

``` 
removeTimer id=8
```

**JSON Response:**

``` 
{
  "data":{
    "timerId":8,
    "triggerCount":141,
    "value":10
  },
  "description":"Timer removed",
  "status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse.
  - timerId – The ID of the timer added
  - triggerCount – The number of times the timer triggered since it was added
  - value – The time value for the timer (see parameter table for setTimer function)
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
