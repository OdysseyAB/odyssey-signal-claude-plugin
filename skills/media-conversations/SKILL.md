---
name: media-conversations
description: How brands are talked about in media and social channels in Odyssey Signal - share of voice, mentions, reach, PR value, sentiment, and breakdowns by channel type such as podcasts, radio and social media. Use for "share of voice", "media", "mentions", "PR value", "reach", "media sentiment", "what do people say about us", "podcasts", "social media".
---

# Media and social conversations

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient:** the Signal must have a `conversation` DataSet (`describe_signal`). Its base counts conversations that
   mention a brand, never respondents. `list_metrics` on it gives the share metrics (share of conversations,
   frequency, reach, PR value), the volume metrics and the sentiment metrics; `describe_dataset` gives its
   dimensions and periods, which differ from the survey's.
2. **Choose** with the user: share of voice against competitors, volume over time, or sentiment.
3. **Query** each metric with the brands of interest and the standard period. Breakdowns: `group_by` sentiment or
   channel type (dimensions as `describe_dataset` lists them); several in one `group_by` as a cross-tab.
4. **Present** share of voice as a ranked table or stacked bar, volume as a trend, sentiment as shares, each with
   its base (number of conversations) and warnings.

## Markets

On this DataSet a market can only be a filter, not a breakdown: to compare markets, run one query per market (ids
from `list_dimension_values`) and show them side by side.

## Not available here

The individual posts, episodes and articles behind the figures cannot be read through this server. Say so, and point
to the Conversations page in the Odyssey portal.

## Next questions

Offer: share of voice over time (`brand-trends`), sentiment per channel type, or how AI assistants mention the brand
(`ai-visibility`).
