# Reverse refraction solver

A Bislin-style curvature calculator run backwards. Instead of assuming a
refraction coefficient and predicting what is visible, you enter what a camera
actually saw — observer height, target distance, target height, visible
height — and it solves for the refraction the atmosphere had to supply:

- on a **globe** (R = 6371 km): the implied coefficient k, and
- on a **flat plane**: the implied k' (light bending away from the surface),

each with the temperature gradient that coefficient requires
(k = 503·(P/T²)·(0.0343 + dT/dh)) and the resulting air temperature at
target-summit height, stated against the surface temperature.

Live at: https://funwithscience.net/refraction-solver/

## Reference bands on the scale

- Normal marine k = 0.10–0.20, with ticks at 0.13 (Gauss survey standard)
  and 0.17 (ISA sea-level lapse).
- The hatched band converts the 10–15 arcminute false-sea-horizon lifts that
  R. L. Ives documented as "a standard midday condition" on the Gulf of
  California (J. Franklin Institute 252, 285–295, 1951) into the k producing
  the same angular lift over the entered path — it moves with distance.
- Near-surface k is measured to swing far outside the survey band
  (Hirt et al., J. Geophys. Res. 2010).

## Notes

Single self-contained HTML file (`docs/index.html`), no dependencies, no
network calls. The "visible ±" field propagates measurement uncertainty into
a k range on both branches. Known limits are stated in the page footer:
single-k is a whole-path average and cannot model layered ducts or the
mirage skin in the last metre above the water.

The preset loads the Isla Tortuga case (camera 0.15 m, 58.9 km, 228 m summit,
86 ± 14 m visible) from the funwithscience.net analysis of a widely shared
flat-earth video.
