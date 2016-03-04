---
layout: post
title: listStreamAliases
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: liststreamaliases
---

Returns a complete list of aliases.

This function has no parameters.

------

**Example:**

**API Call:**

``` 
listStreamAliases
```

**JSON Response:**

``` 
{
"data":[
    {
    "aliasName":"video1",
    "creationTime":1448267205,
    "expirePeriod":300,
    "localStreamName":"MyStream",
    "oneShot":true,
    "permanent":false
}
],
"description":"Currently available aliases",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details.

- data – Contains an array of pairs of `aliasName` and `localStreamName`
  - aliasName – The alias alternative to the `localStreamName`
  - creationTime – The time the alias is created
  - expirePeriod - The expiration period of the alias
  - localStreamName – The original stream name
  - oneShot - Determines if the alias can only be used once
  - permanent - Determines if the alias is for permanent use (unless EMS is restarted)
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not