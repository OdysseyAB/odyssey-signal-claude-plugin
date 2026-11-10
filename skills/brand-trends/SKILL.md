---
name: brand-trends
description: How brand KPIs in Odyssey Signal develop over time - a metric over months, quarters, half-years or years, moving averages, custom date ranges, unfinished periods, one or several brands, and comparisons with an earlier period. Use for "trend", "over time", "development", "last 12 months", "since last quarter", "year on year".
---

# Brand trends over time

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient:** Signal, DataSet, metric (`list_metrics`), own brand and competitors (`describe_dataset` → `defaults`).
2. **Choose the time axis.** `describe_dataset` → `period` lists the allowed granularities (month, quarter,
   half-year, year), the rolling options per granularity, and the standard. Unless the user asks for something else,
   keep the standard granularity and smoothing and set only `last` (how many periods, up to 120). Typical: `last` 12
   for months, 8 for quarters.
3. **Query** the metric with `last`, the brands to show (`brands` and `focus`), and nothing else changed.
4. **Present** a line chart or table: one series per brand, the period label from each row, value, base and warning.
   Mark periods with a low base. Say whether the figures are a moving average and over how many periods.

## Periods

- A custom range: `ending` (a period id from `list_periods`, exactly as listed) plus `last`.
- Unfinished last period: `complete_only: true` keeps only complete periods. Say a period is unfinished only when
  the answer says so (`meta.period.last_complete` is false, or a warning). With `meta.period.pooled` true, each
  figure covers the whole window as one span: say so.
- Rolling windows for months are 1, 3 or 12 only. Rolling 6 or 9 months is not available here; say so and offer 3 or
  12. When the user asks for a moving average ("3-month average"), set `rolling` to one of the values `period.options`
  lists (months 1, 3 or 12; quarters 1–4; half-year and year only 1) and say "moving average over N periods" with
  every figure.
- Over several periods a row names its period even when you did not group by it: read that label, never add rows up.

## Comparing two periods

To compare with the previous period or the same period last year, query with `last` covering both (for example
`last: 2` for the previous period, or `last: 5` with quarters for the same quarter last year) and show the two rows,
each read by the period it names. Never build a period id yourself. Never compute the difference or a percentage change, and never call a change significant: significance is
not available here.

## Several KPIs over time

One metric per query: query each KPI with the same period settings and brands, then show them together (small
multiples or one table). Never put two metrics with different units on one axis without saying so.

## Next questions

Offer: the same trend for competitors, the trend per target group or market (`target-group-analysis`), or the image
profile for the same period (`brand-image-and-drivers`).
