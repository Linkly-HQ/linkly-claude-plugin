---
description: Shorten one or more URLs with Linkly, optionally naming the link
argument-hint: "[url] [name for the link]"
---

Create Linkly short links for the URL(s) the user wants shortened.

Which URLs: if the arguments contain one or more URLs, use those. If the
arguments are empty, use the URL(s) most recently discussed in the
conversation or visible in the file the user is working on. If it is
genuinely ambiguous which URL the user means, ask rather than guess.

For each URL, call the Linkly `create_link` tool:
- `url`: the destination. If it lacks a scheme, assume `https://`.
- `name`: any non-URL text in the arguments; otherwise derive a short,
  human-readable name from the page or context (e.g. "Spring sale landing").
- Pass UTM parameters only if the user asked for them or the destination
  URL already carries them.

If the Linkly connector is not yet connected, the tool call will prompt the
user to sign in with Linkly via OAuth — tell them to complete that and then
retry; there are no API keys to configure.

Reply with the short URL (the `full_url` field) for each link, one per line,
alongside its name. If the user asked to shorten links inside a file, also
offer to replace the originals in place — but do not edit the file unless
they say yes.
