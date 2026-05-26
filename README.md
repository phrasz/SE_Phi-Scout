# φ-Scout

## 🔴 See Live
| Tool | Link |
|---|---|
| φ-Scout (generator) | **[phrasz.github.io/SE_Phi-Scout/phi-scout.html](https://phrasz.github.io/SE_Phi-Scout/phi-scout.html)** |
| 3D Visualizer | **[phrasz.github.io/SE_Phi-Scout/phi-scout-viz.html](https://phrasz.github.io/SE_Phi-Scout/phi-scout-viz.html)** |

> ⚠️ **Use a Chromium-based browser** (Chrome, Edge, Brave, etc.).  
> Firefox isolates `file://` pages from each other — the live link-between-tools localStorage sync **will not work** in Firefox.

---

## About

When searching a large sphere (3 km radius contract, unknown NPC station, etc.) a naive grid leaves poles over-sampled and midlatitudes thin. φ-Scout uses the **Fibonacci sphere** algorithm — the same geometry nature uses in sunflower seeds — to place *N* waypoints with perfectly uniform angular spacing, then exports them as Space Engineers GPS strings you can paste directly into your HUD.

Two tools ship together:

| File | What it does |
|---|---|
| `phi-scout.html` | Configure & generate waypoints → copy GPS |
| `phi-scout-viz.html` | 3D preview of the spiral on a globe |

Open both in the same browser. They share waypoints automatically via localStorage — generate in φ-Scout and the visualizer updates live.

---

## Quick Tutorial

**1. Open `phi-scout.html` in your browser** (or the hosted GitHub Pages link).

**2. Set your parameters**
- **Center GPS** — paste the contract center point from SE
- **Radius** — search radius in metres (match the contract)
- **Point count** — 24–32 covers most 3 km spheres cleanly
- **Offset** — shift the sphere relative to center if needed
- **Color** — pick a HexColor for the GPS waypoints

**3. Click Generate** — waypoints appear as a GPS block ready to copy.

**4. Paste into Space Engineers**
- Open the GPS menu (`K` by default)
- Paste — all waypoints import at once

**5. Optional: preview in 3D**
- Open `phi-scout-viz.html` in a second tab
- It auto-loads the last generated set (same browser, same origin)
- Use **⟳ φ-Scout Sync** to manually reload, or it updates automatically
- **Left-drag** rotates · **Scroll** zooms · **F** toggles free rotation (no pole-lock)

---

## φ Facts

> *"Nature already solved the packing problem. We just borrowed the answer."*

**φ = 1.6180339887…** (the golden ratio)  
It is irrational — its continued fraction is `[1; 1, 1, 1, …]`, the *slowest-converging* of all irrationals. That's exactly why it spreads points so well: no two steps ever land on the same line.

**The golden angle = 137.507…°**  
Divide a full circle by φ: `360° / φ ≈ 222.5°`. The *short arc* left over is `360° − 222.5° = 137.5°`.  
Rotate each new point by exactly this angle, forever — it never repeats, never clusters.

**Sunflowers, pinecones, nautilus shells, galaxies** all use Fibonacci spirals for the same reason: maximum packing density with zero redundancy.

**In a Fibonacci sphere**, the angular gap between any two nearest-neighbour points converges to the same value as *N* grows. No lat/lon grid can match this — grids always bunch at the poles.

**The formula is three lines:**
```
height(i) = 1 − 2i / (N − 1)          # uniform in z, pole to pole
radius(i) = sqrt(1 − height²)          # circle radius at this height
angle(i)  = i × 137.5°                 # golden angle rotation
```

That's it. φ does the rest.

---

## Files

```
phi-scout.html          Main app
phi-scout-viz.html      3D visualizer (Three.js, no build step)
```

## Disclaimer
Made by AI -- because I'm overworked, and underpaid... ergo -- it is FREE as in BEER.
