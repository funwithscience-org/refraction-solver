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
- Indicative regime bands above the survey range: minor looming 0.20–0.35,
  major looming 0.35–0.60, duct / Fata Morgana above ~0.60 (k = 1: light
  follows the surface). The upper regimes are documented as locally routine
  in some waters — Ives measured 10–15 arcminute false-sea-horizon lifts as
  "a standard midday condition" on the Gulf of California (J. Franklin
  Institute 252, 285–295, 1951), equivalent to k ≈ 0.6–0.95 over ~55 km.
- Near-surface k is measured to swing far outside the survey band
  (Hirt et al., J. Geophys. Res. 2010).

## Credit

Inspired by Walter Bislin's Advanced Earth Curvature Calculator
(https://walter.bislins.ch/bloge/index.asp?page=Advanced+Earth+Curvature+Calculator),
the standard forward solver of the genre; this tool runs the same physics in
the inverse direction, and borrows his k-to-temperature-gradient formulation.

## Notes

Single self-contained HTML file (`docs/index.html`), no dependencies, no
network calls. Below the scale, two eye-view panels draw the scene each model
must produce — target slab, elevation grid lines, and the sea horizon at the
solved k — with a dashed line marking that model's standard-air horizon. The "visible ±" field propagates measurement uncertainty into
a k range on both branches. Known limits are stated in the page footer:
single-k is a whole-path average and cannot model layered ducts or the
mirage skin in the last metre above the water.

The default values load the Isla Tortuga case (camera 0.15 m, 58.9 km,
228 m summit, 86 ± 14 m visible) from the funwithscience.net analysis of a
widely shared flat-earth video.
