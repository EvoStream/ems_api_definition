---
layout: post
title: stopWebRTC
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: stop_web_rtc
---

Stops the WebRTC Signalling client to an ERS (Evostream Rendezvous Server)

This function has no parameters.

------

**Example:**

**API Call:**

``` 
stopwebrtc
```

**JSON Response:**

``` 
{
"data":{
    "ersip":"",
    "ersport":0,
    "roomid":""
},
"description":"Stopped WebRTC Negotiation Service",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details.

- data – The data to parse
  - ersip – The IP address of the ERS
  - ersport – The port of the ERS
  - roomId – The room identifier
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
