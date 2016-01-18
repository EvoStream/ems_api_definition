---
layout: post
title: Application Based Events
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: application_based_events
---

## applicationStart, applicationStop

These events are created right after the internal EMS application has started and when that application has stopped, likely indicating server shutdown.

- config – Configuration of the application that just started (see EMS User's Guide for details)
- id – ID of the application that just started
- name – Name of the application that just started

**Example:**                                                 

``` 
config:
acceptors:
0:
	ip: 127.0.0.1
	port: 1112
	protocol: inboundJsonCli
	sslCert: 
	sslKey: 
	useLengthPadding: true
1:
	ip: 0.0.0.0
	port: 7777
	protocol: inboundHttpJsonCli
	sslCert: 
	sslKey: 
2:
	ip: 0.0.0.0
	port: 1935
	protocol: inboundRtmp
	sslCert: 
	sslKey: 
3:
	clustering: true
	ip: 127.0.0.1
	port: 1936
	protocol: inboundRtmp
	sslCert: 
	sslKey: 
4:
	clustering: true
	ip: 127.0.0.1
	port: 1113
	protocol: inboundBinVariant
	sslCert: 
	sslKey: 
5:
	ip: 0.0.0.0
	port: 5544
	protocol: inboundRtsp
	sslCert: 
	sslKey: 
6:
	ip: 0.0.0.0
	port: 6666
	protocol: inboundLiveFlv
	sslCert: 
	sslKey: 
	waitForMetadata: true
aliases:
	0: er
	1: live
	2: vod
appDir: C:\emsdemo\config\
authPersistenceFile: ..\config\auth.xml
bandwidthLimitPersistenceFile: ..\config\bandwidthlimits.xml
connectionsLimitPersistenceFile: ..\config\connlimits.xml
default: true
description: EVOSTREAM MEDIA SERVER
eventLogger:
	sinks:
	1:
		filename: ..\logs\events.txt
		format: text
		type: file
		hasStreamAliases: false
		initApplicationFunction: GetApplication_evostreamms
		initFactoryFunction: GetFactory_evostreamms
		library: 
		maxRtmpOutBuffer: 524288
		mediaStorage:
			1:
				description: Default media storage
				mediaFolder: ../media
		metaFileGenerator: false
		name: evostreamms
		protocol: dynamiclinklibrary
		pushPullPersistenceFile: ..\config\pushPullSetup.xml
		rtcpDetectionInterval: 15
		streamsExpireTimer: 10
		validateHandshake: false
id: 1
name: evostreamms
```

------

## serverStarted

The server has started.

------

## serverStopped

The server is just about to stop.
