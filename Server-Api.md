For the following api-calls assume lower case and spaces replaced by hyphens. Urls are therefore build starting with /[server] and adding in the headers related to the task, for example /kongregate/chat-service/update/ .

# Chat Service

This group of services handles everything chat related. These do return error-object with the keys success, message and possibly login.

Success will be false in case of errors and if it is an error that will likely be solved by logging in again, login will be set to true.

## Accounts

Get all required information about logged-in users, including yourself. This takes no additional payload of any kind.

The members object contains the rank of each user, organised by chat and then user, while the users object contains a list of active platforms and the user's name.

### Example

Chat 17 with user 1:

`{"self":1,"members":{17:{1:Owner}},"users":{1:{name:"Idrinth",platforms:{"k":true,"f":false,"a":false,"n":true}}}`

### Other Responses

`{"success":false,"message":"please login again","login":true}`

## Create

Creates a new chat with a random password and sets the creating user as chat-owner.

### Example

`Idrinth-Addition: my chat 9000`

### Responses

`{"success":false,"message":"please login again"}`

`{"success":false,"message":"the message didn't use an allowed format"`

`{"success":true,"data":{name:"name",access:"Owner",pass:"pass"}`

## Delete

Takes the chat-id as the next path-part and deletes a chat if you are an Owner.

### Responses

`{"success":false,"message":"please login again","login":true}`

`{"success":false,"message":"the request didn't use an allowed format"}`

`{"success":false,"message":"you lack the right to delete this chat."}`

`{"success":true}`

## Join

Sends chatjoin-data via the header Idrinth-addition and gets the necessary data back to build the chat-gui if sucessfull.

### Example

`Idrinth-Addition: {"id":"22","pass":"halloWelt"}`

### Responses

`{"success":false,"message":"please login again","login":true}`

`{"success":false,"message":"the message didn't use an allowed format."}`

`{"success":false,"message":"You need to supply an ID and a password"}`

`{"success":false,"message":"You are banned from this chat"}`

`{"success":true,"data":{"id":22,"name":"halloWelt","pass":"halloWelt"}}`

`{"success":false,"message":"Password and ID do not match"}`

## Login

A query containing a username and password in the Idrinth-Addition-header.

### Example

`Idrinth-Addition: {"user":"Tester","pass":"Password"}`

### Responses

`{"success":false,"message":"data not provided, either username or password is empty"}`

`{"success":false,"message":"User unknown, do you want to register?","allow-reg":true}`

`{"success":false,"message":"Combination of username and password unknown."}`

`{"success":true,"data":MyChats()}`

## My chats

Returns a list of all allowed chats with their names and passwords.

### Example

`{"1":{"access":"User","pass":"Hallo","name":"World"}}`

## Rank

Changes the rank of a specific user in a specific chat. Chat and user to be changed need to be submitted as a json encoded value of the header Idrinth-Addition.

Possible ranks are:
- Banned
- Leave
- User
- Mod
- Owner

### Example:

`Idrinth-Addition: {"user":1,chat:"1","access":""}`

### Responses

`{"success":false,"message":"please login again","login":true}`

`{"success":false,"message":"the message didn't use an allowed format"}`

`{"success":false,"message":"you can not change this user's rights in the desired way')`

`{"success":true,"message":"User's rights changed"}`

## Register

A query containing a username and password in the Idrinth-Addition-header.

### Example

`Idrinth-Addition: {"user":"Tester","pass":"Password"}`

### Responses

`{"success":true,"data":MyChats()}`

`{"success":false,"message":"You need to provide data for registering in"}`

`{"success":false,"message":"You need to provide data for registering in"}`

`{"success":false,"message":"The given login already exists, please choose another one"}`

## Update

This handles the sending of new messages as well as retrieving messages send by others. The first are send as a json object of messages per chat, while the later is handled with sending the highest known message id.

### Example

`Idrinth-Addition: {"messages":[{"chat":1,"text":"Hi, anyone around?"}],"maxId":111}`

### Responses

`{"success":false,"message":"please login again","login":true)`

`{"success":false,"message":"the message didn't use an allowed format"}`

`{"messages":{"1":{"112":{"time" => "2016-07-25 15:09:08","user":1,"text":"Hi, anyone around?"}}}}`

# Raid Service

provides raids to join

# I am alive

A single call for tracking purposes, to see if there's anyone using the script. It takes a pseudeo UUID as the next part of the path and returns nothing. UUIDs are checked to match the following regex:

`^[a-z0-9]{4}-[a-z0-9]{8}-[a-z0-9]{12}-[a-z0-9]{16}-[a-z0-9]{20}-[a-z0-9]{24}$`

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

## Init

Reduces pseudo-static data, that is not meant to be requeried. This is a list of guild names and class names.

### Example

`{"classes":{"4":"Adventurer"},"guilds":{"kongregate":{"0":"[Sytem:Guildless]"},"world":{"0":"[System Guildless""}}}`

# War Service

access to war raids and war statistics