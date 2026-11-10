---
name: demand-space-map
description: Odyssey Signal's demand-space map - where the user's brand and competitors are positioned among the category's demand spaces, how large each demand space is, the category's drivers on the map, and brand profiles per demand space as a spider chart. Use for "positioning", "demand space", "map", "where do we sit", "white space", "brand profile spider".
---

# Demand-space map

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, ask rather than guess.

## Steps

1. **Orient:** Signal, DataSet (one with position metrics in `list_metrics`, unit `index`, `value_type` `point`),
   own brand, competitors.
2. **Choose the map** with the user (`get_map` `type`):
   - `brand_position`: brands placed on the map. Add the category's drivers (`drivers: true`) or demand-space sizes
     (`sizes: true`) only when the user asks for them.
   - `demand_space_sizes`: how large each demand space is.
   - `brand_profile`: a spider of each brand's strength per demand space. One line per brand, so name a few brands.
   When the DataSet has several position metrics, ask which (`metric`). A Double Index NET metric is never a
   position map: draw it as a `brand_profile`.
3. **Get the drawing rules once per map type** with `get_map_guide` (`type`, free of credits), in the theme the user
   wants (`light` or `dark`).
4. **Call `get_map`** with the brands (`brands`, own brand in `focus`) and the standard period. Each point comes
   placed (`draw.rho`, `draw.bearing_deg`) with sectors, colours and labels: draw it exactly as the guide says. Never
   place points yourself from `value`. If the answer has rings (`radial.rings`), it is a Double Index position: fetch
   its own guide too, `get_map_guide(type: "brand_position", variant: "position_di")`, before you draw.
5. **Describe** where the brands sit relative to each other and to the demand spaces.

## Reading a map

- A position has no order: never rank, average or sum brands by it.
- `demand_space` names the sector a point falls in (numbered from 1 at the top, clockwise, with the study's name
  where it has one).
- `context.polar.outside_map` true means the brand sits beyond the map's edge; `radius_true` says how far.
- A brand of type `ghost` (*Ghost 1*, …) is not a brand but the study's reference point for a demand space: use it to
  describe where real brands sit, never list, rank or count it.
- Drivers have one position, not one per period; their bubble size is the share choosing the driver.
- On a map indexed against the market's average NET brand, `net_count` says how many brands the average holds, and a
  null value means too few: say so.

## Over time

A map shows one period, and a map over time is not available here. To compare, fetch the map for each period
(`ending`, a period id from `list_periods`) and show them side by side; each map uses credits, so confirm the periods
with the user first; describe
movements in words, without computing distances.

## Next questions

Offer: the brand profile per demand space, the demand-space sizes, or the image behind a position
(`brand-image-and-drivers`).
