# Gravity · n-body simulation

## Physics

Newtonian gravity — force between two bodies:
```
F = G · m₁ · m₂ / r²
```

where `G ≈ 6.674 × 10⁻¹¹ N·m²·kg⁻²`

---

## How to use

Click and drag on the canvas to spawn a new body. Drag direction and length set the initial velocity vector.

| Control | Description |
|---|---|
| **M** | Mass of the next body. Use the planet presets or the slider. |
| **S** | Trail length drawn behind each body. |
| **F** | Fix — locks the most massive body to the center of the screen. |
| **St** | Stick — camera follows the main body as it moves. |
| **▶ ▶▶ ▶▶▶** | Time speed — slow, normal, fast. |
| **⏸** | Pause / resume. |
| **↺** | Restart — clears all bodies and resets the view. |

---

## Known issues & resolutions

### Zero-distance singularity
When `r → 0`, gravitational force diverges to infinity, causing bodies to reach arbitrarily large velocities. A softening parameter ε sets a minimum effective distance:
```
F = G · m₁ · m₂ / (r² + ε²)
```

This prevented the singularity but introduced the issue below.
**Status: resolved via body collision detection.**

### ε-induced perihelion precession
By capping the effective distance, ε systematically underestimates the gravitational force at close range. The resulting error accumulates orbit after orbit, producing an artificial perihelion drift far larger than any physical effect.

Removing ε eliminated the drift but reintroduced the singularity — both issues resolved together via collision.

---

## Roadmap

- [ ] Distance metric overlay
- [ ] Mass metric overlay
- [ ] Force metric overlay
- [ ] Gravitational field mesh

## Forward ideas

- Cursor-following attractor mode
- Random-spawning / procedural system generator