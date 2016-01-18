---
layout: post
title: Streams vs Stream Configs and API Command Return Values
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: streams_vs_stream_configs_and_api_command_return_values
---

Issuing commands to the EvoStream Media Server is an Asynchronous event. This means that a successfully issued command will not actually be executed immediately. It will instead be Queued for execution. While this generally transparent for the user, there is an important ramification of this reality:

> When the EMS returns SUCCESS for an issued API command, this only means that the command was successfully QUEUED. IT DOES NOT MEAN THAT THE COMMAND WAS SUCCESSFULLY EXECUTED! 

For example, a pullStream command may return SUCCESS, but the stream may not have actually been pulled!

More details on why this occurs follows.

------



## Stream Configs

When an API command is issued, it creates a Stream Config entry. Each Stream Config is a list of parameters which instructs EMS to take an action. As a result of that action, a stream may be born. At the time at which the command is executed (stream config is created), there is absolutely no guarantee that the action will indeed spawn a stream. There is a very good reason for this behavior. The action itself doesn't solely depend on EMS. In the case of `pullStream`, the success of the command greatly depends on the distant party being invoked to send the stream in question. If that distant party doesn't do that, then the stream can't be created. To summarize, stream config is only the blueprint of the future stream, nothing less, and nothing more.



Stream Configs also have a unique, monotonically increasing ID. This is completely different from the "stream id". When listConfig is used, it will output the format described in the "API Definiion.pdf". Notice the configId value for each node. The listing of the configurations also contains the current status of the stream and the previous status. Finally, removeConfig can be used to terminate a configuration and the corresponding stream (if ever spawned)

------

## Streams

Streams are the active streams currently managed by EMS. They may or may not have an associated config. That is because the stream could be pushed/pulled into/from EMS by a distant party, without any execution of a pushStream/pullStream command.

For example, an Adobe flash application does a “publish” or a “play”. However, when a stream is born due to a `pullStream`/`pushStream`/etc API command, that stream Will have an associated config. listStreams will list all streams regardless of their nature: pulled/pushed by EMS or from 3rd party apps like explained in the Adobe example above. When a stream is actively pushed/pulled by EMS, the node describing that stream will also contain a sub node with the configuration (the stream config explained above). shutdownStream, as the name implies, acts on a stream, not on a stream config. That is why you can't do a `shutdownStream` on a stream name which is not present BUT was configured. The `permanently=1` parameter is provided to save an extra call to `removeConfig` call, but, again, that is only making sense when the stream is active. The streams information returned by listStreams contains a unique id for each and every stream node. That is what we refer to as "stream id".

To summarize the above: *`streamID`* is different from `configID` because they signify two different kinds of entities.
