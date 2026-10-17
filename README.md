<p align="center">
  <img src="assets/logo.png" alt="Editra Logo" width="180">
</p>

<h1 align="center">Editra</h1>

<p align="center">
  <b>A powerful, high-performance, native image editor written in pure Rust.</b><br>
  Professional layers, masks, curves, non-destructive adjustments, vector shapes, type, brushes, and real PSD fidelity.<br>
  Fast, modern, offline-first, and yours.
</p>

<p align="center">
  <img alt="100% Rust" src="https://img.shields.io/badge/100%25-Rust-b7410e?style=flat-square&logo=rust">
  <img alt="macOS · Windows · Linux · Web" src="https://img.shields.io/badge/macOS%20%C2%B7%20Windows%20%C2%B7%20Linux%20%C2%B7%20Web-native-2f7bf5?style=flat-square">
  <img alt="GPU Accelerated" src="https://img.shields.io/badge/GPU-wgpu%20accelerated-success?style=flat-square">
  <img alt="Status: Active" src="https://img.shields.io/badge/status-active-brightgreen?style=flat-square">
</p>

<br>

<p align="center">
  <img src="docs/images/photocraft-demo.jpg" alt="Editra workspace demo" width="100%">
  <br>
  <sub>Editra in action: non-destructive adjustment layers, live Curves editor, layer effects, and real-time GPU preview.</sub>
</p>

---

## Overview

**Editra** is an open-source, native creative suite for digital artists, designers, and photographers. Built entirely in Rust without webview wrappers or Electron overhead, Editra pairs desktop-grade responsiveness with industrial-strength image editing capabilities.

Whether you're retouching high-resolution photographs, compositing complex multi-layered artwork, or designing graphics with vector tools and typography, Editra delivers a familiar, dependable experience with zero lag.

---

## Key Features

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>⚡ Native & High-Performance</h3>
      A pure Rust engine powered by <code>wgpu</code> (DirectX 12, Vulkan, Metal, WebGPU). Features copy-on-write tile caching, multithreaded filters (Rayon), and instantaneous viewport updates on multi-megapixel canvases.
    </td>
    <td width="33%" valign="top">
      <h3>🎛️ Familiar & Intuitive UI</h3>
      Designed with standard creative tool conventions in mind. Access familiar layer panels, adjustment stacks, layer masks, channels, history undo states, and keyboard shortcuts right at your fingertips.
    </td>
    <td width="33%" valign="top">
      <h3>📂 PSD / PSB Compatibility</h3>
      Import and export Adobe Photoshop PSD and PSB files with full fidelity: preserving layer hierarchies, masks, blend modes, vector shapes, text blocks, and layer styles.
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <h3>🎨 Non-Destructive Editing</h3>
      Complete suite of live adjustments: Curves, Levels, Hue & Saturation, Color Balance, Vibrance, Selective Color, Invert, Threshold, Posterize, and Gradient Maps.
    </td>
    <td width="33%" valign="top">
      <h3>🖌️ Natural Paint & Brushes</h3>
      Full stylus pressure and tilt support with customizable brush dynamics (jitter, scattering, size/opacity taper), hardness control, and compatibility with standard <code>.abr</code> brush presets.
    </td>
    <td width="33%" valign="top">
      <h3>📐 Vector & Typography</h3>
      Pen tool, paths, anchor-point editing, boolean path operations, and rich typography engine supporting system and embedded fonts with tracking and leading controls.
    </td>
  </tr>
</table>

---

## Everything in the Box

- **Layer Engine:** Raster layers, adjustment layers, shape layers, type layers, group folders, and smart objects.
- **Blending Modes:** 27 standard ISO blend modes computed in precise 32-bit floating point and linear color spaces.
- **Selection Tools:** Rectangular/elliptical marquees, lasso, polygonal lasso, magnetic selection, magic wand, quick selection, color range picker, and feathering/smoothing algorithms.
- **Retouching Tools:** Clone stamp, healing brush, spot healing, dodge, burn, sponge, blur, sharpen, and smudge.
- **Color Management:** Built-in ICC profile transformations, sRGB, Display P3, Adobe RGB, ProPhoto, CMYK, and Lab color spaces.
- **Automation & CLI:** Headless CLI mode for batch automation, image conversions, scriptable command registries, and JSON control protocol.

---

## Getting Started

### Prerequisites

You need a working Rust toolchain (edition 2024 / recent stable). If you don't have Rust installed, set it up via [rustup.rs](https://rustup.rs/):

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### Building & Running

Clone the repository and launch Editra locally:

```bash
# Clone the repository
git clone https://github.com/sinanedu5-byte/Editra.git
cd Editra

# Run the native desktop application
cargo run -p photocraft --release
```

### Running the Headless CLI

Editra includes a full headless CLI for automated conversions and batch processing:

```bash
# Run the CLI tool
cargo run -p photocraft-cli -- --help
```

---

## Workspace Architecture

Editra is architected into layered, modular Rust crates:

```text
crates/
  geom cms color raster codecs psd tablet  # L0: Core primitives, geometry, ICC profiles, pixel math
  doc                                      # L1: Document model (layers, masks, styles, adjustments)
  ops paint algo text vector               # L2: History, brush dynamics, imaging algorithms, type
  compose gpu format                       # L3: Compositor (CPU & wgpu GPU), native file format
  io plugins                               # L4: PSD & format import/export, sandboxed plugins
  engine                                   # L5: Document session & command dispatch
  ui-egui automation                       # L6: Native UI shell & automation protocol
apps/
  photocraft                               # Native desktop GUI binary
  photocraft-cli                           # Headless command-line tool
  photocraft-web                           # WebAssembly browser client
```

---

<p align="center">
  <b>Editra</b> &mdash; Built with passion in pure Rust.
</p>
