For the following api-calls assume lower case and spaces replaced by hyphens. Urls are therefore build starting with /[server] and adding in the headers related to the task, for example /kongregate/chat-service/update/ .

# Chat Service

This group of services handles everything chat related. These do return error-object with the keys success, message and possibly login.

Success will be false in case of errors and if it is an error that will likely e solved by logging in again, login will be set to true.

## Accounts

## Create

## Join

## Login

## MyChats

## Rank

## Register

## Update

# Raid Service

provides raids to join

# I am alive

a single call for tracking purposes - see if there's anyone using the script

# Tiers Service

Provides all raid's tier data in a json object of raid-objects. This is a GET request, that does not take any additional parameters.

The key for those objects is the lower case name combines with the lower case short name if they differ sufficiently.
Jormungan has the key "jormungan the sea-storm", while "Badland Ambusher (Badlands)" is providing both version since they differ.
On the upper level each objects provides the following fields:

- name : string : the actual long name of the raid
- url : string : the image's name
- n : int[] : Array of damage tiers for normal difficulty
- h : int[] : Array of damage tiers for harddifficulty
- l : int[] : Array of damage tiers for legendary difficulty
- nn : int[] : Array of damage tiers for nightmare difficulty
- epics : int{} : an object mirroring the tier structure with the amount of epics instead of required damage
- os : int{} : optimal share values for each difficulty
- fs : int{} : fair share for each difficulty
- ap : int : the ap-value

## Example:

This is a shortened example for Jormungan. Other raid-bosses follow the same structure.

`{"jormungan the sea-storm":{"name":"Jormungan the Sea-Storm","url":"jormungan-294","n":[200000000,100000000000],"os":{"n":3000000000,"h":3000000000,"l":3000000000,"nm":3000000000},"fs":{"n":937500000,"h":1875000000,"l":2812500000,"nm":3750000000},"epics":{"n":["0","400"],"h":["0","400"],"l":["0","400"],"nm":["0","400"]},"h":[200000000,100000000000],"l":[200000000,100000000000],"nm":[200000000,100000000000],"ap":1875000000}}`

# Users Service

provides access to register platform names and request known ones.

## Add

A get-request to add a username, that is appended as the next "folder" in this request. Does not return anything.

## Get

A get-request, that returns a list of users grouped by their kong-names. This is meant to be called multiple types to update the content on the client's side.

A single user's data is grouped by his lower-case kongregate username and then in turn has a supobject for each server that he is on. These objects provide the following keys:

- guildId : int : the id ugup gave the guid
- id : int : the id of the user, needed to link to the profile for example
- level : int : the last known level
- updated : string : and sql-style timestamp of the last sucessful update
- class : int : the class-id of the user
- name : string : the ingame name of the user
- 7day: int : levels gained during the last 7 days
- 30day: int : levels gained during the last 30 days

### Example

`{"bjalpha":{"kongregate":{"guildId":"645","id":"27341","level":"2658","updated":"2016-07-24 16:07:01","class":"12","name":"Idrinth","7day":"31","30day":"344"},"world":{"guildId":"0","id":"39135125","level":"7","updated":"2016-07-25 07:52:01","class":"3","name":"i","7day":"0","30day":"0"}}}` 

# War Service

access to war raids and war statistics