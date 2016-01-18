---
layout: post
title: Accessing the Runtime API
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: accessing_runtime_api
---

## ASCII

The ASCII interface is often the first interface used by users. It can be accessed easily through the telnet application (available on all operating systems) or through common scripting languages.

To access the API via the telnet interface, a telnet application will need to be launched on the same computer that the EMS is running on. The command to open telnet from a command prompt should look something like the following:

``` 
telnet localhost 1112
```

**Note:**

Telnet may need to be enabled using Windows® operating systems. To do this, go to the *Control Panel -> Programs -> Turn Windows Features on and off*. Turn the Telnet Client program on.

![](./media/image1.jpg)



Please also note that on Windows®, the default telnet behavior will need to be changed. The local echo and new line mode should be set for proper behavior. Once telnet is launched, exit the telnet session by typing “**ctrl+\]**”. Then enter the following commands:

``` 
set localecho
set crlf
```

To return to the Windows® telnet session, press **Enter**/**Return** key.

Once the telnet session is established, type out the desired commands which will be immediately executed on the server after the Enter/Return key is pressed.

An example of a command request and response from a telnet session would be the following:

**Request:** `version`

**Response:**

``` 
☺«{"data":{"banner":"EvoStream Media Server (www.evostream.com) version 1.7.0. build 4153 with hash: c50ee04ec98886ed1f54d599355e04346bf50df0 on branch: develop - PacMan|m|-(built on 2015-11-03T01:50:37.000)","branchName":"develop","buildDate":1446515437,"buildNumber":"4153","codeName":"PacMan|m|","hash":"c50ee04ec98886ed1f54d599355e04346bf50df0","releaseNumber":"1.7.0."},"description":"Version","status":"SUCCESS"}
```

- **JSON**

When using the regular ASCII interface, it may be necessary to use a JSON interpreter so that responses can be more human-readable. JSON parsers are available online.

------

## ASCII CLI

This is the user friendly version of the ASCII telnet interface. It offers a readable response without having to parse the JSON results. To access this interface from the command prompt, execute the following:

However, since the objective of this interface is simplicity, there are some parameters that are not included on the display. Thus, for advanced usages and/or configurations, it is better to use the regular ASCII telnet interface.

An example of a command request and response from an ASCLII CLI telnet session would be the following:

**Request:** `version`

**Response:**

``` 
Command entered successfully!
Version

  banner: EvoStream Media Server (www.evostream.com) version 1.7.0. build 4153 with hash: 4ab5d9145ae3b4b3dfeb3af5ce6890f015824974 on branch: develop - PacMan|m| - (built on 2015-11-06T08:24:32.000)
  buildDate: 2015-11-03T01:50:37.000
  buildNumber: 4153
  codeName: PacMan|m|
  releaseNumber: 1.7.0.
```

------

## HTTP

To access the API via the HTTP interface, simply make an HTTP request on the server using any browser with the command to be executed. By default, the port used for these HTTP requests is **7777**. The HTTP interface port can be changed in the main configuration file used by the EMS (config.lua).

A general http format request would be the following:

``` 
http://[EMS IP]:7777/[API]
```

An example of a command request and response from an HTTP session would be the following:

``` 
http://IP:7777/[API]?params=([base64 encoded parameters])
```



**Request:** `http://localhost:7777/version`

**Response:**

``` 
{"data":{"banner":"EvoStream Media Server (www.evostream.com) version 1.7.0. build 4153 with hash: 4ab5d9145ae3b4b3dfeb3af5ce6890f015824974 on branch: develop - PacMan|m| - (built on 2015-11-06T08:24:32.000)","branchName":"develop","buildDate":"2015-11-06T08:24:32.000","buildNumber":"4176","codeName":"PacMan|m|","hash":"4ab5d9145ae3b4b3dfeb3af5ce6890f015824974","releaseNumber":"1.7.0."},"description":"Version","status":"SUCCESS"}
```



All of the API functions are available via HTTP, but the request must be formatted slightly different if parameters are included. To make an API call over HTTP, the parameters to be used should be in base64 format.

Sampling a `pullstream` command:

1. Type in the parameters first:
   
   ``` 
   (firstParam=XXX secondParam=YYY…)
   
   (uri=rtsp://localhost:5544/vod/mp4.bunny.mp4 localStreamName=bunny)
   ```
   
2. Convert the parameters using a base64 encoder:

**Converted parameter:** 

``` 
dXJpPXJ0c3A6Ly9sb2NhbGhvc3Q6NTU0NC92b2QvbXA0LmJ1bm55Lm1wNCBsb2NhbHN0cmVhbW5hbWU9YnVubnkp
```

**The corresponding request in HTTP format would be:**

``` 
http://localhost:7777/pullstream?params= dXJpPXJ0c3A6Ly9sb2NhbGhvc3Q6NTU0NC92b2QvbXA0LmJ1bm55Lm1wNCBsb2NhbHN0cmVhbW5hbWU9YnVubnkpxxxxxxxxxx 
```



- **Base64**

A group of similar binary-to-text encoding schemes that represent binary data in an ASCII string format by translating it into a radix-64 representation. There are available base64 encoders online to get the encoded result.

- **PHP and JavaScript**

PHP and JavaScript functions are also provided. These functions simply wrap the HTTP interface calls and can be found in the EMS Web UI directory.

- **Securing the API**

By default, the ASCII API is protected and access from any outside computer is prohibited. This can of course be modified within the config.lua file, but keeping this restriction is recommended for maintaining server security.

The HTTP based API is also restricted by default to only local access. However, unlike the ASCII API interface, there are often good reasons to expose the HTTP API. To secure the HTTP based API in this case, you will enable Proxy Authentication on the EWS (details found in the EWS section of this doc). This will enforce that a valid username and password be provided for each and every API call made, ensuring on authorized access to the EMS API.
