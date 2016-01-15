---
layout: post
title: launchProcess
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: launch_process
---

Allows the user to launch an external process on the local machine. This can be used to do transcoding when paired with applications such as LibAVConv and FFMPEG. This function has the following parameters:

|     **Parameter Name**     | **Mandatory** |  **Default Value**   | **Description**                          |
| :------------------------: | :-----------: | :------------------: | ---------------------------------------- |
|       fullBinaryPath       |     true      |        *null*        | The path to the executable               |
|         keepAlive          |     false     |       *1 true*       | If the process dies for any reason, the EMS will restart the external application when keepAlive is 1 |
|         arguments          |     false     | *zero-length string* | Complete list of arguments that need to be passed to the process, delimited by ESCAPED SPACES (“\\ “) |
|         groupName          |               |                      |                                          |
| $&lt;ENV&gt;=&lt;VALUE&gt; |     false     | *zero-length string* | Any number of environment variables that need to be set just before launching the process |

An example of the launchProcess command is:

``` 
launchProcess fullBinaryPath=/home/ems/ffmpeg_preset.sh arguments=10fps\ Stream1\ Stream1_10fps keepAlive=1 $SAMPLE_E_VAR=MyVal
```

This sample command launches a script, named ffmpeg\_prest.sh, which presumably contains a shell-script that will run FFMPEG with a specific set of parameters.

The arguments field passes the three values (“10fps”, “Stream1”, “Stream1\_10fps”) to the ffmpeg\_preset.sh script. In this example, these parameters might tell this hypothetical script to transcode Stream1 to be only 10 frames-per-second, and then name the resultant stream “Stream1\_10fps”.

The final parameter is an example for setting an environment variable (SAMPLE\_E\_VAR set to MyVal) on the command line prior to script/binary execution.

------

**Example:**

**API Call:**

``` 
API	launchProcess fullBinaryPath=/home/ems/ffmpeg_preset.sh arguments=10fps\ Stream1\ Stream1_10fps keepAlive=1 $SAMPLE_E_VAR=MyVal
```

**JSON Response:**

``` 
{
   "data":{
      "arguments":"",
      "configId":1,
      "fullBinaryPath":"d:\\run.bat",
      "groupName":"process_group_UHBqMT6C",
      "keepAlive":true,
      "operationType":6
   },
   "description":"Process enqueued for start",
   "status":"SUCCESS"
}
```

The JSON response contains the following details:

- data – The data to parse
  - arguments – Complete list of arguments that need to be passed to the process
  - configID – The configuration ID for this command
  - fullBinaryPath – Full path to the binary that needs to be launched
  - groupName - ??
  - keepAlive – If keepAlive is set to 1, the server will restart the process if it exits
  - operationType – The type of operation
  - $<ENV>=<VALUE> – Any number of environment variables that need to be set just before launching the process
- description – Describes the result of parsing/executing the command


- status – `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
