---
layout: post
title: Configuring and Receiving Event Notifications
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: configuring_and_receiving_event_notifications
---

The EvoStream Media Server (EMS) generates notifications based upon events that occur at runtime. These events are formatted as HTTP calls and can be delivered to any address and port desired.

Event Notifications are **disabled** by default and must be enabled by modifying the EMS config file: config.lua.

To enable Event Notifications you will need to Enable/Uncomment the *eventLogger* section of the config.lua file. *Comments in LUA are specified by either a “--“ for a single line, or denoted by a “--\[\[“ to start a comment block and a “\]\]--“ to end a comment block. By default the eventLogger section is commented out using block style comments, so you will need to remove both the* “**--\[\[**“ *and* “**\]\]--**“ *strings.* See the Configuration Files section for more information.

------



## Sinks

Sinks are defined as “a specific destination for events” and can be of two types: “file” and “RPC”. File sinks simply write events to a file, as defined by the “filename” parameter. This works much like a system logger. Users can choose the format of the output between JSON, XML, W3C and text. JSON and XML will be formatted as JSON and XML respectively and each event will be written to a single line. This is done for ease of parsing. The W3C formatted file is compliant with the requirement of having space or tab-delimited columns. In addition, it has a header line that is commented out (\#) that indicates the names of the columns. As with JSON and XML, each event is also written to a single line. The Text format writes to the event file in a way that is easy to read, where events are on multiple lines. *The file sink is **off** by default,* but can be turned on by creating the sink in the config.lua file.

To receive HTTP based Event Notifications, an RPC type sink must be defined (and is by default). The URL parameter defines the location that will be called with each event. The URL can be a specific web service script or just an IP and port on which you are listening. RPC sinks have the option of one of three serializer types, or in other words, the way the data will be formatted within the HTTP post: JSON, XML, XMLRPC. XMLRPC events will be formatted as XML using a traditional XML-RPC schema. The XML serializer type will use an XML schema that is more condensed and specific to the EMS Event Notification System. The JSON serializer type will have the same schema as XML, but will be formatted as JSON.

For any Sink, users can define an array of *enabledEvents*. When this array is present, ONLY the events listed will be sent to that sink. If this array is not present, ALL events will be sent to the sink. The full list of events can be found later in this document.
