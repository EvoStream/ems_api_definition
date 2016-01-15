---
layout: post
title: generateServerPlaylist
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: generate_server_playlist
---

Will create a server-side playlist with the specified sources.

This function has the following parameters:

| **Parameter Name** | **Mandatory** |  **Default Value**   | **Description**                          |
| :----------------: | :-----------: | :------------------: | ---------------------------------------- |
|      sources       |     true      |        *null*        | The stream or media file source(s) to be used as input. This is a comma-delimited list of active stream names or media files |
|     pathToFile     |     true      |        *null*        | The path to the output server playlist file |
|   sourceOffsets    |     false     | *zero-length string* | The corresponding offsets for the source streams/files listed in sources. This can be a comma-delimited list |
|     durations      |     false     | *zero-length string* | The corresponding durations for the source streams/files listed in sources. This can be a comma-delimited list |

**sourceOffsets** and **durations** specify what part of the source stream/file to play for each of the items listed and for how long. The values for **sourceOffsets** and **durations** are defined specifically as follows:

- **sourceOffsets** specifies the starting position, in seconds, for each of the source stream/file. This parameter can also be used to indicate whether the stream is live or a media file.
  - -2 means that the EMS will look for a live stream with the source name specified. If a live stream is not found, it will attempt to play a media file with the source name. If a media file with that name and path cannot be found the EMS will wait for a live stream to become available.
  - -1 implies that the source is explicitly a live stream. If no live stream is found, the EMS waits indefinitely if *duration* is set to -1. If *duration* is another value the EMS will wait *duration* seconds before moving to the next item in the playlist.
  - 0 or a positive number implies that the specified source is a media file. The EMS will start playback *sourceOffset* seconds from the beginning of the file. If no file is found the playlist item is skipped.
  - Any negative number other than -1 or -2 will be assumed to be -2
- **durations** specifies the length of the playback of each of the sources in seconds.
  - All positive numbers will cause the EMS to play the stream/file for *duration* seconds or until the end of the media file or live stream, whichever comes first.
  - 0 means that only a single frame of the stream/file will be played.
  - -1 means that the EMS will play a live stream until it is no longer available or a media file until its end.
  - -2 will play media files until their end (same as -1 behavior). For live sources, it will play the live stream until that stream is no longer available. When the source stream is lost the EMS shall move to the next item in the playlist.
  - Any negative number other than -1 or -2 will be assumed to be -2.

An example of the generateServerPlaylist interface is:

``` 
generateServerPlaylist sources=File1.mp4,livestream1,File2.mp4,livestream1 pathToFile=/MyFileDirectory/MyPlaylist.lst sourceOffsets=0,-1,0,-1 durations=-1,60,-1,-1
```

------

**Example:**

**API Call:**

``` 
generateServerPlaylist sources=bunnyA.mp4,bunnyB.mp4 pathToFile=../media/testPlaylist sourceOffsets=0,-1 durations=-1,60
```

**JSON Response:**

``` 
{
"data":{
    "durations":[-1,60],
    "pathToFile":"..\/media\/testPlaylist",
    "sourceOffsets":[0,-1],
    "sources":["bunnyA.mp4","bunnyB.mp4"]
},
"description":"Server playlist written to ..\/media\/testPlaylist.lst",
"status":"SUCCESS"
}
```

------

The JSON response for generateServerPlaylist contains the following details:

- data – The data to parse
  - durations – An array of durations for each stream/file in the list, expressed in seconds
  - pathToFile – The full path and filename of the playlist file
  - sourceOffsets – An array of offsets for each stream/file in the list
  - sources – An array of streams or media files
- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
