# Sokie's own MCP server

Sokie's server, running on Sokie: manage your Sokie servers from an agent, signed in as you.

## What it does

Ask your agent what's live on a server, why its calls fail, or how many calls your workspace has made this month. Have it redeploy, roll back to an earlier deploy, or rewrite a tool's description. It can also list a server's tools, skills and deploys, the names of its secrets, and your workspace's audit trail.

It acts as you, in the workspace you choose when it connects, and never does more than you can.

## Add it

- **Claude** (claude.ai and the Claude apps): open [Sokie in Claude's directory](https://claude.ai/directory/sokie) and choose **Connect**.
- **Any other client**: add `https://mcp.sokie.sh/mcp` as a custom connector. In Claude Code, run `claude mcp add --transport http sokie https://mcp.sokie.sh/mcp`, then `/mcp` to connect.

The first time you connect, a Sokie page opens. Sign in if you aren't already (someone new signs up there), choose the workspace, and choose what your agent may do: **Everything you can, asking before it changes anything**, or **Read only**. Then **Allow**, and confirm it's you with your passkey if Sokie asks. On Read only, your agent doesn't see the tools that change things.

A connection reaches one workspace. To work in another, connect again and choose it. If a call needs something your role in the workspace can't do, it stops and says so.

## Stop an agent

**Your agent** in the Sokie sidebar lists the agents you connected for that workspace. Hold any of them to reading, or disconnect it, and your other agents carry on. Either takes effect from its next call.

If you connected with an API key before, that agent keeps working until the key stops; it then asks you to connect again, and signs in this way.

[Manage Sokie from your agent](https://sokie.sh/docs/manage-from-your-agent) has the whole setup.

## Calls that ask first

Reading runs straight away. Redeploying, restoring and changing a tool's description ask you first. Your agent puts the question to you, or gives you a link to answer it. Once you say yes, it makes the same call again. A call waits 10 minutes for your answer.

On a server linked to a repository, changing a description opens a pull request, and production changes when it merges. On a server with no repository, it goes live as soon as you allow it.

## What it can't do

Deploying new source, setting a secret and deleting a server are done with the `sokie` CLI or in the app. So are billing, members and API keys.

## Working on it

It wraps Sokie's HTTP API, whose document is `openapi.json`. The repository is linked through the Sokie App, so a merge to `main` deploys it and a pull request gets a preview.

- `sokie.json`: the server's settings, including how each person's credential reaches the API.
- `tools/`: one file per operation, with its description and risk.
- `tests/`: cases that run on previews and on `sokie dev`.
- `resources/`: the guide agents read.

Put your own API key in `.sokie/dev.env` as `SOKIE_CALLER_KEY` (git ignores it), then run `sokie dev`, and `sokie test` to run the cases.

When the API changes, save its document from `https://api.sokie.cloud/v1/openapi.json` over `openapi.json`. `sokie check` then says which operations have no tool yet.
