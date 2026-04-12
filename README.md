
<div align="center">

# 🚗 SUMO2Unity: Traffic Co-Simulation Tool

![Contributors](https://img.shields.io/github/contributors/SimuTraffX-Lab/SUMO2Unity?style=for-the-badge&color=blue)
![Forks](https://img.shields.io/github/forks/SimuTraffX-Lab/SUMO2Unity?style=for-the-badge&color=blue)
![Stars](https://img.shields.io/github/stars/SimuTraffX-Lab/SUMO2Unity?style=for-the-badge&color=gold)
![Issues](https://img.shields.io/github/issues/SimuTraffX-Lab/SUMO2Unity?style=for-the-badge&color=red)
![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)

**Bridging microscopic traffic simulation (SUMO) with high-fidelity Virtual Reality rendering (Unity).**



</div>

---

## 📖 Introduction

**SUMO2Unity** is an open-source co-simulation tool created by the **SimuTraffX-Lab** that unifies the mathematical traffic logic of **SUMO** with the 3D rendering power of the **Unity Game Engine**. It imports massive 2D SUMO road networks and procudurally generates them into 3D Unity meshes, maintaining real-time NetMQ synchronization of traffic logic and signal phases.

---

## 📁 Repository Structure

The project is structured to easily separate the 3D rendering environment, the background synchronization tools, and the simulation scenarios.

```text
SUMO2Unity-main/
│
├── 🎮 Assets/             # Unity Game Engine Source Code
│   ├── _Project/          # Core Unity C# scripts (SimulationController, RoadNetworkBuilder, ExchangeData)
│   ├── Scenes/            # Ready-to-play Unity sample scenes
│   └── Settings/          # Unity rendering and input profiles
│
├── ⚙️ RequiredFiles/       # Core Synchronization Utilities
│   ├── Sumo2UnityTool.exe # Custom executable handling NetMQ ZeroMQ socket bridging
│   └── Sumo2UnityTool_combined.py # Python counterpart scripts for networking
│
├── 📊 Results/            # Output Data & Logging
│   ├── FPS_Report.txt     # Framerate performance logs
│   ├── rtf_report.txt     # Real-Time Factor tracking
│   ├── vehicle_data.txt   # Detailed CSV logs of X,Y,Z vehicle coordinates
│   ├── fps2chart/         # Python tools to plot Framerate data
│   └── rtf2chart/         # Python tools to plot Real-Time Factor data
│
├── 🗺️ Scenario1/           # Default Urban Demo Environment
│   ├── Sumo2Unity.net.xml # SUMO Network map geometry
│   ├── Sumo2Unity.sumocfg # SUMO Configuration file
│   ├── Sumo2Unity.rou.xml # Pre-calculated vehicle routes
│   └── Sumo2Unity.Poly.xml# Polygon footprint data for buildings/intersections
│
└── 🗺️ Scenario2/           # Complex Highway/Intersection Environment
    ├── Sumo2Unity.net.xml 
    ├── Sumo2Unity.sumocfg 
    ├── Sumo2Unity.rou.xml 
    └── Sumo2Unity.Poly.xml
```

---

## 🚀 Getting Started

Follow these step-by-step video tutorials to configure the environment:

### Phase 1: SUMO Requirements
▶️ **[Watch SUMO setup tutorial](https://youtu.be/IwsrNWlX9Ag?si=ui75deOeqbreQTf7)**
1. Install [SUMO (Version 1.22)](https://eclipse.dev/sumo/).
2. Set Up `SUMO_HOME` Environment Variables in your Windows OS.
3. Keep `Scenario1` or `Scenario2` folders handy for routing.

### Phase 2: Unity Environment
▶️ **[Watch Unity VR setup tutorial](https://youtu.be/ngccSGH3-_8?si=X1Lx07NUWUqOvJ2f)**
1. Install Unity Hub via the official portal.
2. Install **Unity Editor Version 6000.0.53f1**.
3. Install Visual Studio (along with Unity Game Development workloads).

### Phase 3: Launching Sumo2Unity
▶️ **[Watch Sumo2Unity Quickstart tutorial](https://youtu.be/Cv1wBGuaT0E)**
1. Open this downloaded folder in Unity Hub using version `6000.0.53f1`.
2. Ensure you have activated `Sumo2UnityTool.exe` in the target scenario folder to bridge the socket.
3. Open a sample scene in `Assets/Scenes/`, compile, and hit Play!

---

## 📺 Demos

Sumo2Unity supports **VR and Human-in-the-Loop Simulation**, from driving an ego car to bicycling through dense traffic logically managed by SUMO AI.

*Here are some local video demos of the simulation in action:*

| 🚗 Car POV | 🦅 Birds View |
|:---:|:---:|
| <video src="https://github.com/user-attachments/assets/220236c7-b1b4-46c9-9d6e-89d1d02586a0" controls="controls" width="100%"></video> | <video src="https://github.com/user-attachments/assets/3824c5f9-d305-47c0-b4e4-74edf35dbb93" controls="controls" width="100%"></video> |

---











## ⚙️ Architecture Overview

SUMO and Unity run as completely separate background programs, conversing over an ultra-fast **NetMQ (ZeroMQ)** TCP Socket system (`localhost` ports `5556` and `5557`).

![Flow Architecture Diagram](https://github.com/user-attachments/assets/471cd9d7-f4b7-40db-9b2d-481847c045ef)

* **Traffic Physics Engine (SUMO)**: Generates deterministic AI vehicle data and phase light logic and pushes JSON packets.
* **ExchangeData.cs (Unity)**: A concurrent background thread built into Unity pulling data to avoid frame stuttering.
* **SimulationController.cs (Unity)**: Translates coordinates mathematically to the 3D plane and smooths movement via Lerp interpolation for butter-smooth visual fidelity.

---

## 📜 Citations

If you utilize SUMO2Unity in academic research, please cite our papers to support the project:

> *Mohammadi, A., Park, P. Y., Nourinejad, M., Cherakkatil, M. S. B., & Park, H. S. (2024). SUMO2Unity: An Open-Source Traffic Co-Simulation Tool to Improve Road Safety. In IEEE Intelligent Vehicles Symposium (IV).*

> *Mohammadi, A., Cherakkatil, M. S. B., Park, P. Y., Nourinejad, M., & Asgary, A. (2025). An Open-Source Virtual Reality Traffic Co-Simulation for Enhanced Traffic Safety Assessment. Applied Sciences.*

## ⚖️ License
* **Codebase:** Distributed under the MIT License.
* **Assets:** Distributed under the CC-BY License.
