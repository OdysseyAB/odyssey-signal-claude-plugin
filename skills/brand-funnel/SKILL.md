---
name: brand-funnel
description: The brand funnel in Odyssey Signal - awareness, consideration, preference, usage and the Signal's own funnel conversion metrics - for the user's brand and its competitors, showing how the brand scores at each step, with conversion only where the Signal provides its own conversion metric. Use for "funnel", "conversion", "where do we lose people", "from awareness to consideration", "path to purchase".
---

# Brand funnel

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient:** Signal, DataSet (usually `perception:primary`), own brand, competitors.
2. **Find the funnel steps** in `list_metrics`, usually in the group *Attitudinal Brand Strength*: for example
   awareness (aided, unaided or top of mind), consideration, preference or mind share, usage or purchase. The steps
   differ per Signal and category: propose the order from the metrics' names and descriptions and confirm it with the
   user. Pick by `id`: the same name can appear twice (read both descriptions and ask).
3. **Conversion figures:** many Signals have their own conversion metrics (for example *Upper Funnel Conversion*,
   *Lower Funnel Conversion*). Use those, and explain them with their `description`. Never compute a conversion
   rate, a share of a share ("consideration among those aware") or a drop-off yourself. If the Signal has no
   conversion metric, show the steps side by side and say that the conversion between them is not provided.
4. **Query each step** with the same period, brands and markets (own brand in `focus`, `include:
   ["reference_line"]`).
5. **Present** a funnel table or chart: one column per step, one row per brand, value, competitor average, base and
   warning. Describe where the own brand is above or below the competitor average at each step, using only the
   returned figures.

## Funnel over time or by group

- Over time: query each step with `last` (see `brand-trends`).
- By target group or market: add the same `group_by` or `filters` to every step (see `target-group-analysis`).
  Bases fall quickly in breakdowns: mark `low` cells.

## Next questions

Offer: the trend for the weakest step, the funnel for a target group, or what the brand is associated with
(`brand-image-and-drivers`).
