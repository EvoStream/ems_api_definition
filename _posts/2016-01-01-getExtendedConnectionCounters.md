---
layout: post
title: getExtendedConnectionCounters
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: getextendedconnectioncounters
---

Returns a detailed description of the network descriptors counters. This includes historical high-water-marks for different connection types and cumulative totals.

This interface has no parameters.

------

**Example:**

**API Call:**

``` 
getExtendedConnectionCounters
```

**JSON Response:**

``` 
{
"data":{
    "origin":{
    "grandTotal":{
        "current":22,
        "inBytes":258381745,
        "inSpeed":0.0000,
        "max":24,
        "outBytes":350990,
        "outSpeed":0.0000,
        "total":304
        },
    "managedNonTcpUdp":{
        --removed content for clarity
        },
    "managedTcp":{
        --removed content for clarity
        },
    "managedTcpAcceptors":{
        --removed content for clarity
        },
    "managedTcpConnectors":{
        --removed content for clarity
        },
    "managedUdp":{
        --removed content for clarity
        },
    "rawUdp":{
    "current":0,
    "inBytes":0,
    "max":0,
    "outBytes":0,
    "total":0
    }
    },
    "total":22
},
"description":"Connection counters",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - origin
    - grandTotal – Stats for all connections
    - managedNonTcpUdp – Stats for non-TCP/UDP connections
    - managedTcp – Stats for TCP connections
    - managedTcpAcceptors – Stats for TCP acceptors
    - managedTcpConnectors – Stats for TCP connectors
    - managedUdp – Stats for UDP connections
    - rawUdp – Stats for raw UDP
  - Total – Summary
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not