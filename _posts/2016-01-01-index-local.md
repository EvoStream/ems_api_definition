---
layout: post
title:  "EMS API Definition (Local Test Only)"
date:   2016-01-01 00:01:00 +0000
categories: jekyll update
permalink: table_of_contents_local
---

1. Document Definitions
2. Overview
3. Run-Time API
   1. Accessing the Runtime API
      - ASCII
      - HTTP
      - PHP and JavaScript
      - JSON
   2. Configuring and Receiving Event Notifications
      - Sinks
   3. User Defined Variables
   4. Streams vs Stream Configs and API Command Return Values
      - Stream Configs
      - Streams
4. EvoStream Media Server API
   1. Streams
      - [pullStream](/pull_stream)
      - [pushStream](/push_stream)
      - [createHLSStream](/create_hls_stream)
      - [createHDSStream](/create_hds_stream)
      - [createMSSStream](/create_mss_stream)
      - [createDASHStream](/create_dash_stream)
      - [record](/record)
      - [transcode](/transcode)
   2. Aliasing
      - [listStreamsIds](/list_streams_ids)
      - [getStreamInfo](/get_stream_info)
      - [listStreams](/list_streams)
      - [getStreamsCount](/get_streams_count)
      - [shutdownStream](/shutdown_stream)
      - [listConfig](/list_config)
      - [removeConfig](/remove_config)
      - [getConfigInfo](/get_config_info)
      - [addStreamAlias](/add_stream_alias)
      - [listStreamAliases](/list_stream_aliases)
      - [removeStreamAlias](/remove_stream_alias)
      - [flushStreamAliases](/flush_stream_aliases)
      - [addGroupNameAlias](/add_group_name_alias)
      - [flushGroupNameAliases](/flush_group_name_aliases)
      - [getGroupNameByAlias](/get_group_name_by_alias)
      - [listGroupNameAliases](/list_group_name_aliases)
      - [removeGroupNameAliases](/remove_group_name_aliases)
      - [listHttpStreamingSessions](/list_http_streaming_sessions)
      - [createIngestPoint](/create_ingest_point)
      - [removeIngestPoint](/remove_ingest_point)
      - [listIngestPoints](/list_ingest_points)
      - [startWebRTC](/start_web_rtc)
      - [stopWebRTC](/stop_web_rtc)
   3. Utility and Feature API Functions
      - [launchProcess](/launch_process)
      - [setTimer](/set_timer)
      - [listTimers](/list_timers)
      - [removeTimer](/remove_timer)
      - [generateLazyPullFile](/generate_lazy_pull_file)
      - [generateServerPlaylist](/generate_server_playlist)
      - [insertPlaylistItem](/insert_playlist_item)
      - [uploadMedia](/upload_media)
      - [getMetadata](/get_metadata)
      - [pushMetadata](/push_metadata)
      - [shutdownMetadata](/shutdown_metadata)
      - [listStorage](/list_storage)
      - addStorage
      - [removeStorage](/remove_storage)
      - [setAuthentication](/set_authentication)
      - [setLogLevel](/set_log_level)
      - [version](/version)
      - [quit](/quit)
      - [help](/help)
      - [shutdownServer](/shutdown_server)
   4. Connections
      - [listConnectionsIds](/list_connections_ids)
      - [getConnectionInfo](/get_connection_info)
      - [listConnections](/list_connections)
      - [clientsConnected](/clients_connected)
      - [httpClientsConnected](/http_clients_connected)
      - [getExtendedConnectionCounters](/get_extended_connection_counters)
      - [resetMaxFdCounters](/reset_max_fd_counters)
      - [resetTotalFdCounters](/reset_total_fd_counters)
      - [getConnectionsCount](/get_connections_count)
      - [getConnectionsCountLimit](/get_connections_count_limit)
      - [setConnectionsCountLimit](/set_connections_count_limit)
      - [getBandwidth](/get_bandwidth)
      - setBandwidthLimit
   5. Services
      - listServices
      - createService
      - enableService
      - shutdownService
5. EMS Event Notification System
   1. Stream Event Definitions
      - inStreamCreated, outStreamCreated, streamCreated
      - inStreamClosed, outStreamClosed, streamClosed
      - inStreamCodecsUpdated, outStreamCodecsUpdated, streamCodecsUpdated
      - audioFeedStopped
      - videoFeedStopped
   2. Adaptive Streaming/File-based Streaming Events
      - hlsChunkCreated, hdsChunkCreated, mssChunkCreated, dashChunkCreated
      - hlsChunkClosed, hdsChunkClosed, mssChunkClosed, dashChunkClosed
      - hlsChunkError, hdsChunkError, mssChunkError, dashChunkError
      - hlsChildPlaylistUpdated, hdsChildPlaylistUpdated
      - hlsMasterPlaylistUpdated, hdsMasterPlaylistUpdated
      - mssPlaylistUpdated, dashPlaylistUpdated
   3. Web Server Events
      - streamingSessionStarted
      - streamingSessionEnded
      - fileDownloaded
   4. API Based Events
      - cliRequest
      - cliResponse
      - processStarted, processStopped
      - timerCreated
      - timerTriggered
      - timerClosed
   5. Connection Based Events
      - protocolRegisteredToApp
      - protocolUnregisteredFromApp
      - carrierCreated
      - carrierClosed
   6. Application Based Events
      - applicationStart, applicationStop
      - serverStarted
      - serverStopped
   7. Web Server Events
      - streamingSessionStarted
      - streamingSessionEnded
      - fileDownloaded
   6. Event Table of Protocol Types
