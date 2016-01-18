---
layout: post
title: inStreamCodecsUpdated, outStreamCodecsUpdated, streamCodecsUpdated
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: codecs_updated
---

A new inbound, outbound or neutral stream has been identified with a specific codec.

- appName – Name of the application using the stream.
- audio – Statistics about the audio stream.
- bandwidth – Bandwidth of the stream.
- connectionType – Connection type used by stream.
- creationTimestamp – Epoch time stamp when the stream was created (msec since 1/1/70)
- ip – IP address used by the stream
- nearIP – The address used by the host computer
- farIP – the address used by the stream source
- name – Name assigned to the stream
- port – Port used by the stream
- nearPort – The port used by the host computer
- farPort – the port used by the stream source
- pullSettings – `pullstream` settings. *Only present for inbound streams that are pulled via the pullStream API command*
- queryTimestamp – Epoch time stamp when the stream was queried (msec since 1/1/70)
- record – Record settings for the stream
- type – Protocol type (see Table of Protocol Types below)
- typeNumeric – Protocol type in decimal
- uniqueId – Stream ID
- upTime – Stream duration in milliseconds
- video – Statistics about the video stream

------

**Example:**                                       

``` 
appName: evostreamms
	audio:
		bytesCount: 0
		codec: AUNK
		codecNumeric: 4707755069515235328
		droppedBytesCount: 0
		droppedPacketsCount: 0
		packetsCount: 0
	bandwidth: 548
	connectionType: 1
	creationTimestamp: 1361182998409.229
	ip: 192.168.2.88
	name: test
	port: 49730
	pullSettings:
		audioCodecBytes: 
		configId: 1
		emulateUserAgent: EvoStream Media Server (www.evostream.com) player
		forceTcp: false
		isAudio: true
		keepAlive: true
		localStreamName: test
		operationType: 1
		pageUrl: 
		ppsBytes: 
		rtcpDetectionInterval: 10
		spsBytes: 
		ssmIp: 
		swfUrl: 
		tcUrl: 
		tos: 256
		ttl: 256
		uri: rtmp://cp76072.live.edgefcs.net/live/MED-HQ-Flash@42814
	queryTimestamp: 1361182998456.029
	type: INR
	typeNumeric: 5282249572905648128
	uniqueId: 2
	upTime: 46.800
	video:
		bytesCount: 56
		codec: VH264
		codecNumeric: 6217274493967007744
		droppedBytesCount: 0
		droppedPacketsCount: 0
		packetsCount: 1
```



