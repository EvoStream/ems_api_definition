---
layout: post
title: Adaptive Streaming / File-based Streaming Events
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: adaptive_streaming
---

## hlsChunkCreated, hdsChunkCreated, mssChunkCreated, dashChunkCreated

Event triggered when an HLS/HDS/MSS/DASH chunk file was opened on disk.

**file** – Name of the HLS/HDS/MSS/DASH chunk file that was opened.



Example for HLS: 

`/evo-webroot/hls/stream1/segment_1362025844863_1362025844863\_14.ts`

Example for HDS: 

`/evo-webroot/hds/stream1/f4vSeg1-Frag1`

Example for MSS: 

`/evo-webroot/mss/stream1/video/524288/1413797685000.m4s`

Example for DASH: 

`/evo-webroot/dash/stream1/video/229376/1416464032000.fmp4`

------

## hlsChunkClosed, hdsChunkClosed, mssChunkClosed, dashChunkClosed

Event triggered when an HLS/HDS/MSS/DASH chunk file was closed on disk.

**file** – Name of the HLS/HDS/MSS/DASH chunk file that was closed.



Example for HLS: 

`/evo-webroot/hls/stream1/segment_1362025844863_1362025844863_14.ts`

Example for HDS: 

`/evo-webroot/hds/stream1/f4vSeg1-Frag1`

Example for MSS: 

`/evo-webroot/mss/stream1/video/524288/1413797685000.m4s`

Example for DASH: 

`/evo-webroot/dash/stream1/video/229376/1416464032000.fmp4`

------

## hlsChunkError, hdsChunkError, mssChunkError, dashChunkError

Event triggered when an error occurs while writing an HLS/HDS/MSS/DASH chunk file.

**error** – Description of the error encountered.



Example for HLS: 

``` 
Could not write video sample to /evo-webroot/hls/stream1/
segment_1362025844863_1362025844863_14.ts
```

------

## hlsChildPlaylistUpdated, hdsChildPlaylistUpdated

Event triggered when an HLS or HDS stream specific playlist file was modified

**file** – Name of the HLS or HDS playlist that was updated



Example for HLS: 

`/evo-webroot/hls/stream1/playlist.m3u8`

Example for HDS: 

`/evo-webroot/hds/stream1/stream1.f4m`

------

## hlsMasterPlaylistUpdated, hdsMasterPlaylistUpdated

Event triggered when an HLS or HDS group playlist file was modified

**file** – Name of the HLS or HDS playlist that was updated



Example for HLS: 

`/evo-webroot/hls/playlist.m3u8`

Example for HDS: 

`/evo-webroot/hds/stream1.f4m`

------

## mssPlaylistUpdated, dashPlaylistUpdated

Event triggered when an MSS/DASH stream specific playlist file was modified

**file** – Name of the MSS/DASH manifest that was updated



Example for MSS: 

`/evo-webroot/mss/stream1/manifest.f4m`

Example for DASH: 

`/evo-webroot/dash/stream1/manifest.mpd`

------

## recordChunkCreated, recordChunkClosed, recordChunkError

Event triggered when a new record fragment has been opened, completed and ready on disk, or failed due to a write error

**file** – Name of the record fragment that was opened, closed, or had a write error



Example for MP4 record: 

`/media/record/stream1_part0008.mp4`
