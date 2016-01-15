---
layout: post
title: uploadMedia
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: upload_media
---

Creates an acceptor which receives an HTTP POST binary upload. The acceptor will be opened on a specified port and the uploaded media file will be written on a specified directory. The acceptor then waits for an HTTP PUT from a client with the media file as payload. The media file is then written on the specified location in the server.

This function has the following parameters:

| **Parameter Name** | **Mandatory** | **Default Value** | **Description**                          |
| :----------------: | :-----------: | :---------------: | ---------------------------------------- |
|        port        |     true      |      *null*       | The port value to bind on                |
|    targetFolder    |     true      |      *null*       | The folder where the binary upload will be serialized |

The sending client must conform to the following:

- It must send the data by way of HTTP POST
- The POST request must be in http/1.1 format
- A StreamName must be provided in the POST line. This will then be the filename of the media file (mp4) when written. (e.g., *POST /mystreamname HTTP/1.1\\r\\n*)
- Content-type must be set to *video/mp4* or *application/octet-stream*
- Content-length must be used. This function is intended for uploading VOD MP4 so the EMS will expect that the size of the file is already known

An example of the uploadMedia interface is:

``` 
uploadMedia port=3333 targetFolder=/MyMediaFolder
```

------

**Example:**

**API Call:**

``` 
shutdownstream id=55
```

**JSON Response:**

``` 
{
"data":{
    "ip":"0.0.0.0",
    "port":3333,
    "targetFolder":"..\/media"
},
"description":"Media upload acceptor configuration.",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data – The data to parse.
  - ip – The IP referring to the EMS, normally 0.0.0.0
  - port – The specified port number where the acceptor will wait for HTTP POSTs
  - targetFolder – The specified folder where the media file will be written
- description – Describes the result of parsing/executing the command
- status – `SUCCES` if the command was parsed and executed successfully, `FAIL` if not
