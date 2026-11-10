---
name: brand-health-check
description: A snapshot of how a brand is doing in Odyssey Signal right now - its key brand KPIs (awareness, consideration, preference, NPS, scores) for the latest period, against the competitor average, with its rank and base warnings. Use for "how is our brand doing", "give me our KPIs", "brand health", "where do we stand", or what a metric means.
---

# Brand health check

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient** (skip what you already know in this conversation): the Signal, the DataSet (usually
   `perception:primary`), the user's own brand (`describe_dataset` → `defaults.own_brands`; ask if there are several)
   and the metrics (`list_metrics`).
2. **Pick the KPIs.** Propose a short set from the metric groups, typically from *Attitudinal Brand Strength*
   (awareness aided and unaided, consideration, preference or mind share, usage) plus NPS or a satisfaction score
   when the Signal has one. Confirm the set with the user: each query uses credits.
3. **Query each KPI** with the same settings: standard period (leave period arguments out), own brand in `focus`,
   `include: ["reference_line", "rank"]`, and the competitor set (leave `brands` out for the Signal's standard set, or
   the user's own list).
4. **Present** one table: KPI, value (in its unit), competitor average (`context.reference`), rank
   (`context.rank`, and which brands it covers), base, warning. Say which period it is, whether it is a moving average, and
   which markets it covers.

## Reading the figures

- `context.reference` is the average over exactly the brands in the query. If `list_metrics` gives the metric its
  own `reference`, it is that figure instead (as `reference.description` says): name it that way.
- Rank only means something against the whole competitor set: never query the brand alone for a rank.
- NPS and net scores are points from -100 to 100, not percentages. A mean score is on the question's own scale.
- A row with `base_warning: low`: show it, but draw no conclusion. `caution`: add the reservation.
- What a metric means: give its `description` and `business_question` from `list_metrics`. The verbatim question
  wording is not available here; say it is in the portal.

## Change since last period

The server does not return a change figure, and you must not compute one. Query the KPI with `last: 2` (the current and
the previous period) and read each row by the period it names; never build a period id yourself. Show both figures side
by side and say which is higher. Whether a change
is statistically significant is not available.

## Next questions

Offer: the trend behind a KPI (`brand-trends`), the full competitor ranking (`competitor-benchmark`), the KPI by
target group (`target-group-analysis`), or the funnel (`brand-funnel`).
