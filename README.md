# Inngest for Grok and Cursor

Build durable workflows and inspect Inngest Cloud through OAuth MCP. Includes
15 skills for writing functions and agents, debugging runs, working with events,
and using the Inngest SDK and CLI.

This is an initial package for local testing. Marketplace approval and signed-in
testing in Grok, Grok Bot, and Cursor are pending. Automatic sign-in in clients
that require OAuth dynamic client registration depends on Inngest deploying
that server support.

## Grok Build

Install the plugin from this repository:

```sh
grok plugin install inngest/inngest-grok-plugin --trust
```

`--trust` confirms you have reviewed the plugin. Without it, Grok shows the
source and stops without installing. To connect your Inngest account, open
`/mcps`, select `inngest-cloud`, and press `i` to sign in.

To validate a local checkout:

```sh
grok plugin validate .
```

## Cursor

In Cursor's Customize view, use **Import from Disk** and select a checkout of this
repository. Cursor loads the manifest, the skills, and the Inngest MCP server.
Enable the server and complete sign-in when prompted.

## Grok and Grok Bot

This repository is the package source for our partner submission. Hosted
installation depends on marketplace approval and each host's plugin support.
For direct MCP testing, add this remote server in a host that supports custom
MCP connections:

```text
https://api.inngest.com/mcp
```

## Testing

Use a test Inngest account and select its test environment during authorization.
No credentials or API keys are bundled with the plugin.

1. Confirm the host discovers the Inngest skills and `inngest-cloud` MCP server.
2. Complete OAuth and ask: "List my environments, apps, and functions."
3. Ask: "In my test environment, find recent failed runs and explain the failed steps."
4. Confirm the results match the Inngest dashboard and include the selected environment.
5. In a local code project, ask: "Show me an Inngest function with a durable step."

Event sending, function invocation, reruns, cancellation, and other changes need
an explicit request scoped to a test environment. Hosted clients cannot reach a
local Dev Server. For local development, add a separate MCP connection at
`http://127.0.0.1:8288/mcp`, using the port your server actually starts on.

## Package layout

- `plugin.json`: portable Agent Plugins manifest for skills and MCP.
- `.cursor-plugin/plugin.json`: Cursor manifest. It adds the logo, and the xAI
  marketplace reads the plugin version from it.
- `mcp.json`: portable Streamable HTTP connection.
- `.mcp.json`: equivalent HTTP connection for Grok Build.
- `skills/`: 15 Inngest skills and their reference material.
- `examples/`: TypeScript examples.

Keep these in sync when they change:

- The server URL in `mcp.json`, `.mcp.json`, and `.cursor-plugin/plugin.json`.
- The name, version, and description in `plugin.json` and
  `.cursor-plugin/plugin.json`.
- `references/expressions.md` inside `inngest-steps`, `inngest-events`, and
  `inngest-durable-functions`. Each skill carries its own copy so it stays
  self-contained.

The initial skills
and assets were copied from
[inngest-codex-plugin](https://github.com/inngest/inngest-codex-plugin/tree/c6fb94699c9ead893170cc510721fdcf3471460a/plugins/inngest)
(version 0.4.3). This package has its own release version.

- [Inngest MCP documentation](https://www.inngest.com/docs/ai-dev-tools/mcp)
- [Grok Build plugin guide](https://github.com/xai-org/grok-build/blob/main/crates/codegen/xai-grok-pager/docs/user-guide/09-plugins.md)
- [Cursor plugins](https://cursor.com/docs/plugins)
- [Support](https://www.inngest.com/discord)
- [Privacy](https://www.inngest.com/privacy)
- [Terms](https://www.inngest.com/terms)

MIT. See [LICENSE](LICENSE).
