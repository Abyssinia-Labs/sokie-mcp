# Sokie's own MCP server

Sokie's server, running on Sokie: manage your servers from an agent, with your own API key.

It wraps Sokie's HTTP API, whose document is `openapi.json`. The repository is linked through the Sokie App, so a merge to `main` deploys it and a pull request gets a preview.

- `sokie.json`: the server's settings, including how each person's key reaches the API.
- `tools/`: one file per operation, with its description and risk.
- `tests/`: cases that run on previews and on `sokie dev`.
- `resources/`: the guide agents read.

## Working on it

Put your own API key in `.sokie/dev.env` as `SOKIE_CALLER_KEY` (git ignores it), then run `sokie dev`, and `sokie test` to run the cases.

When the API changes, `sokie source pull` brings in its document and shows what changed.
