---
layout: post
title: getConfigInfo
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: getconfiginfo
---

Returns the information of the stream by the configId.

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|         id         |     true      |      *null*       | The `configId` of the configuration to get some information |

------

**Example:**

**API Call:**

``` 
getConfigInfo id=1
```

**JSON Response:**

``` 
{
"data":{
    "AESKeyCount":5,
    "audioOnly":false,
    "bandwidth":0,
    "chunkBaseName":"segment",
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "cleanupOnClose":false,
    "configId":1,
    "createMasterPlaylist":true,
    "drmType":"none",
    "fileLength":0,
    "groupName":"HLS",
    "groupTargetFolder":"..\/evo-webroot\\HLS\\",
    "hlsResume":false,
    "hlsVersion":3,
    "keepAlive":true,
    "localStreamName":"bunny",
    "masterPlaylistPath":"..\/evo-webroot\\HLS\\playlist.m3u8",
    "maxChunkLength":0,
    "offsetTime":0,
    "operationType":3,
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistName":"playlist.m3u8",
    "playlistType":"appending",
    "staleRetentionCount":10,
    "startOffset":0,
    "status":{
        "current":{
            "code":0,
            "description":"Streaming",
            "timestamp":1448958829,
            "uniqueStreamId":10
            },
        "previous":{
            "code":3,
            "description":"Connected",
            "timestamp":1448958829,
            "uniqueStreamId":0
            }
        },
    "targetFolder":"..\/evo-webroot\\HLS\\test_sintel",
    "timestamp":1448955776495.1621,
    "useByteRange":false,
    "useSystemTime":false
},
"description":"Configuration Info",
"status":"SUCCESS"
}
```

------

The JSON response for pullStream contains the following details:

- data – The information about the configuration

