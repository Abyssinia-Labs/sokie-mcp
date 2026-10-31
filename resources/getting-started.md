---
uri: sokie://guides/getting-started
title: Getting started with Sokie's server
description: How to find a server, follow a deploy, and what this server can't do.
---

# Getting started

Each tool acts for the person whose API key this connection uses. A key belongs to one workspace, and can do what its scopes and servers allow. A tool answers `SCOPE_REQUIRED` when the key is missing a scope, and the answer names it.

## Find a server

Start with `listServers`. Each server has a `slug` and a `serverId`: `getServer` takes the slug, and the tools for deploys, tools, calls and secrets take the `serverId`.

## Read more than one page

Lists come a page at a time. When `isDone` is false, call the tool again with `cursor` set to `continueCursor`.

## Follow a deploy

`redeploy` and `restoreDeploy` start a deploy and return at once. Follow it with `getDeploy` until it settles. Production keeps answering until the new deploy is live.

Before restoring, call `checkRestore`: it says what the restore would do, or why it can't be done. On a server linked to a repository, a restore stops production following the default branch until someone resumes it.

## Change a tool's description

On a server linked to a repository, use `proposeToolDescription`, which opens a pull request. Production changes when it merges. On a server with no repository, use `deployToolDescription` with the server's `liveDeploymentId` as `base`. It goes live straight away.

## Calls that ask first

Redeploying, restoring and changing a description ask the person first. When a call is held, ask them to answer it, then make the same call again.

## What this server can't do

Deploying new source, setting a secret and deleting a server are done with the `sokie` CLI or in the app. So are billing, members and API keys.
