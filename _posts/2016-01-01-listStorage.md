---
layout: post
title: listStorage
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: liststorage
---

Lists currently available media storage locations.

This function has no parameters.

------

**Example:**

**API Call:**

``` 
listStorage 
```

**JSON Response:**

``` 
{
"data":[
    {
    "clientSideBuffer":15,
    "description":"Default media storage",
    "enableStats":false,
    "externalSeekGenerator":false,
    "keyframeSeek":true,
    "maxPlaylistFileSize":4096,
    "mediaFolder":"\/home\/qatest\/Desktop\/evostreamms-1.7.0.4242-x86_64-Ubuntu_14.04\/media\/",
    "metaFolder":"\/home\/qatest\/Desktop\/evostreamms-1.7.0.4242-x86_64-Ubuntu_14.04\/media\/",
    "name":"0x00000001",
    "seekGranularity":1000
    }
    ],
"description":"Available storages",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - clientSideBuffer – How much data should be maintained on the client side when a file is played from this storage
  - description – Description given to this storage. Used to better identify the storage
  - enableStats – If true, \*.stats files are going to be generated once the media files are used
  - externalSeekGenerator – If true, \*.seek and \*.meta files are going to be generated by another external tool
  - keyframeSeek – If true, the seek/meta files are going to be generated having only keyframe seek points
  - mediaFolder – The path to the media folder
  - metaFolder – Path to the folder which is going to contain all the seek/meta files. If missing, the seek/meta files are going to be generated inside the media folder
  - name – Name given to this storage. Used to better identify the storage.
  - seekGranularity – Sets the granularity for the seek files
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
