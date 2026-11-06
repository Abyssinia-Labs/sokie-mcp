# Sokie's own MCP server

Sokie's server, running on Sokie: manage your Sokie servers from an agent, with your own API key.

## What it does

Ask your agent what's live on a server, why its calls fail, or how many calls your workspace has made this month. Have it redeploy, roll back to an earlier deploy, or rewrite a tool's description. It can also list a server's tools, skills and deploys, the names of its secrets, and your workspace's audit trail.

It acts with your own Sokie API key. It reaches only the servers that key can, and does only what the key allows.

## Add it

- **Claude** (claude.ai and the Claude apps): open [Sokie in Claude's directory](https://claude.ai/directory/sokie) and choose **Connect**.
- **Any other client**: add `https://mcp.sokie.sh/mcp` as a custom connector. In Claude Code, run `claude mcp add --transport http sokie https://mcp.sokie.sh/mcp`, then `/mcp` to connect.

The first time you connect, a Sokie page asks for a Sokie API key. Paste it, then choose what your agent may do: everything your key allows, or **Read only**. On Read only, your agent doesn't see the tools that change things.

## Which key to make

Make the key at [sokie.sh](https://sokie.sh), in **Settings › API keys**. Start from **Agent**: it can read everything and change tool descriptions. To let your agent redeploy and restore as well, set **Deploys** to **Read and write**.

A key works in one workspace, so a connection reaches one workspace. If the key is missing a permission, the call stops and says which one. To cut an agent off, revoke its key.

[API keys](https://sokie.sh/docs/api-keys) says what each permission allows. [Manage Sokie from your agent](https://sokie.sh/docs/manage-from-your-agent) has the whole setup.

## Calls that ask first

Reading runs straight away. Redeploying, restoring and changing a tool's description ask you first. Your agent puts the question to you, or gives you a link to answer it. Once you say yes, it makes the same call again. A call waits 10 minutes for your answer.

On a server linked to a repository, changing a description opens a pull request, and production changes when it merges. On a server with no repository, it goes live as soon as you allow it.

## What it can't do

Deploying new source, setting a secret and deleting a server are done with the `sokie` CLI or in the app. So are billing, members and API keys.

## Working on it

It wraps Sokie's HTTP API, whose document is `openapi.json`. The repository is linked through the Sokie App, so a merge to `main` deploys it and a pull request gets a preview.

- `sokie.json`: the server's settings, including how each person's key reaches the API.
- `tools/`: one file per operation, with its description and risk.
- `tests/`: cases that run on previews and on `sokie dev`.
- `resources/`: the guide agents read.

Put your own API key in `.sokie/dev.env` as `SOKIE_CALLER_KEY` (git ignores it), then run `sokie dev`, and `sokie test` to run the cases.

When the API changes, save its document from `https://api.sokie.cloud/v1/openapi.json` over `openapi.json`. `sokie check` then says which operations have no tool yet.
