# **Bolt-3D — AI-Native Physics Engine in Your Browser**

*"The Unity Killer, In Your Browser"*

---

## 🚀 Overview

**Bolt-3D** is an **AI-powered, browser-native game engine** for building **high-quality 3D worlds** and **physics simulations** — instantly, from a prompt.
It repurposes [Bolt.new](https://github.com/stackblitz/bolt.new) from website generation to **real-time Three.js world generation**, integrating:

* **Needle Progressive GLTF** for streaming environments & characters from the cloud
* **Dynamic Physics Engine Switching** — from lightweight (Cannon) to heavyweight (Rapier, Havok, PhysX WASM) for fidelity control
* **VRoid / GLTF Avatar Support** with rigging, retargeting, ragdoll physics, and third-person controllers
* **Action-based AI World Builder** that can spawn, edit, and reconfigure a scene in seconds

---

## 🛑 The Problem

Unity and Unreal are heavy, bloated, and locked to native installs. Their physics layers are either outdated (Unity/PhysX) or require expert setup (Unreal).
On the web, developers are stuck with **basic toy physics** or have to write thousands of lines of boilerplate just to stand up a scene.
Sharing interactive worlds is slow and painful.

---

## 💡 The Solution

A **Figma for physics and simulation**:

* Runs entirely in-browser (WebContainers) — no native binaries, no install
* Streams **optimized 3D assets** on demand from Needle Cloud
* Dynamically swaps physics engines for **performance vs. fidelity** without changing code
* Lets you create, modify, and share high-quality worlds **from natural language prompts**

---

## 🎥 Demo

> “Create a Fortnite-style island with a VRoid character in a white robe, ragdoll physics enabled, realistic lighting, and a stack of boxes I can knock over.”

In seconds, Bolt-3D:

1. Spawns the environment streamed from Needle
2. Loads the chosen character from the catalog
3. Configures physics engine + ragdoll setup
4. Drops the props with full rigid-body interaction
5. Gives you a playable TPS controller and sharable link

---

## ⚙️ Features

* **AI World Builder** — Action-based schema for dynamic scene generation (`worldPhysics`, `worldCreate`, `worldLoad`, `worldCharacter`, etc.)
* **Dynamic Physics Switching** — `cannon-es` fallback, Rapier WASM stub, future Havok/PhysX support
* **Cloud Asset Streaming** — Needle progressive GLTF for low-latency large scenes
* **VRoid-Ready Characters** — Fully rigged, controller-ready, with ragdoll toggle
* **Modular Engine Design** — Adapter pattern for physics, loaders, navigation
* **Zero Install** — Built on WebContainers; runs in your browser

---

## 📂 Repo Structure

```
src/
  agent/
    bolt/                  # Action parser, executor, and runtime hook
    catalog/characters.json# Character registry (id, description, tags, src)
  engine/
    render/                 # Three.js/R3F renderer, scene, loaders
    physics/                # Engine API + adapters
    character/              # Controllers, ragdoll builder, retargeting
    navigation/              # Navmesh loader and agent movement
  scenes/
    demoScene.tsx           # Starter scene
  ui/
    debugPanel.tsx          # Physics toggle, collider debug, perf HUD
```

---

## 🛠️ Getting Started

### 1. Install

```bash
npm install
```

### 2. Run Dev Server

```bash
npm run dev
```

Your scene will open automatically in the browser.

### 3. Try the Demo

Use the built-in AI prompt to run:

```
Create a sunny island with a character from characters.json#nana, ragdoll disabled, 20 falling boxes, and a directional light.
```

---

## 🧩 Action Schema

Bolt-3D uses `<boltAction>` tags to describe world edits.

Example:

```xml
<boltAction type="worldPhysics">
  { "engine": "cannon", "gravity": [0,-9.81,0] }
</boltAction>

<boltAction type="worldCharacter">
  {
    "id": "hero",
    "type": "player",
    "src": "characters.json#nana",
    "controller": "tps-basic",
    "ragdoll": false
  }
</boltAction>
```

---

## 🗺 Roadmap

* [ ] Multiplayer state sync
* [ ] Advanced navmesh crowd simulation
* [ ] Physics material editor in debug panel
* [ ] Expanded asset catalog with semantic search
* [ ] VRM live avatar streaming + animation blending

---

## 🤝 Contributing

1. Fork the repo
2. Create a feature branch
3. Submit a PR with a detailed description

---

## 📜 License

MIT © 2025 QEM Labs


---

## 🙏 Acknowledgments

This project is built on top of the open-source [Bolt.new](https://github.com/stackblitz/bolt.new) framework, extending its AI-powered code generation capabilities to create immersive 3D worlds and physics simulations.
