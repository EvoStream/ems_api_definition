---
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: removeGroupNameAliases
---

# removeGroupNameAliases

This command returns a complete list of group name aliases.

This function has the following parameters:

| Parameter Name | **Mandatory** | **Default Value** | **Description**                          |
| :------------: | :-----------: | :---------------: | ---------------------------------------- |
|   aliasName    |     true      |      *null*       | The alias alternative to be removed from the group name |

An example of the removeGroupNameAlias interface is:

``` 
removeGroupNameAlias aliasName=myalias
```

This removes the alias name “myalias”.

------

**Example:**

**API Call:**

``` 
removeGroupNameAlias aliasName=TestGroupAlias
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
"description":"Group Alias removed",
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
