<div align="center">

# Propagation

**An interactive 3D neural signal network built with Three.js**

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen?style=for-the-badge&logo=github)](https://balbaks.github.io/propagation/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)](LICENSE)
[![Three.js](https://img.shields.io/badge/Three.js-r160-black?style=for-the-badge&logo=threedotjs)](https://threejs.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](CONTRIBUTING.md)

<br>

![Propagation Demo](assets/screenshot.svg)

*Watch thousands of luminous nodes fire cascading signals through a self-organizing neural network — rendered in real-time 3D with bloom post-processing.*

**[Launch Demo](https://balbaks.github.io/propagation/)** | **[Repository](https://github.com/balbaks/propagation)**

</div>

---

## Features

- **Neuron Dynamics** — Leaky integrate-and-fire model with configurable threshold, decay, and refractory periods
- **Signal Propagation** — Cascading signals travel along edges with visible comet-trail particles
- **Hebbian Plasticity** — Frequently used connections strengthen; idle ones decay — visible pathway emergence
- **Live Controls** — On-screen sliders for node count, signal speed/strength, threshold, decay, learning rate
- **Interactive Input** — Click to inject charge, spacebar for random bursts, orbit/zoom with mouse
- **Stats Overlay** — Real-time firing rate, active signal count, and activated node count
- **Cinematic Mode** — Hide UI + auto-drift camera for clean recordings (press C)
- **Single-File** — Zero dependencies beyond Three.js CDN — open propagation.html and go

---

## Performance

- **Instanced meshes** — all 3,000+ nodes and signals rendered in single draw calls
- **Spatial bucketing** — neighbor computation uses a uniform grid instead of O(n²)
- **Typed arrays** — all neuron state stored in Float32Array for cache-friendly access
- **60fps target** — tested smooth at 5,000 nodes on integrated graphics

---

## Controls Reference

### Simulation Parameters

| Slider | Range | Default | What It Does |
|--------|-------|---------|--------------|
| Node count | 500-5000 | 3000 | Rebuilds entire graph on release |
| Signal speed | 0.2-5.0 | 1.5 | Travel speed along edges |
| Signal strength | 0.1-1.5 | 0.6 | Charge deposited per arrival |
| Base threshold | 0.5-2.5 | 1.0 | Activation needed to fire |
| Decay rate | 0.1-3.0 | 1.1 | How fast charge leaks away |
| Refractory time | 0.1-1.5 | 0.5 | Seconds before node can re-fire |

### Plasticity Parameters

| Slider | Range | Default | What It Does |
|--------|-------|---------|--------------|
| Learn rate | 0-0.2 | 0.04 | Weight gain when edge contributes to a fire |
| Decay / sec | 0-0.5 | 0.02 | Weight loss per second for all edges |

### Keyboard and Mouse

| Input | Action |
|-------|--------|
| Click | Inject charge into nearest node |
| Spacebar | Spawn random signal |
| C | Toggle cinematic mode |
| Mouse drag | Orbit camera |
| Mouse wheel | Zoom in/out |
| Right drag | Pan |

---

## Getting Started

```bash
git clone https://github.com/balbaks/propagation.git
cd propagation
python3 -m http.server 8000
```

Then visit `http://localhost:8000`

**Requirements:** Modern browser with WebGL 2.0 support. Internet connection for Three.js CDN. No build step or dependencies required.

---

## How It Works

The simulation uses a **leaky integrate-and-fire** neuron model. Each node accumulates charge from incoming signals and fires when it crosses a threshold, spawning new signals to its neighbors.

The edge network is built via spatial k-nearest-neighbors (k=3-4) within a spherical volume of radius 16.

**Hebbian plasticity:** Edge weights increase when they contribute to a postsynaptic fire, and decay slowly when idle. This causes well-used pathways to visibly strengthen while unused ones fade.

**Stability:** The model has a sharp critical point — small parameter changes can push it from "calm with occasional waves" to "permanently saturated." Defaults are tuned via soak tests.

---

## Project Structure

```text
propagation.html      — Main demo (self-contained)
index.html            — Landing page
README.md
LICENSE               — MIT
CONTRIBUTING.md
package.json
.gitignore
.nojekyll
assets/
  screenshot.svg
.github/workflows/
  pages.yml           — Auto-deploy to GitHub Pages
```

---

## Tuning Tips

- Set node count to 2000-3000 for a dense starfield
- Keep signal strength at 0.55-0.65 (higher causes runaway saturation)
- Keep threshold at 1.0-1.2 (provides margin against convergent summation)
- Enable plasticity and watch pathways emerge over 30-60 seconds
- Toggle cinematic mode (C) for clean recordings

---

## Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md). Open areas:

- Record and add a GIF demo
- Touch/gesture support for mobile
- Export/import network topology
- Color theme presets
- VR mode (WebXR)

---

## License

MIT — see [LICENSE](LICENSE) for details.

---

<div align="center">

Built with [Three.js](https://threejs.org/) — Inspired by neural dynamics and graph visualization

</div>