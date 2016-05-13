---
layout: post
title: createHLSStream
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: createhlsstream
---

Create an HTTP Live Stream (HLS) out of an existing H.264/AAC stream.  HLS is used to stream live feeds to iOS devices such as iPhones and iPads.  

This function has the following parameters:

|    Parameter Name    | Mandatory |              Default Value               | Description                              |
| :------------------: | :-------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   |   true    |                  *null*                  | The stream(s) that will be used as the input. This is a comma-delimited list of active stream names (local stream names) |
|     targetFolder     |   true    |                  *null*                  | The folder where all the *.ts/*.m3u8 files will be stored. This folder must be accessible by the HLS clients. It is usually in the web-root of the server |
|      keepAlive       |   false   |                 1 *true*                 | If true, the EMS will attempt to reconnect to the stream source if the connection is severed |
| overwriteDestination |   false   |                 1 *true*                 | If true, it will force overwrite of destination files |
| staleRetentionCount  |   false   | *if not specified, it will have the value of playlistLength* | The number of old files kept besides the ones listed in the current version of the playlist. Only applicable for rolling playlists |
| createMasterPlaylist |   false   |                 1 *true*                 | If true, a master playlist will be created |
| cleanupDestination  |   false   |                0 *false*                 | If  true, all *.ts and *.m3u8 files in the target folder will be removed before HLS creation is started |
|      bandwidths      |   false   |                    0                     | The corresponding bandwidths for each stream listed in `localStreamNames`. Again, this can be a comma-delimited list |
|      groupName       |   false   | *it will be a random name in the form of hls_group_xxxx* | The name assigned to the HLS stream or group. If the `localStreamNames` parameter contains only one entry and `groupName` is not specified, `groupName` will have the value of the input stream name |
|     playlistType     |   false   |                appending                 | Either appending or rolling              |
|    playlistLength    |   false   |                    10                    | The length (number of elements) of the playlist. Used only when playlistType is **rolling**. Ignored otherwise |
|     playlistName     |   false   |              playlist.m3u8               | The file name ofthe playlist (*.m3u8)    |
|     chunkLength      |   false   |                    10                    | The length (in seconds) of each playlist element (*.ts file). Minimum value is 1 (second) |
|    maxChunkLength    |   false   |                    0                     | This parameter represents the maximum length, in seconds, the EMS will allow anysingle chunk to be. This is primarily in the case of `chunkOnIDR=true` where the EMS will wait for the next key-frame. If the `maxChunkLength` is less than `chunkLength`, the parameter shall be ignored |
|    chunkBaseName     |   false   |                 segment                  | The base name used to generate the *.ts chunks |
|      chunkOnIDR      |   false   |                 1 *true*                 | If true, chunking is performed ONLY on IDR. Otherwise, chunking is performed whenever chunk length is achieved |
|       drmType        |   false   |                   none                   | Sets the type of DRM encryption to use.  Options are: **none** (no encryption), **evo** (AES Encryption), **SAMPLE-AES** (Sample-AES), **verimatrix** (Verimatrix DRM). For Verimatrix DRM, the “drm” section of the config.lua file must be active and properly configured |
|     AESKeyCount      |   false   |                    5                     | Specifies the number of keys that will be automatically generated and rotated over while encrypting this HLS stream |
|      audioOnly       |   false   |                0 *false*                 | Specifies if the resulting stream will be audio only. A value of 1(true) will result in a stream without video |
|      hlsResume       |   false   |                0 *false*                 | If true, HLS will resume in appending segments to previously created childplaylist even in cases of EMS shutdown or cut off stream source |
|     cleanupOnClose     |   false   |                0 *false*                 | If true, corresponding hls files to a stream will be deleted if the said stream is removed or shut down or disconnected|
|     useByteRange     |   false   |                0 *false*                 | If true, will use the EXT-X-BYTERANGE feature of HLS (version 4 and up) |
|      fileLength      |   false   |                0 *false*                 | When using `useByteRange=1`, this parameter needs to be set too. This will be the size of file before chunking it to another file, this replace the `chunkLength` in case of EXT-X-BYTERANGE, since `chunkLength` will be the byte range chunk |
|    useSystemTime     |   false   |                0 *false*                 | If true, uses UTC in playlist time stamp otherwise will use the local server time |
|      offsetTime      |   false   |                    0                     |                                          |
|     startOffset      |   false   |                    0                     | A parameter valid only for HLS v.6 onwards. This will indicate the start offset time (in seconds) for the playback of the playlist |

An example of the createHLSStream interface is:

``` 
createHLSStream localstreamnames=hlstest bandwidths=128 targetfolder=/MyWebRoot/ groupname=hls playlisttype=rolling playlistLength=10 chunkLength=5
```



The corresponding link to use on an iOS device to pull thisstream would then be:

`http://My_IP_or_Domain/hls/playlist.m3u8` 

In other words: `http://my_web_server/HLS_group_name/playlist_file_name`

------

**Example:**

**API Call:**

``` 
createHLSStream localstreamnames=testpullStream bandwidths=128 targetfolder=../evo-webroot groupname=hls playlisttype=rolling
```

**JSON Response:**

``` 
{
"data":{
    "AESKeyCount":5,
    "audioOnly":false,
    "bandwidths":[128],
    "chunkBaseName":"segment",
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "cleanupOnClose":false,
    "configIds":[7],
    "createMasterPlaylist":true,
    "drmType":"none",
    "fileLength":0,
    "groupName":"hls",
    "hlsResume":false,
    "hlsVersion":3,
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "maxChunkLength":0,
    "offsetTime":0,
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistName":"playlist.m3u8",
    "playlistType":"rolling",
    "staleRetentionCount":10,
    "startOffset":0,
    "targetFolder":"..\/evo-webroot",
    "useByteRange":false,
    "useSystemTime":false
},
"description":"HLS stream created",
"status":"SUCCESS"
}
```

------

The JSON response for pullStream contains the following details:

- data – The data to parse
  - AESKeyCount - the number of keys that will be automatically generated and rotated over while encrypting this HLS stream
  - audioOnly - If true, the EMS will only stream audio
  - bandwidths – An array of integersspecifying the bandwidths used for streaming
  - chunkBaseName– The base name or prefix used for naming the output HLS chunks
  - chunkLength – The length (in seconds)of each playlist element (.ts files)
  - chunkOnIdr – If true, chunking was made on IDR boundary
  - cleanupDestination – If true, HLS files at the target folder were deleted before HLS creation began
  - cleanupOnClose - If true, corresponding hls files to a stream will be deleted if the stream is disconnected
  - configIDs – The configuration IDs for this command
  - createMasterPlaylist–If true, a master playlist is created
  - drmType - The type of DRM encryption used
  - fileLength - The size of file before chunking it to another file, this replace the `chunkLength` in case of EXT-X-BYTERANGE
  - groupName –  The name of the target folder where HLS fileswill be created
  - hlsResume – If true, will resume in appendingsegments to previously created child playlist even in cases of EMS shutdown or cut off stream source
  - hlsVersion – The configured HLS version
  - keepAlive–  If true, the stream will attempt to reconnect if the connection is severed
  - localStreamNames– An array of local names for the streams
  - maxChunkLength - The maximum length the EMS willallow any single chunk to be
  - offsetTime - 
  - overwriteDestination –  If true, forced overwrite was enabled during HLS creation
  - playlistLength – The number of elements in the playlist. Useful only for rolling playlistType
  - playlistName– The file name of the playlist (*.m3u8)
  - playlistType – Either appending or rolling
  - staleRetentionCount – The number of old files kept besides the ones listed in the current version of the playlist. Only applicable for rolling playlists
  - startOffset - Indicate the start offset time (in seconds) for the playback of the playlist
  - targetFolder–The folder where all the .ts /.m3u8 files are stored
  - useByteRange - Enables the use the EXT-X-BYTERANGE feature of HLS (version 4 and up)
  - useSystemTime - Determine what time stamp is used in playlist


- description– Describes the result of parsing/executing the command


- status– `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not

------
