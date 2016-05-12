---
layout: post
title: listConnectionsIds
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: listconnectionsids
---

Returns a list containing the IDs of every active stream-related connection. This does not include other connections used for EMS operations (telnet, license manager, interface, etc.).

This interface has no parameters.

------

**Example:**

**API Call:**

``` 
listConnectionsIds
```

**JSON Response:**

``` 
{
    "data":[144,186,201],
    "description":"Available connection IDs",
    "status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – An array of connection IDs


- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
