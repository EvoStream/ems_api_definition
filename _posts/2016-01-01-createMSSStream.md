---
layout: post
title: createMSSStream
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: create_mss_stream
---

Create a Microsoft Smooth Stream (MSS) out of an existing H.264/AAC stream. Smooth Streaming was developed by Microsoft to compete with other adaptive streaming technologies.

This function has the following parameters:

|  **Parameter Name**  | **Mandatory** |            **Default Value**             | **Description**                          |
| :------------------: | :-----------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   |     true      |                  *null*                  | The stream(s) that will be used as the input. This is a comma-delimited list of active stream names (local stream names) |
|     targetFolder     |     true      |                  *null*                  | The folder where all the manifest and fragment files will be stored. This folder must be accessible by the MSS clients. It is usually in the web-root of the server |
|      bandwidths      |     false     |                    0                     | The corresponding bandwidths for each stream listed in `localStreamNames`. Again, this can be a comma-delimited list |
|      groupName       |     false     |       *mss\_group\_xxxx (random)*        | The name assigned to the MSS stream or group. If the `localStreamNames` parameter contains only one entry and groupName is not specified, groupName will have the value of the input stream name |
|     playlistType     |     false     |                Appending                 | Either \`appending\` or \`rolling\`      |
|    playlistLength    |     false     |                    10                    | The number of fragments before the server starts to overwrite the older fragments. Used only when `playlistType` is 'rolling'. Ignored otherwise |
|     manifestName     |     false     |              manifest.ismc               | The manifest file name                   |
|     chunkLength      |     false     |                    10                    | The length (in seconds) of fragments to be made |
|      chunkOnIDR      |     false     |                0 *false*                 | If 1 (true), chunking is performed ONLY on IDR. Otherwise, chunking is performed whenever chunk length is achieved |
|      keepAlive       |     false     |                 1 *true*                 | If 1 (true), the EMS will attempt to reconnect to the stream source if the connection is severed |
| overwriteDestination |     false     |                 1 *true*                 | If 1 (true), it will allow overwrite of destination files |
| staleRetentionCount  |     false     | *If not specified, it will have the value of playlistLength* | How many old files are kept besides the ones present in the current version of the playlist. Only applicable for rolling playlists |
|  cleanupDestination  |     false     |                0 *false*                 | If 1 (true), all manifest and fragment files in the target folder will be removed before MSS creation is started |
|       ismType        |     false     |                   ismc                   | Either **ismc** for serving content to client or **isml** for serving content to smooth server |
|        isLive        |     false     |                 1 *true*                 | If true, creates a live MSS stream, otherwise set to 0 for VOD |
|   publishingPoint    |     false     |                  *none*                  | This parameter is needed when `ismType=isml`, it is the REST URI where the mss contents will be ingested |
|      ingestMode      |     false     |                  single                  | Either `single` for a non looping ingest or `loop` for looping an ingest |

An example of the createMSSStream interface is:

To playback the created MSS stream, use a Smooth Streaming player such as one of the following:

- [*http://smf.cloudapp.net/healthmonitor*](http://smf.cloudapp.net/healthmonitor)
- [*http://playready.directtaps.net/pr/doc/slee/*](http://playready.directtaps.net/pr/doc/slee/)

Enter the following stream URL: `http://My_IP_or_Domain/group1/manifest`

In other words: `http://my_web_server/MSS_group_name/manifest_file_name`

------

**Example:**

**API Call:**

``` 
createMSSStream localstreamnames=testpullStream targetfolder=../evo-webroot groupname=mss
```

**JSON Response:**

``` 
{
"data":{
    "bandwidths":[0],
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "configIds":[10],
    "groupName":"mss",
    "ingestMode":"single",
    “isLive”:”true”,
    "ismType":"ismc",
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "manifestName":"manifest.ismc",
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistType":"appending",
    "publishingPoint":"http://192.168.2.35:88/liveingest.isml",
    "staleRetentionCount":10,
    "targetFolder":"..\/evo-webroot"
},
"description":"MSS stream created",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse
  - bandwidths – An array of integers specifying the bandwidths used for streaming
  - chunkLength – The length (in seconds) of each playlist element (.ismc files)
  - chunkOnIdr – If true, chunking was made on IDR boundary
  - cleanupDestination – If true, MSS files at the target folder were deleted before MSS creation began
  - configIds - The configuration IDs for this command
  - groupName – The name of the target folder where MSS files will be created
  - ingestMode – The type of ingest
  - isLive - Creates a live MSS stream, otherwise set to 0 for VOD
  - keepAlive – If true, the stream will attempt to reconnect if the connection is severed
  - localStreamNames – An array of local names for the streams
  - manifestName – The file name of the manifest file. If blank, defaults to ‘manifest’
  - overwriteDestination – If true, overwriting of destination files during MSS creation is allowed
  - playlistLength – The number of fragments before the server starts to overwrite the older fragments. Useful only for \`rolling\` playlistType
  - playlistType – Either \`appending\` or \`rolling\`
  - publishingPoint - It is the REST URI where the mss contents will be ingested
  - staleRetentionCount – The number of old files kept besides the ones listed in the current version of the manifest. Only applicable to rolling playlist type
  - targetFolder – The folder where all the manifest and chunk files are stored


- description – Describes the result of parsing/executing the command
  
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
  
  ​