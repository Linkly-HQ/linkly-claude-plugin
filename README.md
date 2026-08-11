# Linkly plugin for Claude

Official [Linkly](https://linklyhq.com) plugin for Claude Code and Cowork.
Create branded short links, track click analytics, and keep the links in
your documents healthy — without leaving Claude.

The plugin bundles:

- **The Linkly MCP connector** — the same hosted server
  (`https://mcp.linklyhq.com`) listed in the Anthropic Connectors Directory.
  OAuth sign-in, no API keys. 25 tools covering links, custom domains,
  click analytics, and webhooks.
- **`/shorten`** — shorten the URL you're looking at (or any URL you give
  it), with an optional friendly name.
- **`link-hygiene` skill** — bulk-shorten the links in a README or doc,
  apply consistent UTM tags, and report click performance for a document's
  links, flagging dead ones.

## Setup

See [SETUP.md](SETUP.md). Short version: have a Linkly account (free tier is
fine) and complete the OAuth prompt the first time a tool runs.

## Requirements

- A Linkly account — https://linklyhq.com
- Claude Code, or Cowork with plugin support

## Privacy Policy

This plugin connects Claude to your Linkly workspace through Linkly's hosted
MCP server. Link data and analytics you access stay between Claude and
Linkly's API; the plugin itself stores nothing and runs no code of its own.

- Linkly privacy policy: https://linklyhq.com/privacy
- Terms of service: https://linklyhq.com/support/terms

Data handling in brief: the connector reads and writes only within the
Linkly workspace you authorize via OAuth. It does not access conversation
data beyond what is needed to execute the tool calls you make, and Linkly
does not receive your conversation history.

## Support

- Documentation: https://linklyhq.com/support/mcp-server
- Contact: support@linklyhq.com
- Issues: https://github.com/Linkly-HQ/linkly-claude-plugin/issues

## License

MIT — see [LICENSE](LICENSE).
