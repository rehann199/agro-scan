<div align="center">

# AGRO-SCAN

**Crop-health scanning with real pixel analysis: upload a canopy photo, get a colour-health score, a stress heatmap and rule-based next steps.**

**Web app**<br/>
FastAPI · SQLite · Pillow · NumPy · Vanilla JS · Chart.js

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?logo=chartdotjs&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

<table>
  <tr>
    <td><img src="assets/screenshots/agro-scan-dashboard.webp" width="420" alt="Farm overview dashboard with KPIs, weekly health trend, status donut and latest heatmaps" /></td>
    <td><img src="assets/screenshots/agro-scan-scan-result.webp" width="420" alt="Scan result showing the original photo beside a stress heatmap, metrics and recommendations" /></td>
  </tr>
</table>
<sub>Screenshots are real captures of a local build running on fictional demo data.</sub>

</div>

---

## Product at a Glance

| | |
|---|---|
| **What it is** | Reference implementation of a crop-scanning app with colour-based analysis |
| **Analysis** | HSV colour classification, Excess-Green and VARI, canopy cover, yellowing and browning shares |
| **Output** | 0-100 colour-health score, stress heatmap, rule-based recommendations, alerts |
| **Data** | Seeded fictional data: 3 farms, 8 fields, 60 scans from synthetic Pillow-drawn images |
| **Stack** | FastAPI, SQLite, Pillow, NumPy, vanilla JS, Chart.js |

## Product Showcase

<table>
  <tr>
    <td><img src="assets/screenshots/agro-scan-fields.webp" width="420" alt="Fields grid with crop, acreage, growth stage, health ring and sparkline" /><br/><sub>Fields with health rings, status and sparklines</sub></td>
    <td><img src="assets/screenshots/agro-scan-field-detail.webp" width="420" alt="Field detail with health trend chart, latest heatmap and scan table" /><br/><sub>Field detail: score trend with yellow and brown fractions</sub></td>
  </tr>
  <tr>
    <td><img src="assets/screenshots/agro-scan-upload.webp" width="420" alt="Upload flow with a generated sample image selected" /><br/><sub>Upload flow with a synthetic sample selected</sub></td>
    <td><img src="assets/screenshots/agro-scan-history.webp" width="420" alt="Scan history table with thumbnails, scores and compare action" /><br/><sub>Scan history with before/after compare and CSV export</sub></td>
  </tr>
  <tr>
    <td><img src="assets/screenshots/agro-scan-alerts.webp" width="420" alt="Alerts list with critical and warning items and the rule values that triggered them" /><br/><sub>Alerts, each with the measured value that fired it</sub></td>
    <td><img src="assets/screenshots/agro-scan-mobile.webp" width="200" alt="Mobile dashboard with bottom navigation" /><br/><sub>Mobile layout</sub></td>
  </tr>
</table>

## Key Features

- Farms and fields with crop, acreage, growth stage and latest health score
- Image upload with real pixel analysis: green cover, yellowing and browning, ExG and VARI
- Stress heatmap overlay beside the original image
- Per-field health trend charts, scan history and two-scan compare
- Alerts and recommendations from transparent threshold rules
- CSV export
- Built-in synthetic sample generator for trying the flow without a camera
- Responsive layout with phone navigation

## Architecture

One FastAPI service serves a REST API and a static single-page frontend. An analysis module (Pillow and NumPy) turns each image into metrics, a score and a heatmap; SQLite stores records and images live on disk. The seed script generates synthetic images and sends them through the same pipeline as uploads. See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Engineering Highlights

- Every number is computed from pixels with documented thresholds; the method is printed on each result
- Yellow and brown are shares of detected leaf area, and near-empty frames are rejected rather than scored
- Recommendations store the measured value that triggered them
- Seeded demo data goes through the real pipeline, so charts and alerts are genuine outputs
- Heatmaps are smoothed and blended for readability

## Status & Scope

This is a **reference implementation** with **colour-based analysis**. It has **no machine-learning model and no disease classifier**, and it is not a disease diagnosis; the footer says so on every page. Scores, heatmaps, recommendations and alerts are real computed outputs from rule-based logic. Thresholds were tuned on synthetic imagery and are not validated on real field photos. The demo build runs on seeded fictional data and has no authentication.

The original project folder this was named after contained only empty placeholder files; this app is a new build.

## Documentation

- [Product overview](docs/PRODUCT_OVERVIEW.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Technical case study](docs/TECHNICAL_CASE_STUDY.md)
- [Engineering challenges](docs/ENGINEERING_CHALLENGES.md)
- [Privacy and source](docs/PRIVACY_AND_SOURCE.md)

Rights and usage: [RIGHTS.md](RIGHTS.md)
