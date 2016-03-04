---
layout: post
title: pullStream
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: pullstream
---

This will try to pull in a stream from an external source. Once a stream has been successfully pulled it is assigned a “local stream name” which can be used to access the stream from the EMS.

This function has the following parameters:

|    Parameter Name     |                Mandatory                 |        Default Value        | Description                              |
| :-------------------: | :--------------------------------------: | :-------------------------: | ---------------------------------------- |
|          uri          |                   true                   |           *null*            | TheURI of the external stream. Can be RTMP, RTSP or unicast/multicast (d) mpegts |
|       keepAlive       |                  false                   |          1 *true*           | If `keepAlive` is set to 1, the server will attempt to reestablish connection with astream source after a connection has been lost. The reconnect will be attemptedonce every second |
|    localStreamName    |                  false                   |         *computed*          | If provided, the stream will be given this name. Otherwise, a fallback techniqueis used to determine the stream name (based on the URI) |
|       forceTcp        |                  false                   |          1 *true*           | If 1 and if the stream is RTSP, a TCP connection will be forced.  Otherwise the transport mechanism will benegotiated (UDP or TCP) |
|         tcUrl         |                  false                   |    *zero-length string*     | When specified, this value will be used to set the TC URL in the initial RTMPconnect invoke |
|        pageUrl        |                  false                   |    *zero-length string*     | When specified, this value will be used to set the originating web page address in the initial RTMP connect invoke |
|        swfUrl         |                  false                   |    *zero-length string*     | When specified, this value will be used to set the originating swf URL in the initial RTMP connect invoke |
|      rangeStart       |                  false                   |             -2              | For RTSP and RTMP connections.  A value from which the playback should start expressed in seconds. There are 2 special values: -2 and -1. For more information, please read about start/len parameters here: [http://livedocs.adobe.com/flashmediaserver/3.0/hpdocs/help.html?content=00000185.html](http://livedocs.adobe.com/flashmediaserver/3.0/hpdocs/help.html?content=00000185.html) |
|       rangeEnd        |                  false                   |             -1              | The length in seconds for the playback. -1 is a special value. For more information, please read about start/len parameters here: [http://livedocs.adobe.com/flashmediaserver/3.0/hpdocs/help.html?content=00000185.html](http://livedocs.adobe.com/flashmediaserver/3.0/hpdocs/help.html?content=00000185.html) |
|          ttl          |                  false                   | *operating system supplied* | Sets the IP_TTL (time to live) option on the socket |
|          tos          |                  false                   | *operating system supplied* | Sets the IP_TOS (Type of Service) option on the socket |
| rtcpDetectionInterval |                  false                   |             10              | How much time (in seconds) should the server wait for RTCP packets before declaring the RTSP stream as a RTCP-less stream |
|   emulateUserAgent    |                  false                   |     *EvoStream message*     | When specified, this value will be used as the user agent string. It is meaningful only for RTMP |
|        isAudio        |    trueif uri is RTP, otherwise false    |          1 *true*           | If 1 and if the stream is RTP, it indicates that the currently pulled stream is an audio source. Otherwise the pulled source is assumed as a video source |
|    audioCodecBytes    | true if uri is RTP and isAudio is true, otherwise false |    *zero-length string*     | The audio  codec setup of this RTP stream if it is audio. Represented as hex format  without '0x' or 'h'. *For example:  audioCodecBytes=1190* |
|       spsBytes        | true if uri is RTP and isAudio is false, otherwise false |    *zero-length string*     | The video SPS  bytes of this RTP stream if it is video. It should be base 64 encoded. |
|       ppsBytes        | true if uri is RTP and isAudio is false, otherwise false |    *zero-length string*     | The video PPS bytes of this RTP stream if it is video. It should be base 64 encoded |
|         ssmIp         |                  false                   |    *zero-length string*     | The source IP from source-specific-multicast. Only usable when doing UDP based pull |
|       httpProxy       |                  false                   |    *zero-length string*     | This parameter has two valid values: **IP:Port** – This value combination specifies an RTSP HTTP Proxy from which the RTSP stream should be pulled from **Self** - Specifying “self” as the value implies pulling RTSP over HTTP |
|    sendRenewStream    |                  false                   |          0 *false*          | If true, the server will send RenewStream via SET_PARAMETER when a new client connects. Only valid for RTSP URIs |

The EMS provides several shorthand User Agent strings (not case-sensitive) for convenience:

| **emulateUserAgent**      | **Resolves as..**                        |
| ------------------------- | ---------------------------------------- |
| emulateUserAgent=evo      | EvoStreamMedia Server ([www.evostream.com](http://www.evostream.com)) |
| emulateUserAgent=FMLE     | FMLE/3.0 (compatible; FMSc/1.0)          |
| emulateUserAgent=wirecast | Wirecast/FM 1.0 (compatible;  FMSc/1.0)  |
| emulateUserAgent=flash    | MAC 11,3,300,265                         |

An example of the pullStream interface is:

`pullStream uri=rtsp://AddressOfStream keepAlive=1 localStreamname=RTSPteststream`

`pullStream uri=rtmp://AddressOfStream keepAlive=1 localStreamname=RTMPteststream`



Then, to access that stream via a flash player, the following URI can be used:

`rtsp://AddressOfEMS:5544/RTSPteststream` 

`rtmp://AddressOfEMS/live/RTSPteststream` 

------

**Example:**

**API Call:**

``` 
pullstreamuri=rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4 localStreamname=testpullstream
```

**JSON Response:**

``` 
{
"data":{
    "audioCodecBytes":"",
    "configId":1,
    "emulateUserAgent":"EvoStream Media Server (www.evostream.com) player",
    "forceTcp":false,
    "httpProxy":"",
    "isAudio":true,
    "keepAlive":true,
    "localStreamName":"testpullstream",
    "operationType":1,
    "pageUrl":"",
    "ppsBytes":"",
    "rangeEnd":-1,
    "rangeStart":-2,
    "rtcpDetectionInterval":10,
    "sendRenewStream":false,
    "spsBytes ":"",
    "ssmIp":"",
    "swfUrl":"",
    "tcUrl":"",
    "tos":256,
    "ttl":256,
    "uri":{
      "document":"mp4:sintel.mp4",
      "documentPath":"\/cfx\/st\/",
      "documentWithFullParameters":"mp4:sintel.mp4",
      "fullD ocumentPath":"\/cfx\/st\/mp4:sintel.mp4",
      "fullDocumentPathWithParameters":"\/cfx\/st\/mp4:sintel.mp4",
      "fullParameters":"",
      "fullUri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cf x\/st\/mp4:sintel.mp4",
      "fullUriWithAuth":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
      "host":"s2pchzxmtymn2k.cloudfront.net",
      "ip":"54.239.131.57",
      "original Uri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
      "parameters":{
          },
      "password":"",
      "port":1935,
      "portSpecified":false,
      "scheme":"rtmp",
      "userName":""
      }
},
"description":"Stream rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4 enqueued for pulling",
"status":"SUCCESS”
}
```

------

The JSON response for pullStream contains the following details:

- data – The data to parse
  - audioCodecBytes - The audio codec setup of thisRTP stream if it is audio
  - configID – The configuration ID for this command
  - emulateUserAgent – This is the string that the EMS uses to identify itself with the other server. It can be modified so that EMS identifies itself as, say, a Flash Media Server
  - forceTcp – Whether TCP MUST be used, or if UDP can be used
  - httpProxy - May either be IP:Port combination orself
  - isAudio - Indicates if the currently pulled stream is an audio source
  - keepAlive – If true, the stream will attempt to reconnect if the connection is severed
  - localStreamName – The local name for the stream
  - operationType – The type of operation
  - pageUrl – A link to the page that originated the request (often unused)
  - ppsBytes - The video PPS bytes of this RTP stream if it is video
  - rangeEnd - The length in seconds for the playback
  - rangeStart - A value from which the playback should start expressed in seconds
  - rtcpDetectionInterval – Used for RTSP. This is the time period the EMS waits to determine if an RTCP connection is available for the RTSP/RTP stream. (RTSP is used for synchronization between audio and video)
  - sendRenewStream – If 1, the server will `sendRenewStream` via SET_PARAMETER when a new client connects
  - spsBytes - The video SPS bytes of this RTP stream if it is video
  - ssmIp - The source IP from source-specific-multicast
  - swfUrl – The location of the Flash Client thatis generating the stream (if any)
  - tcUrl – An RTMP parameter that is essentially acopy of the URI
  - tos – Type of Service network flag
  - ttl – Time To Live network flag
  - uri – Contains key/value pairs describing thesource stream’s URI
    - document – The document name of the source stream
    - documentPath – The document path of the source stream
    - documentWithFullParameters – The document name with parameters of the source stream
    - fullDocumentPath - The document path of the destination stream
    - fullDocumentPathWithParameters - The document path with parameters of the destination stream
    - fullParameters – The parameters for the source stream’s URI
    - fullUri – The full URI of the source stream
    - fullUriWithAuth – The full URI with authentication of the source stream
    - host – Name of the source stream’s host
    - ip – IP address of the source stream’s host
    - originalUri – The source stream’s URI where it was generated
    - parameters – Parameters for the source stream’s URI (if any)
    - password – Password for authenticating the source stream (if required)
    - port – Port used by the source stream
    - portSpecified – True if the port for the source stream is specified
    - scheme – The protocol used by the source stream
    - userName – The user name for authenticating the source stream (if required)


- description– Describes the result of parsing/executing the command


- status– `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
