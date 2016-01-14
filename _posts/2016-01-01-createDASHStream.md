---
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: createDASHStream
---

# createDASHStream

Create Dynamic Adaptive Streaming over HTTP (DASH) out of an existing H.264/AAC stream. DASH was developed by the Moving Picture Experts Group (MPEG) to establish a standard for HTTP adaptive-bitrate streaming that would be accepted by multiple vendors and facilitate interoperability.

This function has the following parameters:

|  **Parameter Name**  | **Mandatory** |            **Default Value**             | **Description**                          |
| :------------------: | :-----------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   |     true      |                  *null*                  | The stream(s) that will be used as the input. This is a comma-delimited list of active stream names (local stream names) |
|     targetFolder     |     true      |                  *null*                  | The folder where all the manifest and fragment files will be stored. This folder must be accessible by the DASH clients. It is usually in the web-root of the server |
|      bandwidths      |     false     |                    0                     | The corresponding bandwidths for each stream listed in localStreamNames. Again, this can be a comma-delimited list |
|      groupName       |     false     |       *dash\_group\_xxxx (random)*       | The name assigned to the DASH stream or group. If the localStreamNames parameter contains only one entry and groupName is not specified, groupName will have the value of the input stream name |
|     playlistType     |     false     |                appending                 | Either \`appending\` or \`rolling\`      |
|    playlistLength    |     false     |                    10                    | The number of fragments before the server starts to overwrite the older fragments. Used only when playlistType is 'rolling'. Ignored otherwise |
|     manifestName     |     false     |               manifest.mpd               | The manifest file name                   |
|     chunkLength      |     false     |                    10                    | The length (in seconds) of fragments to be made |
|      chunkOnIDR      |     false     |                 1 *true*                 | If 1 (true), chunking is performed ONLY on IDR. Otherwise, chunking is performed whenever chunk length is achieved |
|      keepAlive       |     false     |                 1 *true*                 | If 1 (true), the EMS will attempt to reconnect to the stream source if the connection is severed |
| overwriteDestination |     false     |                 1 *true*                 | If 1 (true), it will allow overwrite of destination files |
| staleRetentionCount  |     false     | *If not specified, it will have the value of playlistLength* | How many old files are kept besides the ones present in the current version of the playlist. Only applicable for rolling playlists |
|  cleanupDestination  |     false     |                0 *false*                 | If 1 (true), all manifest and fragment files in the target folder will be removed before DASH creation is started |
|    dynamicProfile    |     false     |                 *1 true*                 | Set this parameter to 1 (default) for a live DASH, otherwise set it to 0 for a VOD |

An example of the createDASHStream interface is:

``` 
createDASHStream localstreamnames=dashtest bandwidth=128 targetfolder=/MyWebRoot/ groupname=group1 rolling=true rollingLimit=10 chunkLength=10
```

To playback the created DASH stream, use a DASH player such as the following:

``` 
http://digitalprimates.net/dash/dashTest.html
```

This player is the most stable for EMS DASH playback but it doesn’t support live profile for EMS DASH.

Enter the following stream URL:

In other words: `http://my\_web\_server/dash\_group\_name/manifest\_file\_name`

An alternative DASH player, GPAC Osmo4, can be downloaded from here:

[*http://gpac.wp.mines-telecom.fr/downloads/gpac-nightly-builds/*](http://gpac.wp.mines-telecom.fr/downloads/gpac-nightly-builds/)

This player supports MPEG-DASH live profile for EMS DASH.

Another DASH player, Dash.as, can be downloaded from here:

*[https://github.com/castlabs/dashas](https://github.com/castlabs/dashas)*

------

**Example:**

**API Call:**

``` 
createDASHStream localstreamnames=testpullStream targetfolder=../evo-webroot groupname=dash
```

**JSON Response:**



``` 
{
"data":{
    "bandwidths":[0],
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "configIds":[11],
    "dynamicProfile":true,
    "groupName":"dash",
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "manifestName":"manifest.mpd",
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistType":"appending",
    "staleRetentionCount":10,
    "targetFolder":". .\/evo-webroot"
},
"description":"DASH stream created",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse.
  - bandwidths – An array of integers specifying the bandwidths used for streaming
  - chunkLength – The length (in seconds) of each playlist element (.mpd files)
  - chunkOnIdr – If true, chunking was made on IDR boundary
  - cleanupDestination – If true, DASH files at the target folder were deleted before DASH creation began
  - configIds - The configuration IDs for this command
  - dynamicProfile – Tells if the DASH stream is a live or VOD
  - groupName – The name of the target folder where DASH files will be created
  - keepAlive – If true, the stream will attempt to reconnect if the connection is severed
  - localStreamNames – An array of local names for the streams.
  - manifestName – The file name of the manifest file. If blank, defaults to ‘manifest’
  - overwriteDestination – If true, overwriting of destination files during DASH creation is allowed
  - playlistLength – The number of fragments before the server starts to overwrite the older fragments. Useful only for \`rolling\` playlistType
  - playlistType – Either \`appending\` or \`rolling\`
  - staleRetentionCount – The number of old files kept besides the ones listed in the current version of the manifest. Only applicable to rolling playlist type
  - targetFolder – The folder where all the manifest and chunk files are stored


- description – Describes the result of parsing/executing the command.
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not.
