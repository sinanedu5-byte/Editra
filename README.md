<p align="center">
  <img src="assets/logo.png" alt="Editra Logo" width="180">
</p>

<h1 align="center">Editra</h1>

<p align="center">
  <b>A powerful, professional image editor running directly in your browser.</b><br>
  Built with pure Rust, compiled to WebAssembly, and rendered with WebGPU &amp; WebGL2.<br>
  Full PSD fidelity, non-destructive layer adjustments, curves, vector paths, brushes, and zero installation required.
</p>

<p align="center">
  <a href="https://sinanedu5-byte.github.io/Editra/"><img alt="Open in Browser" src="https://img.shields.io/badge/Launch-Web%20App-0070f3?style=for-the-badge&logo=googlechrome&logoColor=white"></a>
</p>

<p align="center">
  <img alt="100% Rust" src="https://img.shields.io/badge/100%25-Rust-b7410e?style=flat-square&logo=rust">
  <img alt="WebAssembly" src="https://img.shields.io/badge/WebAssembly-Wasm-654ff0?style=flat-square&logo=webassembly">
  <img alt="WebGPU & WebGL2" src="https://img.shields.io/badge/Graphics-WebGPU%20%2F%20WebGL2-success?style=flat-square">
  <img alt="Runs in Browser" src="https://img.shields.io/badge/Platform-Browser%20(Chrome%20%7C%20Firefox%20%7C%20Safari%20%7C%20Edge)-2f7bf5?style=flat-square">
</p>

<br>

<p align="center">
  <img src="docs/images/photocraft-demo.jpg" alt="Editra workspace demo" width="100%">
  <br>
  <sub>Editra in the browser: non-destructive adjustment layers, live Curves editor, layer effects, and real-time GPU preview.</sub>
</p>

---

## 🌐 Overview

**Editra** brings desktop-grade, Photoshop-level creative editing directly to the web. Unlike traditional web photo editors that rely on heavy JavaScript frameworks or dumbed-down canvas tools, Editra is a comprehensive, layered creative suite written from the ground up in **pure Rust** and executed client-side via **WebAssembly**.

Every stroke, blend mode, and curve adjustment runs locally in your browser with hardware acceleration (WebGPU / WebGL2). Your files never leave your computer, ensuring absolute privacy, zero latency, and true offline capability.

---

## 🚀 Key Features

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>⚡ Hardware-Accelerated Speed</h3>
      GPU-accelerated rendering powered by <code>wgpu</code> (WebGPU with seamless WebGL2 fallback). Smooth panning, zooming, and editing on multi-megapixel canvases.
    </td>
    <td width="33%" valign="top">
      <h3>🎛️ Full Layer Stack</h3>
      Complete layer management: raster layers, group folders, layer masks, clipping masks, opacity control, and 27 ISO blend modes computed in 32-bit floating point precision.
    </td>
    <td width="33%" valign="top">
      <h3>📂 PSD / PSB Compatibility</h3>
      Open and save Adobe Photoshop PSD and PSB files directly in your browser without sacrificing layers, masks, styles, or vector shapes.
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <h3>🎨 Live Adjustments</h3>
      Non-destructive adjustment layers including Curves, Levels, Hue/Saturation, Color Balance, Vibrance, Selective Color, Invert, Threshold, and Gradient Maps.
    </td>
    <td width="33%" valign="top">
      <h3>🖌️ Natural Brushes</h3>
      Full stylus pressure, tilt, smoothing, scattering, dynamic jitter, and compatibility with standard Photoshop <code>.abr</code> brush presets.
    </td>
    <td width="33%" valign="top">
      <h3>📐 Vector & Typography</h3>
      Pen tool, anchor-point path editing, boolean operations, and rich typography support with embedded OpenType fonts.
    </td>
  </tr>
</table>

---

## 🛠️ Running Locally

### Option 1: Development Server with Trunk

To build and serve Editra locally using [Trunk](https://trunkrs.dev/):

1. **Install Prerequisites:**
   ```bash
   # Install Rust (if not already installed)
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

   # Add the WebAssembly compilation target
   rustup target add wasm32-unknown-unknown

   # Install Trunk
   cargo install trunk --locked
   ```

2. **Serve the Web Application:**
   ```bash
   cd apps/photocraft-web
   trunk serve
   ```

3. Open your browser at **`http://127.0.0.1:8765`**.

---

### Option 2: Docker Container

You can also run Editra locally inside an Nginx container with Docker:

```bash
# Build the container image
docker build -t editra-web .

# Run the container
docker run -d --name editra -p 8080:8080 editra-web
```

Open **`http://localhost:8080`** in your browser.

---

## 📦 Architecture

Editra is organized into clean, modular Rust crates:

```text
crates/
  geom cms color raster codecs psd tablet  # L0: Core primitives, geometry, ICC profiles, pixel math
  doc                                      # L1: Document model (layers, masks, styles, adjustments)
  ops paint algo text vector               # L2: History, brush dynamics, imaging algorithms, typography
  compose gpu format                       # L3: Compositor (CPU & wgpu WebGPU/WebGL2), native format
  io plugins                               # L4: PSD & format import/export, sandboxed plugins
  engine                                   # L5: Document session & command registry
  ui-egui automation                       # L6: Modern, data-driven web UI shell
apps/
  photocraft-web                           # WebAssembly application bundle (Trunk + wasm-bindgen)
  photocraft-web-boot                      # Chunked bootloader for static hosting providers
```

---

<p align="center">
  <b>Editra</b> &mdash; Professional image editing, anywhere in the browser.
</p>
