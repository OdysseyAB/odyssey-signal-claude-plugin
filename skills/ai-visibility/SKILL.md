---
name: ai-visibility
description: How AI assistants mention brands, from Odyssey Signal - share of visibility, answer penetration, first position and average position, sentiment, AI brand equity and AI brand profile per demand space, and breakdowns by AI provider, platform, model, prompt type and vertical. Use for "AI visibility", "generative engine", "GEO", "how do AI assistants talk about us", "AI search", "LLM mentions", "AI sentiment".
---

# AI visibility

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient:** the Signal must have a `visibility` DataSet (`describe_signal`). Its base counts AI answers, never
   respondents. `list_metrics` on it gives the visibility metrics (share of visibility, answer penetration),
   prominence (first position, average position), sentiment, and AI brand equity; `describe_dataset` gives its
   dimensions and periods.
2. **Choose** with the user: overall visibility against competitors, placement in answers, sentiment, a breakdown
   by AI engine, or the AI brand profile.
3. **Query** each metric with the brands of interest. Breakdowns: `group_by` provider, platform, model, prompt type
   or vertical (as `describe_dataset` lists them), several in one `group_by` as a cross-tab.
4. **Present** a ranked table or chart with base (AI answers) and warnings.

## Reading the figures

- Average position: lower is better (1 is mentioned first). Say so whenever you show it.
- A vertical narrows the brand list to one end market; say which vertical a figure covers.
- AI brand profile per demand space: `get_map` type `brand_profile` with the AI brand profile metric (see
  `demand-space-map`).
- A ranking of competitors is available; confidence intervals and significance are not. Never call one brand
  significantly ahead.

## Markets

On this DataSet a market can only be a filter, not a breakdown: run one query per market and show them side by side.

## Not available here

Citations (owned versus earned sources), AI overviews, organic search and shopping results, and the AI answers
themselves cannot be read through this server. Say so, and point to the AI Visibility pages in the Odyssey portal.

## Next questions

Offer: visibility over time (`brand-trends`), the breakdown by AI provider, or how media talk about the brand
(`media-conversations`).
