---
layout: post
title: User Defined Variables
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: user_defined_variables
---

While the EMS provides an extensive set of API functions, there may be times where the variables provided are not sufficient, or where you may need extra information to be associated with individual streams. To support these needs, the EMS API implements User Defined Variables. User Defined Variables can be used with any API function where information is maintained by the EMS (i.e. pulling a stream, creating a timer, starting a transcode job, etc.).

To specify a User Defined Variable, you simply need to append a ‘\_’ to the beginning of your variable name. The User Defined variables are reported back whenever you get information about the command: listStreams, listConfig, Event Notifications, etc.

Some common use cases for User Defined Variables are as follows:

**A.** Setting a timer to stop a stream after a set period of time

``` 
setTimer value=120 _streamName=MyStream
setTimer value=120 _streamID=5
```

These commands will fire a timer event after 120 seconds with the set stream name or stream id respectively.

**B.** Attach a custom identifier to a local stream

``` 
pullstream uri=rtmp://192.168.1.5/live/myStream localstreamname=test1 _myID=5 _myName=secretSquirrel
```

**C.** Set a custom value on a pushed stream

``` 
pushstream uri=rtmp://192.168.1.5/live/myStream localstreamname=test1 _myID=5 _myName=secretSquirrel
```
