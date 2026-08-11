---
name: link-hygiene
description: Audit, shorten, and track the links in a document, README, or campaign — bulk-shorten with consistent UTM tags, check click performance, and find dead or underperforming links using Linkly analytics
---

# Link hygiene with Linkly

Use this skill when the user wants to work on the links inside a document,
page, README, email draft, or campaign as a set — shortening them, tagging
them consistently, or checking how they perform. It relies on the Linkly MCP
connector's tools (`create_link`, `list_links`, `search_links`, `get_link`,
`update_link`, `get_analytics`, `get_analytics_by`).

If a tool call prompts for authentication, have the user complete the Linkly
OAuth sign-in and retry — no API keys are involved.

## Bulk-shorten links in a file

1. Extract the URLs from the file or text the user points at. Skip anchors,
   mailto:, localhost, and URLs that are already Linkly short links (hosts
   like `linkly.link`, `l.linklyhq.com`, or a custom domain the workspace's
   `list_domains` returns).
2. Before creating anything, show the user the list of URLs you intend to
   shorten and get a yes.
3. Create each with `create_link`, naming links after their context in the
   document (heading, link text) rather than the raw URL.
4. Offer to substitute the short URLs back into the file. Preserve the
   original URL in a comment or reference list if the user wants a record.

## Consistent UTM tagging

When the user wants campaign tagging, agree the convention once (source,
medium, campaign), then apply it uniformly: set `utm_source`, `utm_medium`,
`utm_campaign` on `create_link` rather than hand-appending query strings.
Reuse the workspace's existing conventions where visible — check a few
recent links with `list_links` and mirror their UTM style. Do not invent
values for links where the user did not ask for tagging.

## Check how a document's links are performing

1. Match the document's short links to workspace links via `search_links`
   (search by slug, name, or destination).
2. For each match, read `clicks_total` / `clicks_thirty_days` from the link
   record; for breakdowns, use `get_analytics_by` with `counter` set to
   `country`, `platform`, `referer`, or `destination`, filtered by `link_id`.
3. Report a compact table: link name, short URL, clicks (30d), top country
   or referrer. Call out links with zero recent clicks as candidates for
   removal or re-promotion.
4. `get_analytics` returns a time series when the user wants a trend rather
   than totals.

## Cautions

- `update_link` and `delete_link` overwrite or remove live redirects other
  channels may depend on — always confirm before changing an existing link's
  destination, and never delete links without an explicit ask.
- Creating a link consumes the workspace's plan quota; avoid re-creating a
  short link that already exists for the same destination — `search_links`
  by the destination URL first and reuse matches.
- Analytics default to a recent time window; pass explicit `start`/`end`
  arguments when the user asks about older periods.
