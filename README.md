# violetFlow

**A low-cost, open-source, self-optimizing flow reactor that runs its own chemistry experiments.**

violetFlow pumps reactants through a temperature-controlled coil, measures the product with an inline optical detector, and uses Bayesian optimization to choose the next experiment without anyone touching it. The first target reaction is the alkaline fading of crystal violet (CV), a well-characterized benchmark that lets the system be checked against published kinetics.

> **Status: early build.** No hardware is finished yet. This README describes my plan and will undoubtedly change throughout the project development process.

---

## Why

Automated flow chemistry systems ("self-driving labs") usually cost tens of thousands of dollars. violetFlow asks how much of that capability can be reproduced for a few hundred dollars, and where a cheap system stops being reliable.

**Research question:**
*How accurately can a low-cost, self-optimizing flow reactor measure reaction kinetics, and how much of its error can be corrected with physical models and smarter experiment selection?*

## How it works

```
 Pump A (dye) ──┐
                ├── mixer ── reactor coil (in water bath) ── light sensor ── waste
 Pump B (base) ─┘                                               │
       ▲                                                        │
       └──────────── controller picks the next settings ◄───────┘
```

1. Two 3D-printed syringe pumps push crystal violet and sodium hydroxide into a mixer.
2. The mixture flows through a coil of tubing in a water bath. How long it spends in the coil (the residence time, τ = V/Q) is set by the flow rate.
3. A light-tight detector measures how much purple is left at the outlet (via Beer-Lambert law).
4. The controller fits a model to the results and chooses the next flow rate, concentration ratio, or temperature.

## Project goals

| Areas | What violetFlow will measure or show |
|---|---|
| Chemistry | Rate law, activation energy (Arrhenius & Eyring), kinetic salt effect |
| Chemical engineering | Residence time distribution, non-ideal reactor behavior, scale-up |
| Physics | Laminar flow and Taylor dispersion, Dean mixing in coils, optical detection limits |
| Applied math | Advection-diffusion-reaction modeling, parameter estimation, optimal experiment design |
| Data science | Bayesian optimization vs. grid/random/human strategies, uncertainty quantification |

## Repository layout

```
hardware/    CAD (STEP + STL), BOM, assembly
firmware/    Arduino code to control pumps + sensors
software/    Control loop, optimizer, digital twin
analysis/    Notebooks for reproduction of data
data/        Raw experimental runs (unedited, unfiltered)
docs/        Documentation site, logs
```

## Checklist

- [ ] Build and calibrate pump A (gravimetric, target ±2% flow accuracy)
- [ ] Build detector and test against linearity of Beer-Lambert law
- [ ] Build pump B and plumb flow path
- [ ] Measure residence time distribution with tracer tests
- [ ] First CV kinetics run at room temperature
- [ ] Temperature series and activation energy
- [ ] Closed-loop Bayesian optimization campaigns
- [ ] Write-up and preprint

## Safety

Dispose of all household waste at nearest SWA household waste collection facility.

## License

Code is released under the [MIT License](LICENSE). Hardware design files will be released once they are published.

## Author

Paxton Cava
