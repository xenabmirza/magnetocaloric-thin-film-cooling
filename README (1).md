# Magnetocaloric Thin-Film Cooling Model

## Overview
This repository contains Python code for modeling magnetocaloric materials, focusing on their potential application for thin-film microchip cooling in high-performance computing and AI data centers.

Traditional air or liquid cooling systems consume large amounts of energy. In data centers, cooling can account for 30–40% of total electricity use. As AI workloads grow exponentially, especially with LLMs and high-throughput inference, cooling efficiency has become a subject of increasing concern for both cost and environmental sustainability.

Magnetocaloric thin films offer an alternative: by exploiting field-induced temperature changes in solid-state materials, we can create on-chip cooling layers that reduce or even replace energy-intensive active cooling.

---

## Physics Background

### Magnetocaloric Effect (MCE)
The magnetocaloric effect is the observed change in temperature of a magnetic material when it is exposed to a changing magnetic field, under adiabatic conditions. It arises from coupling between the material's magnetic order and entropy.

The Maxwell relation for MCE:
$\[
\left( \frac{\partial S}{\partial H} \right)_T = \mu_0 \left( \frac{\partial M}{\partial T} \right)_H
\]$
From this, we derive:
- **Isothermal entropy change**:
$\[
\Delta S_{\text{iso}}(T) = \mu_0 \int_{H_{\min}}^{H_{\max}} \left( \frac{\partial M}{\partial T} \right)_H dH
\]$
- **Adiabatic temperature change**:
$\[
\Delta T_{\text{ad}}(T) = -\frac{T}{C_{\text{vol}}} \, \mu_0 \int_{H_{\min}}^{H_{\max}} \left( \frac{\partial M}{\partial T} \right)_H dH
\]$

### Magnetoelectric Coupling
In a magnetoelectric thin-film stack, electric fields can indirectly modulate magnetic properties via strain coupling, enabling low-power control of the magnetocaloric response, eliminating the need for large magnetic coils. This is especially important for integration on microchips, where footprint and energy input must be minimal.

---

## Why It Matters for AI and Data Centers

- **Energy crisis in AI**:  
  As model sizes and inference volumes grow, cooling overhead is becoming a major cost driver in AI infrastructure.
  
- **Localized cooling**:  
  Thin-film MCE layers could be deposited directly above or below hotspots (e.g., GPU cores, TPUs), reducing the need to chill the *entire chip or server rack.

- **Sustainability**:  
  Magnetic/electric field control consumes orders of magnitude less energy than running large compressor-based HVAC systems.

- **Scalability**:  
  Solid-state cooling has no moving parts, fewer failure points, and can be fabricated in parallel with chip manufacturing.

---

## Features of This Repository

- **Spontaneous magnetization models**:
  - `Ms_powerlaw` for Gd-like (second-order transition).
  - `Ms_sigmoid` for Heusler-like (first-order transition).
  
- **Paramagnetic Curie–Weiss susceptibility**.

- **Full M(T,H) grid calculation** for chosen material type.

- **Numerical derivatives** to get \(\frac{\partial M}{\partial T}\) at constant field.

- **Integration routines** for:
  - Isothermal entropy change (`delta_S_iso`)
  - Adiabatic temperature change (`delta_T_ad`)

- Easily adjustable parameters for **Curie temperature, saturation magnetization, critical exponent, and transition sharpness**.

---

## Installation

```bash
git clone https://github.com/USERNAME/magnetocaloric-thinfilm-cooling.git
cd magnetocaloric-thinfilm-cooling
pip install -r requirements.txt
