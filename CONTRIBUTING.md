# Contributing to Propagation

Thanks for your interest! This project welcomes small changes and bug reports.

## How to Contribute

1. **File an issue** describing the problem or feature you want
2. **Fork the repository** and create a branch named `fix/something` or `feature/something`
3. **Open a pull request** with a clear description of the change

## Guidelines

- Keep changes small and focused — one logical change per PR
- Include screenshots or short recordings for UI/visual changes
- If changing simulation constants or rendering behavior, explain why and include before/after images or performance impact

## Development Setup

```bash
git clone https://github.com/balbaks/propagation.git
cd propagation
python3 -m http.server 8000
Open http://localhost:8000 in a browser. Edit propagation.html and refresh.

No build tools, dependencies, or bundlers required — the demo pulls Three.js from CDN.

Code Overview
propagation.html — single-file demo containing all HTML, CSS, and JS

Simulation constants are near the top of the script block (search for let SIGNAL_SPEED)

The buildGraph() function handles node/edge creation and teardown

updateSignals(), updateNodes(), and updateEdgeWeights() run each frame

The control panel bindings are near the bottom of the script

Ideas for Contributions
Record a GIF demo for the README

Touch/gesture support for mobile devices

Export/import network topology

Color theme presets

Spatial audio on signal events

VR mode via WebXR

Performance profiling and optimization

Questions?
Open an issue or contact the maintainer: @balbaks