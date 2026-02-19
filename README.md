# Gamma & Beta RNG via Acceptance–Rejection (PSTAT 194 Midterm Group Project)

This repo contains our PSTAT 194 midterm group project implementing acceptance–rejection RNG algorithms from:
**Dieter & Ahrens (1974), “Acceptance-Rejection Techniques for Sampling from the Gamma and Beta Distributions.”**

## What’s included
- `final_version.Rmd` — full implementation + write-up (all code is inside)
- `final_version.pdf` — knitted report
- `slides_final.pdf` — presentation slides

## Methods implemented
We implement a Gamma(shape = a, rate = 1) RNG using a routing “master” function that selects an algorithm by `a`:

- **GS** for `0 < a ≤ 1` (piecewise envelope)
- **GC** for `1 < a ≤ 2.53` (Cauchy envelope)
- **GO** for `a > 2.53` (normal–exponential split with squeeze bounds)

We also generate **Beta(a, b)** using the Gamma-ratio method:
If `X ~ Gamma(a,1)` and `Y ~ Gamma(b,1)` independent, then `X/(X+Y) ~ Beta(a,b)`.

## Verification
For each method we generate 10,000 samples and compare against the theoretical distribution using:
- histogram + theoretical density overlay
- Kolmogorov–Smirnov test against `pgamma` / `pbeta`

All KS test p-values were > 0.05 in our runs (consistent with the target distributions).

## Authors
Harrison Funk, Jayden Gould, Elijah DiFuria, Kian Jadbabaei
