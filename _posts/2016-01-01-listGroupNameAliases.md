---
layout: post
title: listGroupNameAliases
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: list_group_name_aliases
---

This command returns a complete list of group name aliases.

The function has no parameters.

------

**Example:**

**API Call:**

``` 
listGroupAliases
```

**JSON Response:**

``` 
{
"data":[
    {
    "aliasName":"TestGroupAlias",
    "groupName":"MyGroup"
}
],
"description":"Currently available group name aliases",
"status":"SUCCESS"
}
```

------

The JSON response contains the following details:

- data– Provides the following information for each group name alias
  - aliasName – The alias alternative to the groupname
  - groupName – The original group name
- description– Describes the result of parsing/executing the command


- status– `SUCCESS` if the command was parsed and executed successfully, `FAIL` if not
