---
title: Developer Information
layout: default
---
## Communication

We got Slack available for questions and small talk, feel free to mail webmaster AT idrinth DOT de for an invitation.

## Codestyle

- early returns over continue
- early returns instead of else
- static values via object or array and key instead of conditions where possible
- using [prettier](https://github.com/prettier/prettier) via [automatic formatting](https://github.com/Idrinth/automatic-formatting/), following it's style is appreciated

## Commits

- Take your existing branch or open a new one
- Commit with "Fixes #[ticket]" so the commits are automatically listed in the ticket
- Test the changes yourself and fix any bugs you might encounter in your branch
- Check your branch with www.codacy.com and/or www.codeclimate.com if it introduces more issues than it solves
- Create a pull-request and let someone have a look - automatic formatting might happen now if you didn't follow the codestyle
- Valid comments to allow a commit are ":shipit:", ":+1:", "LGTM", "Approved", "Looks Good To Me". They need to be positioned first to be recognised
- When accepting the pull-request all related tickets are closed

## Testing

The test version of a branch is available at https::/dotd.idrinth.de/static/userscript/[branch] and is uncached.
Pushes to your branch are usually deployed to it automatically within seconds.

## Server-Side changes

Serverside code is not publicly accessible, so changes can only be implemented by Idrinth. Please label your tickets accordingly, so they are easy to find.

## Server-Side replacements

* ###VERSION### will be replaced with the current version, for example 1.11.9
* ###PATH### will be replaced with the path to the resource folder of the respective branch
* ###RELOAD-VERSION### will be replaced with either the version or if set the branch's name
* ###LANG### will be replaces with the contents of languages/en.json
