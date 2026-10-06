# Technical Case Study

## Goal
Build an explainable crop-scanning app that is honest about what it measures. The brief was a scanning product with trend charts, alerts and recommendations; the engineering choice was to do real pixel analysis instead of presenting a fake classifier.

## Approach
**Measurement.** Pixels are classified in HSV: green hue 65-170 degrees, yellow 42-65 degrees with higher saturation, brown below 42 degrees with high saturation and low value. Yellow and brown are reported as shares of detected leaf area, so a sparse canopy does not look "healthier". Excess-Green (2g - r - b on chromatic coordinates) and VARI are averaged over leaf pixels.

**Score.** `80% x (1 - 0.9 x yellow - 1.6 x brown) + 20% x ExG vigour`, clamped to 0-100. Brown is weighted more heavily than yellow. Status bands: 75 and above healthy, 55-74 watch, below 55 stressed.

**Heatmap.** Healthy, yellowing and browning pixels map to a green, amber and red ramp, smoothed slightly and blended over a desaturated copy of the photo.

**Recommendations.** Transparent rules on the measured values (brown at 4% and 10%, yellow at 10% and 25%, low canopy cover, a score drop of 12 or more). Each output carries a "because" line with the value that fired it.

**Demo data.** Synthetic canopy images are drawn with Pillow: leaf shapes, soil gaps and a per-field stress trajectory over about 12 weeks. They go through the production pipeline, so the dashboards are driven by computed results.

## Stack
Python, FastAPI, Uvicorn, SQLite, Pillow, NumPy; vanilla JavaScript, Chart.js, custom CSS.

## What is verified and what is not
Verified: the pipeline runs end to end on uploads and seeded images; thresholds respond sensibly to synthetic stress.
Not verified: accuracy on real field photos, lighting robustness, or any agronomic outcome. The thresholds are heuristics, not a calibrated model.
