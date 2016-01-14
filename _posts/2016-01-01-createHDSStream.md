---
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: createHDSStream
---

# createHDSStream

Create an HDS (HTTP Dynamic Streaming) stream out of an existing H.264/AAC stream. HDS is used to stream standard MP4 media over regular HTTP connections. HDS is a new technology developed by Adobe in response to HLS from Apple.

This function has the following parameters:

|  **Parameter Name**  | **Mandatory** |            **Default Value**             | **Description**                          |
| :------------------: | :-----------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   |     true      |                  *null*                  | The stream(s) that will be used as the input. This is a comma-delimited list of active stream names (local stream names) |
|     targetFolder     |     true      |                  *null*                  | The folder where all the manifest (\*.f4m) and fragment (f4v\*) files will be stored. This folder must be accessible by the HDS clients. It is usually in the web-root of the server |
|      bandwidths      |     false     |                    0                     | The corresponding bandwidths for each stream listed in localStreamNames. Again, this can be a comma-delimited list |
|    chunkBaseName     |     false     |                   f4v                    | The base name used to generate the fragments. The default value follows this format: f4vSeg1-FragXXX |
|     chunkLength      |     false     |                    10                    | The length (in seconds) of fragments to be made. Minimum value is 1 (second) |
|      chunkOnIDR      |     false     |                 1 *true*                 | If true, chunking is performed ONLY on IDR. Otherwise, chunking is performed whenever chunk length is achieved |
|      groupName       |     false     | *(it will be a random name in the form of hds\_group\_xxxx)* | The name assigned to the HDS stream or group. If the localStreamNames parameter contains only one entry and groupName is not specified, groupName will have the value of the input stream name |
|      keepAlive       |     false     |                 1 *true*                 | If true, the EMS will attempt to reconnect to the stream source if the connection is severed |
|     manifestName     |     false     |         defaults to stream name          | The manifest file name                   |
| overwriteDestination |     false     |                 1 *true*                 | If true, it will allow overwrite of destination files |
|     playlistType     |     false     |                appending                 | Either \`appending\` or \`rolling\`      |
|    playlistLength    |     false     |                    10                    | The number of fragments before the server starts to overwrite the older fragments. Used only when playlistType is \`rolling\`. Ignored otherwise |
| staleRetentionCount  |     false     | If not specified, it will have the value of playlistLength | How many old files are kept besides the ones present in the current version of the playlist. Only applicable for rolling playlists |
| createMasterPlaylist |     false     |                 1 *true*                 | If true, a master playlist will be created |
|  cleanupDestination  |     false     |                0 *false*                 | If 1 (true), all manifest and fragment files in the target folder will be removed before HDS creation is started |

An example of the createHDSStream interface is:

The corresponding link to use on an HDS player (e.g. OSMF) to pull this stream would then be:

In other words:  `http://my\_web\_server/HDS\_group\_name/manifest\_file\_name`

------

**Example:**

**API Call:**

``` 
createHDSStream localstreamnames=testpullStream targetfolder=../evo-webroot groupname=hds playlisttype=rolling
```

**JSON Response:**

``` 
{
"data":{
    "bandwidths":[0],
    "chunkBaseName":"f4v",
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "configIds":[9],
    "createMasterPlaylist":true,
    "groupName":"hds",
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "manifestName":"",
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistType":"rolling",
    "staleRetentionCount":10,
    "targetFolder":"..\/evo-webroot"
},
"description":"HDS stream created",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse.
  - bandwidths – An array of integers specifying the bandwidths used for streaming
  - chunkBaseName – The base name or prefix used for naming the output HDS chunks
  - chunkLength – The length (in seconds) of each playlist element (.f4m files)
  - chunkOnIdr – If true, chunking was made on IDR boundary
  - cleanupDestination – If true, HDS files at the target folder were deleted before HDS creation began
  - configIds - The configuration IDs for this command
  - createMasterPlaylist – If true, a master playlist is created
  - groupName – The name of the target folder where HDS files will be created
  - keepAlive – If true, the stream will attempt to reconnect if the connection is severed
  - localStreamNames – An array of local names for the streams
  - manifestName – The file name of the manifest file (\*.f4m). If blank, defaults to stream name
  - overwriteDestination – If true, overwriting of destination files during HDS creation is allowed
  - playlistLength – The number of fragments before the server starts to overwrite the older fragments. Useful only for \`rolling\` playlistType
  - playlistType – Either \`appending\` or \`rolling\`.
  - staleRetentionCount – The number of old files kept besides the ones listed in the current version of the playlist. Only applicable for rolling playlists
  - targetFolder – The folder where all the manifest (\*.f4m) and fragment (f4v\*) files are stored


- description – Describes the result of parsing/executing the command.
  
- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not.
  
  ​
