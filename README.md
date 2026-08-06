# Propagation — Node Network demo

Polished interactive WebGL demo of a large node/signal network built with three.js. This single-file demo (propagation.html) shows neuron-like firing, Hebbian plasticity, and a tunable signal propagation system with performance-minded instanced rendering.

Live demo

- Once GitHub Pages is enabled for this repository (See *Publishing* below), the demo will be available at: https://balbaks.github.io/propagation/

Quick description

- Single-file interactive demo: propagation.html
- Controls: sliders for node count, signal speed/strength, threshold, decay, plasticity; transport buttons (pause/reset/burst); click/spacebar injections; cinematic mode.
- Built for spectacle and performance: instanced meshes, spatial bucketing for neighbor computation, bloom/postprocessing.

How to run locally

Option A — quick (open file)
1. Open propagation.html in a modern browser (Chrome/Edge/Firefox). For best results use a browser that supports ES modules and WebGL2.

Option B — serve via a tiny static server (recommended to avoid CORS CDN / import map issues)

1. From the repo root:

   ```sh
   python3 -m http.server 8000
   # or
   npx http-server -p 8000
   ```
2. Open http://localhost:8000/propagation.html or http://localhost:8000/

Controls summary

- Space: inject a random signal
- Click: inject a click at the nearest node
- Cinematic Mode (C or button): hide UI + slow rotation for recordings
- Sliders: Node count (rebuilds graph), Signal speed/strength, Base threshold, Decay rate, Refractory time, Plasticity learn rate/decay

Dependencies

- three.js (imported from unpkg in the file's import map). The demo intentionally avoids a bundler — it's a single ES-module HTML file that pulls three and its addons from CDN.

Contributing

See CONTRIBUTING.md for how to report issues or propose changes.

License

This repository is licensed under the MIT License — see LICENSE.

Credits

- three.js authors and contributors

Notes

- The demo is intentionally single-file so it can be dropped into any static host quickly. If you want a packaged npm/rollup build or an embeddable module, open an issue or submit a PR.
