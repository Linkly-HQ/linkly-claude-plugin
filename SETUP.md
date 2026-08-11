# Linkly plugin setup

There is almost nothing to set up — the plugin bundles the hosted Linkly MCP
connector (`https://mcp.linklyhq.com`), which authenticates with OAuth.

1. You need a Linkly account: https://linklyhq.com (the free tier works).
2. The first time Claude calls a Linkly tool, you'll be prompted to sign in
   with Linkly and authorize a workspace. Complete that in the browser.
3. That's it. No API keys, no environment variables.

The connector operates only within the workspace you authorize. To switch
workspaces, disconnect and reconnect the Linkly server and pick a different
workspace at the authorization step.

Docs: https://linklyhq.com/support/mcp-server · Support: support@linklyhq.com
