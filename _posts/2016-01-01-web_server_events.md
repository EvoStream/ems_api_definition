---
layout: post
title: Web Server Events
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: web_server_events
---

## streamingSessionStarted

This event is created right after an HTTP streaming session has started.

- clientIP – Address of connecting client
- sessionID – Internal ID
- playlist – The playlist file
- startTime – Time session started

------

## streamingSessionEnded

This event is created right after an HTTP streaming session has stopped.

- clientIP – Address of connecting client
- sessionID – Internal ID
- playlist – The playlist file
- startTime – Time session started
- stopTime – Time session stopped

------

## fileDownloaded

This event is created right after an HTTP file download has completed.

- clientIP – Address of connecting client.
- mediaFile – The path to the media file.
- startTime – Time session started.
- elapsed – The number of seconds since the session started
