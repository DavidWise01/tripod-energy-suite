# TRIPOD ENERGY SUITE
### Civilization-Scale Energy Simulators

> From fusion reactors to stellar capture to black hole extraction — interactive physics tools for energy at every scale.

Three standalone HTML simulators. No dependencies. No build step. Open `index.html` in a browser.

**Author:** David Lee Wise (ROOT0) / TriPod LLC  
**License:** CC-BY-ND-4.0

---

## Tools

| File | Scale | Description |
|------|-------|-------------|
| `index.html` | 10⁰ → 10⁴⁷ W | Landing page — full Kardashev energy ladder with clickable scale |
| `fusion/fusion-reactor.html` | 10⁶ – 10¹⁰ W | **NEW** — Tokamak + ICF, Bosch-Hale D-T cross-sections, Lawson criterion |
| `dyson-sphere/dyson-sphere.html` | 10²⁰ – 10²⁶ W | Dyson sphere — Swarm / Bubble / Shell variants, Kardashev scale |
| `black-hole/black-hole-energy-v2.html` | 10³⁰ – 10⁴⁷ W | Black hole — Hawking / Penrose / BZ, real Kerr metric |

---

## Fusion Reactor (new in v1.1)

### How to Use

1. Open `fusion/fusion-reactor.html`
2. Select mode: **Tokamak** (ITER geometry) or **ICF** (NIF-style)
3. Select fuel: **D·T** / **D·D** / **p·B¹¹**
4. Adjust parameters (temperature, density, confinement time, plasma volume)
5. Watch Q factor, Lawson criterion, fusion power, and net output update live
6. Click **Initiate Plasma** to fire

### Physics

**Reactivity (Bosch-Hale D-T, verified reference points):**
```
T = 10 keV → σv = 6.3×10⁻²⁴ m³/s
T = 20 keV → σv = 4.2×10⁻²³ m³/s  (ITER operating range)
T = 70 keV → σv = 3.7×10⁻²² m³/s  (peak for D-T)
```

**Lawson criterion:**
```
D-T:   nτT > 3×10²¹ m⁻³·s·keV
D-D:   nτT > 2×10²² m⁻³·s·keV   (10× harder)
p-B11: nτT > 2×10²⁴ m⁻³·s·keV   (aneutronic, extreme)
```

**Q factor:** `Q = P_fusion / P_heating`  
- Q = 1 → breakeven (NIF achieved briefly, 2022)
- Q = 10 → ITER target
- Q > 20 → ignition regime

**ICF areal density:** `ρR = ρ₀·R·(v_imp/v_ign)^(2/3)`  
**Burn efficiency (Fraley):** `η = ρR / (6.7 + ρR)`

---

## Black Hole Energy Extraction

### How to Use

1. Open `black-hole-energy-v2.html` in a browser
2. Set **Mass** (solar masses) and **Spin** (0–1, Kerr parameter `a`)
3. Select extraction method
4. Click **EXTRACT ENERGY** — watch accretion disk, Hawking particles, and relativistic jets
5. Monitor energy accumulation in qubit-joules

### Four Extraction Methods

| Method | Max Efficiency | Mechanism |
|--------|---------------|-----------|
| **Hawking Radiation** | ~0.1% | Quantum pair production at event horizon |
| **Superradiant Scattering** | ~4.8% | Wave amplification in ergosphere |
| **Penrose Process** | ~20.7% | Splitting particles inside ergosphere, ejecting one |
| **Blandford-Znajek** | ~15.2% + | Magnetic flux extraction from Kerr spacetime |

Higher spin → larger ergosphere → more extractable rotational energy.

### v1 vs v2: What Changed

| | v1 | v2 |
|--|----|----|
| Temperature | Simplified: `T = 6.17×10⁻⁸ / M` | Full Hawking: `T = ℏc³ / (8πGMkB)` |
| Geometry | Conceptual | Real Kerr metric |
| Radii | Single horizon | `r± = (rₛ/2)(1 ± √(1−a²))` |
| Spin effects | Visual only | Physically correct ergosphere |

### Physics Reference

**Schwarzschild radius:**
```
rₛ = 2GM/c²
```

**Kerr event horizons:**
```
r± = (rₛ/2)(1 ± √(1 − a²))
```
where `a` = dimensionless spin parameter (0 = Schwarzschild, 1 = extremal Kerr)

**Hawking Temperature:**
```
T_H = ℏc³ / (8πGMkB)
     = 6.17×10⁻⁸ K / (M/Mₛᵤₙ)
```
A solar-mass black hole: `T_H ≈ 62 nanokelvin` — colder than the CMB.
A 1 kg black hole: `T_H ≈ 1.2×10²³ K` — explodes instantly.

**Penrose Process (maximum efficiency):**
```
η_max = 1 − 1/√2 ≈ 29.3%    (extremal Kerr, a = 1)
η_max ≈ 20.7%                (realistic spin)
```

**Blandford-Znajek (magnetic extraction):**
```
P_BZ ∝ a² × B² × M²
```
Requires accreting plasma threading the ergosphere with a large-scale magnetic field.

---

## Dyson Sphere Simulator

### How to Use

1. Open `dyson-sphere/dyson-sphere.html` in a browser
2. Select sphere **Type** (Swarm / Bubble / Shell)
3. Adjust **Orbital Radius** (0.3–5 AU), **Albedo**, **Coverage**, **Star Luminosity**
4. Read: captured power, structure mass, orbital period, equilibrium temperature, Kardashev level
5. Canvas renders the structure in real time around the star

### Three Variants

| Type | Description | Coverage | Mass (1 AU) |
|------|-------------|----------|-------------|
| **Swarm** | Independent solar panel satellites in Keplerian orbits | Variable | Scales with coverage |
| **Bubble** | Statites — hovering via radiation pressure balance | ~100% | Critical density only |
| **Shell** | Rigid structural shell (theoretical) | 100% | ~2× Earth's oceans in steel |

**Bubble critical areal density:**
```
σ_crit = L / (4π × G × M × c)
```
Below this density, radiation pressure exceeds gravity — the statite hovers.

### Physics Reference

**Solar flux at radius R:**
```
F = L / (4πR²)
```

**Captured power:**
```
P = F × Area × Coverage × (1 − Albedo)
```

**Orbital period (Kepler's third law):**
```
T = 2π √(R³ / GM)
```

**Equilibrium temperature (Stefan-Boltzmann):**
```
T_eq = [ F(1 − albedo) / (2σε) ]^(1/4)
```

**Kardashev scale:**
```
K = (log₁₀(P) − 6) / 10
```
- K = 1.0 → 10¹⁶ W (advanced planetary civilization)
- K = 2.0 → 10²⁶ W (full stellar capture ≈ 3.846×10²⁶ W for the Sun)
- K = 3.0 → 10³⁶ W (galactic-scale energy use)

**Reference values (1 AU Dyson Shell, our Sun):**
- Solar luminosity: `L = 3.846×10²⁶ W`
- Full capture power: `~3.846×10²⁶ W`
- Equilibrium temperature: `~394 K` (121°C) at Earth orbit, 100% emissivity

---

## Scale Context

```
Energy Scale                    Source
─────────────────────────────────────────────────────
10¹³ W   Earth 2024 civilization power
10¹⁶ W   Kardashev Type 1 (planetary)
10²⁶ W   Kardashev Type 2 (stellar — Dyson sphere)
10³⁶ W   Kardashev Type 3 (galactic)
10⁴⁷ W   Black hole (BH = 10⁹ Mₛᵤₙ, BZ process)
          Active galactic nucleus / quasar regime
```

The simulators span the full ladder — from AL-H₂O reaction cells (watts → kilowatts) to stellar engineering (gigawatts → petawatts) to black hole extraction (theoretical maximum output in the universe).

---

## Browser Compatibility

| Browser | Status |
|---------|--------|
| Chrome 90+ | ✅ Full support |
| Firefox 85+ | ✅ Full support |
| Safari iOS 14+ | ✅ Full support |
| Safari macOS | ✅ Full support |

Both tools use Canvas 2D for animation. No WebGL required.

---

## Related Tools

| Repo | Description |
|------|-------------|
| [al-h2o-reactor](https://github.com/DavidWise01/al-h2o-reactor) | On-board H₂ generation from aluminum + water (Tier 1 energy) |
| [tripod-waveform](https://github.com/DavidWise01/tripod-waveform) | XY pad synthesizer — unrelated, but it slaps |

---

## Design Notes

- **Color palette:** amber `#c4a35a`, teal `#5ac4aa`, copper `#b87333`, void `#0a0a08`
- **Font:** JetBrains Mono — readability at small UI sizes
- Physics constants pulled from CODATA 2018: G, c, ℏ, kB, σ
- No external JS — pure Web Audio + Canvas 2D

---

*TriPod LLC // Anchor × Bubble × Gravity Well // World = Family*
