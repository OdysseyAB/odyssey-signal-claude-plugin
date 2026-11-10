---
name: brand-image-and-drivers
description: Brand image in Odyssey Signal survey trackers - which attributes and emotions a brand is associated with, brand profile and driver performance indices against the category, the category's drivers, customer-journey steps, and barriers. Use for "what are we associated with", "brand image", "brand profile", "attributes", "drivers", "strengths and weaknesses", "why do people choose".
---

# Brand image and drivers

Follow the rules in the `getting-started` skill: figures exactly as given, base and warnings, one metric per query,
ask rather than guess.

## Steps

1. **Orient:** Signal, DataSet, own brand, competitors. In `list_metrics`, look in the group *Brand Perception* and
   similar for image metrics such as *Brand Profile*, *Brand Driver Performance*, emotional or functional attributes,
   communication profile, barriers. `list_drivers` lists the category's drivers.
2. **Choose the view** with the user:
   - **Associations:** an attribute metric broken down by attribute (`group_by` the attribute dimension the metric
     supports): which attributes each brand is linked to.
   - **Index against the category:** metrics in unit `index` (for example *Brand Profile*, *Brand Driver
     Performance*) put a brand against an average of 100. Above 100 means stronger than that average on the
     attribute or demand space, below 100 weaker. Use the metric's `description` to say what the average is.
   - **Per demand space:** a brand profile per demand space, or `get_map` type `brand_profile` (see
     `demand-space-map`).
   - **Where the drivers sit:** `list_drivers` names the category's drivers; to show them on the map, use `get_map`
     type `brand_position` with `drivers: true` (latest period only: a driver has one position, not one per period;
     see `demand-space-map`).
3. **Query** with the brands of interest (a few brands keep the table readable) and the standard period.
4. **Present** a heat table: attributes as rows, brands as columns, value, with base warnings. Quote the highest and lowest
   returned values per brand as given, without averaging or ranking beyond them.

## Customer journey and barriers

A journey or barrier metric returns one row per step or barrier (attribute dimension). Show them in the order the
answer gives, with bases.

## Reading index metrics

- An index metric whose `fields` carry `net_count` indexes each brand against the average NET brand of its market
  (100 = that average); a null value means the market had too few brands for an average (`meta.warnings` says so),
  and a `low` row is shown but kept out of the average. Explain that rather than leave it unexplained.
- Never average or sum index values across attributes or brands.

## Not available here

Derived driver importance (relative weights), and gap or brand-fit analyses beyond the index metrics the Signal
provides. Say so, and offer the driver performance or brand profile indices instead.

## Next questions

Offer: the demand-space map (`demand-space-map`), the image for a target group (`target-group-analysis`), or how
media talk about the brand (`media-conversations`).
