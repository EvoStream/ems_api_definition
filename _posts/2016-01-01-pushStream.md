---
layout: post
title: pushStream
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: pushstream
---

This will try to push a local stream to an externaldestination. The pushed stream can only use the RTMP, RTSP or MPEG-TSunicast/multicast protocol. 

This function has the following parameters:

|     Parameter Name     | Mandatory |        Default Value        | Description                              |
| :--------------------: | :-------: | :-------------------------: | ---------------------------------------- |
|          uri           |   true    |           *null*            | TheURI of the external stream. Can be RTMP, RTSP or unicast/multicast (d) mpegts |
|       keepAlive        |   false   |          1 *true*           | If keepAlive is set to 1, the server will attempt to reestablish connection with astream source after a connection has been lost. The reconnect will be attemptedonce every second |
|    localStreamName     |   false   |         *computed*          | If provided, the stream will be given this name. Otherwise, a fallback techniqueis used to determine the stream name (based on the URI) |
|    targetStreamName    |   false   |           *null*            | The name of the stream at destination. If not provided, the target stream name willbe the same as the local stream name |
|    targetStreamType    |   false   |            live             | It can be one of following: live, record, append. It is meaningful only for RTMP |
|         tcUrl          |   false   |    *zero-length string*     | When specified, this value will be used to set the TC URL in the initial RTMPconnect invoke |
|        pageUrl         |   false   |    *zero-length string*     | When specified, this value will be used to set the originating web page address inthe initial RTMP connect invoke |
|         swfUrl         |   false   |    *zero-length string*     | When specified, this value will be used to set the originating swf URL in theinitial RTMP connect invoke |
|          ttl           |   false   | *operating system supplied* | Sets the IP_TTL (time to live) option on the socket |
|          tos           |   false   | *operating system supplied* | Sets the IP_TOS (Type of Service) option on the socket |
|    emulateUserAgent    |   false   |     *EvoStream message*     | When specified, this value will be used as the user agent string. It is meaningful only for RTMP |
| rtmpAbsoluteTimestamps |   false   |          0 *false*          | Forces the timestamps to be absolute when using RTMP |
|  sendChunkSizeRequest  |   false   |          1 *true*           | Sets whether the RTMP stream will or will not send a “Set Chunk Length” message.  This is significant whenpushing to Akamai’s new RTMP HD ingest point where this parameter should be setto 0 so that Akamai will not drop the connection |
|      useSourcePts      |   false   |          0 *false*          | When value is 1 (true), timestamps on source inbound RTMP stream are passed directlyto the outbound (pushed) RTMP streams. This affects only pushed Outbound Net RTMP with net RTMP source.  This parameter overrides the value of theconfig.lua option of the same name |

The EMS provides several shorthand User Agent strings (not case-sensitive) for convenience:

| **emulateUserAgent**      | **Resolves as..**                        |
| ------------------------- | ---------------------------------------- |
| emulateUserAgent=evo      | EvoStreamMedia Server ([www.evostream.com](http://www.evostream.com)) |
| emulateUserAgent=FMLE     | FMLE/3.0 (compatible; FMSc/1.0)          |
| emulateUserAgent=wirecast | Wirecast/FM 1.0 (compatible;  FMSc/1.0)  |
| emulateUserAgent=flash    | MAC 11,3,300,265                         |

An example of the pushStream interface is:

``` 
pushStream uri=rtmp://DestinationAddress/live localStreamname=testpullstream targetStreamName=testpushStream
```



Then, to access that stream via a flash player, the following URI can be used:

`rtsp://DestinationAddress:5544/testpushStream` 

`rtmp://DestinationAddress/live/testpushStream` 

------

**Example:**

**API Call:**

``` 
pushStream uri=rtmp://192.168.1.2 localStreamName=testpullStream targetStreamName=testpushStream 
```

**JSON Response:**

``` 
{
"data":{
    "configId":6,
    "emulateUserAgent":"EvoStream Media Server (www.evostream.com)",
    "forceTcp":false,
    "httpProxy":"",
    "keepAlive":true,
    "localStreamName":"testpullStream",
    "operationType":2,
    "pageUrl":"",
    "rtmpAbsoluteTimestamps":false,
    "sendChunkSizeRequest":true,
    "swfUrl":"",
    "targetStreamName":"testpushStream",
    "targetStreamType":"live",
    "targetUri":{
        "document":"",
        "documentPath":"\/",
        "documentWithFullParameters":"",
        "fullDocumentPath":"\/",
        "fullDocumentPathWithParameters":"\/",
        "fullParameters":"",
        "fullUri":"rtmp:\/\/127.0.0.1",
        "fullUriWithAuth":"rtmp:\/\/127.0.0.1",
        "host":"localhost",
        "ip":"127.0.0.1",
        "originalUri":"rtmp:\/\/localhost",
        "parameters":{
        },
        "password":"",
        "port":1935,
        "portSpecified": false,
        "scheme":"rtmp",
        "userName":""
        },
    "tcUrl":"",
    "tos":256,
    "ttl":256,
    "useSourcePts":false
},
"description":"Local stream testpullStream enqueued for pushing to rtmp:\/\/localhost as testpushStream",
"status":"SUCCESS"
}
```

------

The JSON response for pullStream contains the following details:

- data – The data to parse
  - configID – The configuration ID for this command
  - emulateUserAgent – This is the string that the EMS uses to identify itself with the other server.  It can be modified so that EMS identifiesitself as, say, a Flash Media Server
  - forceTcp – Whether TCP MUST be used, or if UDP can be used
  - httpProxy - May either be IP:Port combination orself
  - keepAlive – If true, the stream will attempt to reconnect if the connection is severed
  - localStreamName – The local name for the stream
  - operationType – The type of operation
  - pageUrl – A link to the page that originated the request (often unused)
  - rtmpAbsoluteTimeStamps – If true, forces the timestamps to be absolute when using RTMP
  - sendChunkSizeRequest – Indicates whether theRTMP stream will or will not send a “Set Chunk Length” message
  - swfUrl – The location of the Flash Client thatis generating the stream (if any)
  - tcUrl – An RTMP parameter that is essentially acopy of the URI
  - tos – Type of Service network flag
  - ttl – Time To Live network flag
  - targeturi – Contains key/value pairs describing the source stream’s URI
    - document – The document name of the sourcestream
    - documentPath – The document path of the sourcestream
    - documentWithFullParameters – The document name with parameters of the source stream
    - fullDocumentPath - The document path of thedestination stream
    - fullDocumentPathWithParameters - The documentpath with parameters of the destination stream
    - fullParameters – The parameters for the sourcestream’s URI
    - fullUri – The full URI of the source stream
    - fullUriWithAuth – The full URI with authenticationof the source stream
    - host – Name of the source stream’s host
    - ip – IP address of the source stream’s host
    - originalUri – The source stream’s URI where itwas generated
    - parameters – Parameters for the source stream’sURI (if any)
    - password – Password for authenticating thesource stream (if required)
    - port – Port used by the source stream
    - portSpecified – True if the port for the sourcestream is specified
    - scheme – The protocol used by the source stream
    - userName – The user name for authenticating thesource stream (if required)


- description– Describes the result of parsing/executing the command


- status– `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
