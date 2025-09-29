# Developer Notes — Fractal Sound Explorer (4D Sonification Project)

This file captures **implementation details, experiments, and technical decisions** for the extended fork of HackerPoet’s **Fractal Sound Explorer**.

---

## 🛠 Core Modifications
- Extend orbit→sound mapping beyond simple stereo:
  - Add **FM synthesis** engine.
  - Stereo width control.
  - Delay/feedback loop.
  - Soft limiter for output.
- GPU → CPU pipeline adjustments:
  - Ensure **low-latency orbit data transfer** for realtime sonification.
  - Optimize shader output for both visual and audio usage.

---

## 🎶 Audio Design Notes
- Orbit dynamics as **oscillator modulation sources**.
- Map periodicity → pitch quantization (musical scales).
- Chaotic behavior → timbral textures.
- Possible extensions:
  - Multi-voice layering (several orbit points simultaneously).
  - MIDI export for external synth control.
  - Rhythmic quantization of orbit returns.

---

## 🎨 Visual Design Notes
- 3D spiral embedding: `(Re(z), Im(z), iteration index)`.
- Orbit magnitude → brightness.
- Orbit angle (arg) → hue.
- Goal: reinforce perception of **4D structures** via color+motion.
- Potential enhancements:
  - Zoom animations synchronized with audio.
  - Overlay orbit trails with alpha decay.
  - VR/AR rendering for immersive higher-dimensional effect.

---

## 🚧 Technical TODOs
- [x] Integrate FM oscillator module (CPU side).
- [x] Implement stereo width + delay feedback processor.
- [x] Add limiter to audio output chain.
- [ ] Refactor shader code for orbit export.
- [x] Build orbit→pitch quantization system (major scale prototype; add scale/mode selection next).
- [ ] Explore multi-threading for audio callback stability.

---

## ✅ Implementation Snapshot
- CPU FM voice derives carrier, modulator, and modulation index directly from orbit magnitude, velocity, and angle.
- Stereo width now reacts to orbit angle while a feedback delay ring buffer adds temporal space; both channels share a soft limiter via `tanh` saturation.
- Pitch output is quantized to a diatonic major scale; configuration hooks are ready for future mode/scale selection work.
- Added smoothing for all target parameters to keep the audio callback stable even under chaotic orbit motion.

---

## 💡 Open Questions
- Should fractal exploration be **real-time interactive instrument** or **offline composition tool**?
- Which fractals provide the richest musical structures? (Mandelbrot vs Ikeda vs Duffing)
- How to balance **visual fidelity** with **audio responsiveness**?
- Should higher-dimensional projections (4D/5D) be precomputed or live-simulated?

---

## 📚 References
- HackerPoet’s original [Fractal Sound Explorer](https://github.com/HackerPoet/FractalSoundExplorer).
- CodeParade’s Itch.io release.
- Research: Orbit→Melody mapping, FM synthesis design, visual perception of fractals.

---

> Add experiment results, benchmarks, and new design choices here as development evolves.
