# Product Overview

AGRO-SCAN is a crop-health scanning app. A user uploads a top-down photo of a canopy or leaf, and the app measures how green, yellowing and browning the visible vegetation is, turns that into a 0-100 colour-health score, draws a stress heatmap, and suggests next steps using simple rules.

It is a **reference implementation**. The analysis is **colour-based**. There is no machine-learning model and no disease classifier, and the UI says so on every page: "Colour-based analysis; not a disease diagnosis."

## Who it is for
Growers and agronomy teams who want a quick, explainable read of canopy colour over time, and a starting point for a larger monitoring product.

## What it does
- **Dashboard.** Acre-weighted average health, field and scan counts, open alerts, weekly average trend, field status split, lowest-scoring fields and latest heatmaps.
- **Fields.** Farms and fields with crop, acreage, growth stage, latest score, status and a sparkline; filter by farm.
- **Field detail.** Health trend (score line with yellow and brown bars), latest heatmap, active recommendations and a full scan table; per-field CSV export.
- **New scan.** Drag and drop (or browse) a JPG/PNG, pick a field, add a note. If no photo is handy, generate a synthetic sample at healthy, early-stress or advanced-stress levels.
- **Scan result.** Original beside heatmap, canopy cover, green cover, yellowing %, browning %, mean ExG and VARI, change versus the previous scan, and recommendations that each show the measured value that triggered them.
- **History and compare.** All scans with filters; tick two to compare before and after.
- **Alerts.** Raised automatically for warning and critical rules; can be acknowledged.
- **CSV export** of scans with metrics and top recommendation.

## Demo data
The demo build runs on seeded fictional data: 3 farms, 8 fields and 60 scans. The seeded images are synthetic leaf and canopy images drawn with Pillow and analysed by the same pipeline an upload goes through.

## Not included
Disease or pest identification, yield prediction, drone or satellite imagery, user accounts, multi-user roles and notifications.
