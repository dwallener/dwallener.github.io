# dwallener.github.io

## Project ARGUS (Attritable Reconnaissance & Global Under-star Surveillance): 
Distributed Causal Inference for Cislunar Custody.

Repo (private): https://github.com/dwallener/argus

## Executive Summary

### The Mission
To eliminate the "Cislunar Gap" by deploying a high-density, low-cost Distributed Tripwire network. We provide persistent anomaly detection and track refinement in deep space and contested terrestrial borders where traditional IR and Radar are economically or physically blinded.

Veto does **not** require high per-node SNR. We utilize high-speed (1 kHz) photometry to extract sub-noise transients, validated via a causal spatiotemporal veto across a shared stellar coordinate system.

### The Problem: The "Exquisite" Failure
Current Space Situational Awareness (SSA) relies on "Exquisite" sensors—billion-dollar telescopes and high-power radars. These systems are:

- Targetable: High-signature active emitters are easily jammed or destroyed.
- Blind: Traditional optics are neutralized by the Moon’s glare or atmospheric noise.
- Sparse: They provide high fidelity on known objects but fail at "discovery" across the 1,700x volume increase of Cislunar space.

The Solution: The Perturbation Mesh
We have developed a "Thin Brain" architecture that treats the universal starscape as a fixed coordinate system for Passive Photometric Monitoring.

- The Primitive: A $200 "Attritable Eye" using high-speed (1 kHz) photometry and intentional optical defocusing to monitor a watchlist of the 500 brightest stellar beacons.
- The Detection: We don't "see" the object; we detect sub-percent photometric perturbations as targets transit the Point Spread Function (PSF) of a known star.
- The Innovation (Causal Validation): Rather than signal-averaging, we employ Spatiotemporal Inference. A single-node "dip" is treated as a candidate event; we only promote it to a "Track" when it is validated by sequential, time-coherent triggers across the distributed mesh that match orbital mechanics.

### The Moat: Statistical Mass & Causal Filtering
Our competitive advantage is not a better lens, but a Deterministic Logic Layer:

- Un-jammable: Completely passive sensing with no RF footprint.
- Mathematically Defensible: Our "Causal Veto" eliminates sensor jitter and cosmic ray artifacts by enforcing strict timing-of-arrival geometry across known baselines.
- Economic Asymmetry: We can seed the entire Cislunar orbit or the Alaskan Arctic for the cost of a single traditional interceptor or destroyer.

### Current Status & Milestones

- Logic: 4-module "Thin Brain" ontology (Saliency/Novelty) is built and sim-proven.
- Validation: Currently prepping for a DevX/AAL field demo in 6 weeks to prove terrestrial "Drone vs. Dog" gating.
- Target: Seeking Techstars/Canopy acceleration to harden the "Star-Blink" mesh for orbital test deployment by Q4 2026.

## Live Lab
### Phase 1: Statistical Inference Sim

### Project Architecture

```mermaid
graph TD
    %% Define Nodes and Styles
    classDef hardware fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
    classDef software fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px;
    classDef logical fill:#fff3e0,stroke:#e65100,stroke-width:2px,stroke-dasharray: 5 5;
    classDef output fill:#fce4ec,stroke:#880e4f,stroke-width:2px;

    %% --- PHYSICAL LAYER (Per Node) ---
    subgraph "Hardware Layer (Per Node)"
        Lens[2cm Defocused Optics]:::hardware
        Sensor[1kHz Photometric Sensor]:::hardware
        Clock[GNSS-Disciplined Oscillator <1ms Sync]:::hardware
    end

    Lens -->|PSF Photons| Sensor
    Sensor -->|Raw 1kHz Stream| NodeInference

    %% --- INFERENCE LAYER (Per Node "Thin Brain") ---
    subgraph NodeInference ["Inference Layer (Per Node 'Thin Brain')"]
        direction TB
        Catalog[Bright Star Watchlist (Top 500)]:::logical
        NoiseFilter[Statistical Anomaly Detector (Change Detection)]:::software
        EventLogger[Candidate Event Logger (Timestamp + Star ID)]:::software
        
        Catalog -.-> NoiseFilter
        NoiseFilter -->|Sub-Noise Transient| EventLogger
        Clock -.-> EventLogger
    end

    %% --- MESH & VALIDATION LAYER ---
    subgraph MeshValidation ["Mesh & Validation Layer (Consensus)"]
        direction TB
        MeshComms[Mesh Communication Layer]:::software
        CausalVeto[Causal Spatiotemporal Veto (Hypothesis Testing)]:::software
        TrajRecon[Trajectory Reconstruction Engine]:::software
        
        MeshComms -->|Time-Aligned Events| CausalVeto
        CausalVeto -->|Vetted Sequence| TrajRecon
    end

    EventLogger -->|Candidate Event (UDP/CoT)| MeshComms

    %% --- OUTPUT LAYER ---
    subgraph OutputLayer ["Output Layer"]
        direction TB
        SAPIENT[SAPIENT/CoT Formatter]:::software
        API[Target Vector API]:::output
    end

    TrajRecon -->|Validated Path| SAPIENT
    SAPIENT --> API

    %% --- NOTES (Optional but Helpful for Pitch) ---
    %% Note1[Note: Individual Nodes log 'Candidate Events' that are below single-node detection thresholds]
    %% Note2[Note: Causal Veto validates the 'tripwire' sequence matches orbital physics]
```

Demo video:
<tbd>

Field Testing: June 2026
Hardware Sprint: In progress
