---
name: target-group-analysis
description: Break Odyssey Signal brand KPIs down by target group - gender, age, region, market and other configured dimensions - filter to a target group such as women 18-34, build cross-tabs, and show how answers to a question are distributed. Use for "by age", "by gender", "among young people", "target group", "segment", "breakdown", "cross-tab", "answer distribution".
---

# Target group analysis

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient:** Signal, DataSet, metric. `describe_dataset` lists the dimensions and marks each as `filterable` and
   `groupable`. Only those can be used. `list_metrics` → `supported_dimensions` says which a metric supports.
2. **Breakdown or filter?**
   - "How does it differ by age?" → `group_by: ["age_group"]` (a breakdown).
   - "How do women aged 18–34 see us?" → `filters` with value ids from `list_dimension_values` (a target group).
     Send ids exactly as that list gives them (integers for survey answers).
   - Several breakdowns at once (age × market): put them all in one `group_by` as a cross-tab rather than one query
     each.
3. **Query** with the brands of interest (`focus` for the own brand) and the standard period.
4. **Present** a table with one column per group, value, base and warning per cell. Breakdowns make bases small: mark
   every `low` cell and draw no conclusion from it; flag `caution` cells.

## Answer distributions

For a single-choice question (for example how often people donate), the metric returns one row per answer (dimension
`answer`). Show the distribution as given; never add answers together into a new figure.

## Limits

- Only the target groups and dimensions configured in the Signal exist. A custom segment (say "families with
  children in the north") cannot be built here unless it is a configured dimension: say so.
- A row-limit error means the question is too wide: use fewer breakdowns or periods rather than raising `limit`.
- An empty filtered answer means no data for that group, not 0 %.

## Next questions

Offer: the trend for one target group (`brand-trends`), the funnel for it (`brand-funnel`), or competitors within it
(`competitor-benchmark`).
