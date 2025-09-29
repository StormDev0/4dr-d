# AGENTS — Fractal Sound Explorer (4D Sonification Project)

## Project Snapshot
- Extended fork of HackerPoet's Fractal Sound Explorer combining fractal rendering with realtime audio.
- Goal: build a playable fractal instrument revealing higher-dimensional structures through synchronized sound and visuals.

## Immediate Objectives
- [done] CPU-side FM synthesis now drives the audio chain with stereo width, delay/feedback, and a soft limiter (see devnotes for parameter mapping).
- Tighten GPU to CPU orbit data flow to keep latency low for realtime audio streaming.
- Extend the new pitch quantization toward configurable scales and rhythmic quantization strategies.
- Package the system as a standalone Fractal Synth Visualizer supporting Mandelbrot, Ikeda, Duffing, and related fractals.

## Audio Workstream
- Treat orbit dynamics as modulation sources for FM operators and multi-voice layering experiments.
- Develop stereo processing that preserves clarity while leveraging chaotic motion for evolving timbres.
- Consider MIDI export pathways so external instruments can mirror orbit behavior.

## Visual Workstream
- Visualize orbits as 3D spirals (Re(z), Im(z), iteration index) with magnitude driving brightness and argument controlling hue.
- Add zoom animations and orbit trails with alpha decay; evaluate VR or AR renderers to strengthen 4D perception.

## Technical Tasks and Considerations
- Monitor the new stereo processors and limiter under stress tests to confirm callback timing remains solid.
- Surface UI bindings for scale/mode selection, delay time, and feedback depth.
- Refactor shaders so orbit data feeds both the renderer and the audio subsystem without redundant passes.
- Investigate multi-threading strategies that keep realtime audio deterministic under heavy visual load.
- Document experiments, benchmarks, and new decisions in devnotes_fractal.md as work progresses.

## Open Questions for Agents
- Clarify whether the primary experience targets realtime performance or offline composition workflows.
- Identify which fractal families yield the richest musical structures for the FM engine.
- Balance visual fidelity with audio responsiveness, especially for higher-dimensional projections.
- Decide whether 4D or 5D projections should be precomputed or generated live.

## Coordination Notes
- Update devnotes_fractal.md with experimental results and keep readme.md aligned with user-facing capabilities.
- When implementing features, attach audio stability tests and visual performance checks to the notes.
- Maintain ASCII-first formatting unless an existing file already uses extended characters.
