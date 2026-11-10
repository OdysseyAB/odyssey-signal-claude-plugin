---
name: getting-started
description: Start here for any question about Odyssey Signal brand-tracking data. Finds the right organization, Signal, DataSet, metric, own brand, competitors and period, sets the rules every answer follows (figures exactly as given, base and warnings, never compute new figures), and builds multi-metric brand reports, charts and spreadsheets from the answers. Use when the user mentions Odyssey, a Signal, brand tracking, or asks what data they can see.
---

# Getting started with Odyssey Signal

Odyssey Signal holds brand-tracking data: survey trackers (brand perception), media and social conversations, and
how AI assistants mention brands. The `odyssey-signal` MCP server reads it with the user's own account. Every tool is
read-only. `query` and `get_map` use the organization's credits; the other tools are free.

## The rules for every answer

These apply in every Odyssey Signal skill.

1. **Every figure comes from a tool answer in this conversation.** Report it exactly as given (value, unit, brand,
   market, period). Never compute a new figure: no difference or change between two figures (give both and say which
   is higher), no ratio, conversion rate, sum, average, index or rescaling. If the user needs a figure no tool
   returns, say the Signal does not provide it. Never estimate, extrapolate or fill a gap, and never invent a reason,
   trend or explanation the answer does not give. Match rows to brands, markets and periods by their `label`, never by
   row order.
2. **Show the base.** Each row has `base` (respondents, conversations or AI answers; `list_metrics` says which) and
   `quality.base_warning`. `low`: draw no conclusion from that row. `caution`: give the figure with that reservation.
3. **One metric per `query`.** For several metrics, query them one after another with the same period, brands and
   breakdown, then present them together.
4. **Ask rather than guess.** When the organization, Signal, metric, market or comparison is unclear, ask one
   question with 2–4 concrete options taken from the tool answers, and recommend one. When a tool answer ends with
   "Ask the user:", follow it.
5. **Say plainly what is not available** (see the end of this file) instead of approximating it. Before you say a
   metric is not measured, check `list_metrics` on every DataSet of the Signal; never swap in a different metric for
   the one the user asked for without saying so and asking.
6. Name the source of every figure: Signal, DataSet, metric name, market, period. Never mix Signal figures with the
   user's own files in one figure.
7. Before you present a table, chart or report, check every figure again against the tool answer it came from.

## Orient before you query

1. `list_organizations`. If there are several and the user has not said which, ask. Then `list_signals`.
2. `describe_signal`: the DataSources, their DataSets and markets. Typical DataSets: `perception:primary` (the main
   brand list), `perception:secondary` (a second brand list, such as retailers), `conversation` (media and social),
   `visibility` (AI assistants).
3. `describe_dataset`: which dimensions can filter (`filterable`) and break down (`groupable`), the allowed periods
   (`period.standard`, `period.options`), and `defaults` (the user's own brands, the standard competitor set).
4. `list_metrics`: the metrics with `id`, name, description, business question, unit and base. Metrics come in groups
   (for example *Attitudinal Brand Strength*, *Brand Perception*, *Marketing Effectiveness Funnel*,
   *Market Landscape*, *Customer Satisfaction*); the groups differ per Signal. **The same name can appear more than
   once** (two "Consideration" metrics, say): always pick by `id`, and when two match, explain the difference from
   their `description` and ask. Pass the metric's `id` as `query`'s `metric`.
5. `list_brands` for brand ids (unique only within their brand list: never mix lists), `list_dimension_values` for
   filter values, `list_periods` for when data exists.

## Defaults that save questions

- **Period:** use the DataSet's standard period (`period.standard`) unless the user asks for another; then use only
  one of `period.options`. For an earlier end, pass a period id from `list_periods` as `ending`. Never invent a date.
  To compare with an earlier period, query with `last` above 1 (for example `last: 2` for the previous period) and
  read each row by the period it names, rather than building a period id yourself.
  With `rolling` above 1 every figure is a moving average: say over how many periods.
- **Brands:** leave `brands` out for the Signal's standard competitor set, and put the user's own brand in `focus`.
- **Markets:** without a market filter, a figure averages over every market the Signal has. Say so, or break down by
  `market` to show each.
- An empty answer means no data matched (not 0 %). Check the period and filters before concluding anything.

## Brand reports, charts and spreadsheets

For a report ("quarterly brand update", "board slide on our brand"):

1. Agree the scope with the user first: Signal, own brand, competitors, period, markets, and which areas (health,
   trends, competitors, target groups, funnel, image, map, conversations, AI visibility). Each `query` and map uses
   credits, so confirm the list of metrics before you run it.
2. Query each metric with the same period, brands and markets. Use the skill for each area.
3. Build the report from the answers only. Put the source line (Signal, period, market, base) under every table and
   chart. Draw charts yourself from the returned rows; for maps use `get_map` and `get_map_guide`.
4. For a spreadsheet, put each answer's rows with brand, market, period, value, unit, base and base warning.
5. Check every figure against its tool answer before handing the report over.

## Not available through this server

Say so plainly and point to the Odyssey portal where it exists there:

- Statistical significance and confidence intervals.
- Rolling 6 or 9 months (rolling months are 1, 3 or 12).
- The verbatim question wording (use the metric's description and business question, and say the exact wording is
  in the portal).
- Custom segments not configured in the Signal, merged brands, saved views.
- The individual conversation posts and AI answers behind the figures.
- Derived driver importance (relative weights).

## Next questions

After each result, offer two or three next questions worth asking, such as the trend behind a figure, the competitor
ranking, or the same figure per target group.
