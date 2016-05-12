---
layout: post
title: listInboundStreamNames
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: listInboundStreamNames
---

Provides a list of all the current inbound localstreamnames.

The API has no parameter.

------

**Example:**

**API Call:**

``` 
listInboundStreamNames
```

**JSON Response:**

``` 
{
"data":[
  {
  "name":"teststream1"
  },
  {
  "name":"teststream2"
  },
  {
  "name":"teststream3"
  }
],
"description":"Inbound local stream names",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details about each stream:

- data – The data to parse.
  - name - the localstreamname of the inbound stream
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not