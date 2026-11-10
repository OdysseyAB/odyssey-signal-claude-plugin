---
name: competitor-benchmark
description: Compare brands in Odyssey Signal - rankings on a KPI, the user's own brand against a chosen competitor set and its average, the standard competitors, secondary brand lists such as retailers, markets side by side, and two KPIs plotted against each other. Use for "competitors", "benchmark", "ranking", "top brands", "versus", "compared with", "which market".
---

# Competitor benchmark

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient:** Signal, DataSet, metric, and the brands. `describe_dataset` → `defaults` gives the user's own brands
   and the Signal's standard competitor set. `list_brands` gives the ids.
2. **Agree the competitor set.** The standard set (leave `brands` out), or the user's own list (`brands`, as integer
   ids). The average and the rank are computed over exactly these brands, so say which brands they cover.
3. **Query** with `include: ["reference_line", "rank"]` and the own brand in `focus` (it is then included even outside
   a top-N).
4. **Present** a ranked table or bar chart: brand, value, rank, base, warning, and the competitor average as a line.
   Match rows to brands by their `label`, never by row order.

## Brand lists

A Signal can have more than one brand list, each its own DataSet (for example `perception:primary` for products and
`perception:secondary` for retailers). A brand id is unique only within its list: never mix ids or figures from two
lists in one comparison.

## Markets

- Side by side: `group_by: ["market"]`, or a market filter with ids from `list_dimension_values`.
- Without a market filter a figure averages over every market the Signal has: say so, or break down by `market`.
- Narrowing the brand list to a vertical or end market: if `describe_dataset` lists such a dimension as
  `filterable`, filter on it; otherwise say the Signal cannot narrow the brand list this way.
- A brand not measured in a market has no row there: say it is not measured, never show 0.

## Two KPIs against each other

For a quadrant (for example awareness against consideration), query each metric with the same brands and period and
plot one against the other. Do not compute anything from the pair; describe where brands sit.

## Not available here

Merged brands (several brands reported as one), significance of a difference between brands, and confidence
intervals. Say so.

## Next questions

Offer: the trend for the top brands (`brand-trends`), where the gap comes from in the funnel (`brand-funnel`), or how
the brands differ in image (`brand-image-and-drivers`).
