---
layout: post
title: Connection Based Events
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: connection_based_events
---

## protocolRegisteredToApp 

A connection has been fully established.

- customParameters – Custom parameters for the protocol.
- protocolType – Protocol type (see Table of Protocol Types below).

**Example:** 

``` 
	customParameters:
		ip: 127.0.0.1
		port: 1112
		protocol: inboundJsonCli
		sslCert: 
		sslKey: 
		useLengthPadding: true
	protocolType: IJSONCLI
```

------

## protocolUnregisteredFromApp 

A connection has been disconnected.

- customParameters – Custom parameters for the protocol.
- protocolType – Protocol type (see Table of Protocol Types below).

**Example:**     

``` 
	customParameters:
		ip: 127.0.0.1
		port: 1112
		protocol: inboundJsonCli
		sslCert: 
		sslKey: 
		useLengthPadding: true
	protocolType: IJSONCLI
```

------

## carrierCreated

Some IO handler, such as a TCP socket, has been created.

------

## carrierClosed  

Some IO handler, such as a UDP socket, has been closed.
