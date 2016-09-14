# Codestyle

- early returns over continue
- early returns instead of else
- static values via object or array and key instead of conditions where possible
- opening and closing brackets are mandatory
- refer to www.codacy.com and www.codeclimate.com as well

# Commits

- take your existing branch or open a new one
- commit with "Fixes #[ticket]" so the commits are automatically listed in the ticket
- test the changes yourself and fix any bugs you might encounter in your branch
- check your branch with www.codacy.com and/or www.codeclimate.com if it introduces more issues than it solves
- create a pull-request and let someone have a look
- Valid comments to allow a commit are :shipit:, :+1:, LGTM, Approved, Looks Good To Me and need to be positioned first to be recognised
- when accepting the pull-request all related tickets are closed

# Testing

The test version of a branch is avabile at https::/dotd.idrinth.de/static/userscript/[branch] and is uncached.
Pushes to your branch are usually deployed to it automatically within secoNds.

# Server-Side changes

Serverside code is not publicly accessible, so changes can only be implemented by  Idrinth. Please label your tickets accordingly, so they are easy to find.

# Server-Side replacements

*  ###VERSION### will be replaced with the current version, for example 1.11.9
* ###PATH### will be replaced with the path to the resource folder of the respective branch
* ###RELOAD-VERSION### will be replaced with either the version or if set the branch's name