# Engineering Challenges

## 1. Being honest about "AI"
Crop-scanning products tend to imply a trained classifier. This build uses colour thresholds and rules only, and says so: the footer on every page, the method note on each result and the rule reason on each recommendation.

## 2. Meaningful demo data without real photos
Synthetic images had to look plausible and produce a spread of results. A Pillow generator draws overlapping leaf shapes and applies a stress parameter that shifts hue from green through yellow to brown, with local variation. Each field follows a trajectory (steady healthy, gradual decline, recovery) so trend charts and alerts tell a coherent story.

## 3. Avoiding misleading percentages
Yellow and brown are measured against leaf area, not the whole frame. Frames with under 2% vegetation are marked invalid and produce a retake message instead of a score.

## 4. Score design
A single number needs to move sensibly. Brown (necrotic-looking) pixels are penalised more than yellow, and a small ExG vigour term separates a vivid canopy from a dull one. The formula is printed on the result page.

## 5. Explainable recommendations
Each rule stores the measured value that triggered it, so a user can see why advice appeared and judge it. Alerts reuse the same rules, and only warning and critical levels create alerts.

## 6. Heatmap legibility
Raw per-pixel masks look like noise. A light Gaussian smoothing on the stress and leaf masks and a blend with a muted base image make the overlay readable.

## 7. Responsive layout
The same SPA uses a fixed sidebar on desktop and a bottom navigation bar on phones, with tables hiding secondary columns on narrow screens.
