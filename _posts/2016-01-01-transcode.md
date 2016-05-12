---
layout: post
title: transcode
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: transcode
---

This function changes the compression characteristics of an audio and/or video stream. This function allows you to change the resolution of a source stream, change the bitrate of a stream, change a VP8 or MPEG2 stream into H.264 and much more. This function will also allow users to create overlays on the final stream as well as crop streams.

> **Transcoding requires SIGNIFICANT computing resources and will severely impact performance. A general guideline is that you can accomplish one transcoding job per CPU core for HD streams.**

**IMPORTANT NOTES:**

- For any parameter that is pluralized, you may specify one value, or multiple. Multiple values must be separated by only a comma (comma-delimited). Specifying multiple values indicates multiple new streams will be created.
- There must be the same number of values for all pluralized parameters. Oder is important: all first values are grouped together to make the first stream, all second parameters are grouped to make the second stream, etc…
- Video related parameters are ignored if the parameter ***videoBitrates*** is not specified.
- Audio related parameters are ignored if the parameter ***audioBitrates*** is not specified.

This function has the following parameters:

|     **Parameter Name**      | **Mandatory** |         **Default Value**          | **Description**                          |
| :-------------------------: | :-----------: | :--------------------------------: | ---------------------------------------- |
|           source            |     true      |               *null*               | Can be a URI or a local stream name from EMS |
|        destinations         |     true      |               *null*               | The target URI(s) or stream name(s) of the transcoded stream. If only a name is given, it will be pushed back to the EMS |
|      targetStreamNames      |     false     |   transcoded\_xxxx *(timestamp)*   | The name of the stream(s) at destination(s). If not specified, and a full URI is provided to destinations, name will have a time stamped value |
|          groupName          |     false     | transcoded\_group\_xxxx *(random)* | The group name assigned to this process. If not specified, groupName will have a random value |
|        videoBitrates        |     false     |       input video's bitrate        | Target output video bitrate(s) (in bits/s, append 'k' to value for kbits/s). Accepts the value 'copy' to copy the input bitrate. An empty value passed would mean no video |
|         videoSizes          |     false     |         input video's size         | Target output video size(s) in wxh (width x height) format. IE: 240x480 |
| videoAdvancedParamsProfiles |     false     |               *null*               | Name of video profile template that will be used. See the contents of 'evo-avconv-presets' folder for sample file presets |
|        audioBitrates        |     false     |       input audio's bitrate        | Target output audio bitrate(s) (in bits/s, append 'k' to value for kbits/s). Accepts the value 'copy' to copy the input bitrate. An empty value passed would mean no audio |
|     audioChannelsCounts     |     false     |    input audio's channel count     | Target output audio channel(s) count(s). Valid values are 1 (mono), 2 (stereo), and so on. Actual supported channel count is dependent on the number of input audio channels. |
|      audioFrequencies       |     false     |      input audio's frequency       | Target output audio frequency(ies) (in Hz, append 'k' to value for kHz) |
| audioAdvancedParamsProfiles |     false     |               *null*               | Name of audio profile template that will be used |
|          overlays           |     false     |               *null*               | Location of the overlay source(s) to be used. These are transparent images (normally in PNG format) that have the same or smaller size than the video. Image is placed at the top-left position of the video |
|          croppings          |     false     |               *null*               | Target video cropping position(s) and size(s) in 'left : top : width : height' format (e.g. 0:0:200:100. Positions are optional (200:100 for a centered cropping of 200 width and 100 height in pixels). Values are limited to the actual size of the video |
|          keepAlive          |     false     |              1 *true*              | If keepAlive is set to 1, the server will restart transcoding if it was previously activated |
|         commandFlags        |     false     |               *null*               | Other commands to the transcode process that are not supported by the baseline transcode command |

An example of the transcode command is:

``` 
transcode source=rtmp://<RTMP server>/live/streamname groupName=group videoBitrates=200k destinations=stream1
```

------

## **Transcode Examples**

To transcode an RTMP source into different video bitratesand send back to EMS

``` 
transcode source=rtmp://<RTMP server>/live/streamname groupName=group videoBitrates=100k,200k,300k destinations=stream100,stream200,stream300
```

To transcode an existing EMS stream into a different audio channel count and send to an RTMP server

``` 
transcode source=stream1 groupName=group audioBitrates=copy audioChannelsCounts=1 destinations=rtmp://<RTMP server 2> targetStreamNames=streamMono
```

To use files as input and/or output

``` 
transcode source=file://C:\videos\test.mp4 groupName=group videoBitrates=100k audioBitrates=copy destinations=file://C:\videos\out.mp4
```

To force TCP for inbound RTSP

``` 
transcode source=rtsp://<RTSP server>/live/streamname groupName=group videoBitrates=copy videoSizes=360x200 $EMS_RTSP_TRANSPORT=tcp
```

To use command flags

``` 
transcode source=rtmp://<RTSP server>/live/streamname groupName=group destinations=destinationStream commandFlags="<command>"
``` 

To stop a running transcoding process(es)

``` 
removeConfig groupName=group
```

------

## Transcoding Customizations:

To configure the transcoder script settings, edit the file **config.lua** and edit the following entries as needed:

``` 
transcoder = {
	scriptPath="emsTranscoder",
	srcUriPrefix="rtsp://localhost:5544/",
	dstUriPrefix="-f flv tcp://localhost:6666/"
},
```

To change the location of the actual trancoder binary, edit the file **emsTranscoder.sh** (linux/unix) and **emsTranscoder.cmd** (windows); and change the following line:

`TRANSCODER\_BIN=/usr/bin/evo-avconv` (linux/unix)

`set TRANSCODER\_BIN= ..\\evo-avconv.exe` (windows)

------

**Example:**

**API Call:**

``` 
transcode source=rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4 groupName=group videoBitrates=200k destinations=stream1
```

**JSON Response:**

``` 
{
"data":{
    "audioAdvancedParamsProfiles":["na"],
    "audioBitrates":["na"],
    "audioChannelsCounts":["na"],
    "audioFrequencies":["na"],
    "croppings":["na"],
    "destinations":["stream1"],
    "dstUriPrefix":"-f flv tcp:\/\/localhost:6666\/",
    "emsTargetStreamName":"stream1",
    "fullBinaryPath":"C:\\EvoStream\\emsTranscoder.bat",
    "groupName":"group",
    "keepAlive":true,
    "localStreamName":"",
    "overlays":["na"],
    "source":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
    "srcUriPrefix":"rtsp:\/\/localhost:5544\/",
    "targetStreamNames":["stream1"],
    "videoAdvancedParamsProfiles":["na"],
    "videoBitrates":["200k"],
    "videoSizes":["na"]
},
"description":"Transcoding successfully started.",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - audioAdvancedParamsProfiles - An array of strings specifying the name of profile presets to be used for audio
  - audioBitrates - An array of integers for target audio output bitrates
  - audioChannelsCounts - An array of values for the target number of audio channels
  - croppings - An array of values for the target cropping positions and size
  - destinations - An array of target URIs or stream names
  - dstUriPrefix - Default destination if destination is a stream name
  - emsTargetStreamName - Target stream name used internally by EMS
  - fullBinaryPath - Actual location of the transcoder binary
  - groupName - Name of the group associated with this transcoding process
  - keepAlive - Transcoding will restart if previously activated
  - localStreamName - Actual EMS stream name of source (if given)
  - overlays - An array of locations for the images to be used as overlays
  - source - The actual stream/file to be used as input for transcoding
  - srcUriPrefix - Default source if given source is a stream name
  - targetStreamNames - An array of the target stream names to be used at the destination
  - videoAdvancedParamsProfiles - An array of strings specifying the name of profile presets to be used for video
  - videoBitrates - An array of values for target video output bitrates
  - videoSizes - An array of values for target video sizes


- description – Describes the result of parsing/executing the command
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not  
