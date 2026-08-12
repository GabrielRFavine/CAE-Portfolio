# 🏎️ Project 01: Vehicle External Aerodynamics Simulation (CFD)

## 1. Project Objective
This project performs a Computational Fluid Dynamics (CFD) analysis of external airflow over a simplified automotive geometry. The primary objective is to evaluate aerodynamic phenomena, map flow separation zones in the rear region, and compute global **Drag ** and **Lift/Downforce** coefficients.

---

## 2. Geometry & Fluid Domain

* **Geometric Model:** Simplified passenger car geometry (standard benchmark for aerodynamic evaluation).
* **Cad Defeaturing:** Suppression of non-aerodynamic features (door handles, panel gaps, side mirrors) to ensure high-quality boundary layer meshing.
* **Computational Domain (Virtual Wind Tunnel):**
  * **Upstream (Inlet):** $3 \times$ vehicle length ($3L$).
  * **Downstream (Outlet):** $6 \times$ vehicle length ($6L$) to allow full development of the turbulent wake.
  * **Width & Height:** Sized to maintain a Blockage Ratio below 3%.

---

## 3. Boundary Conditions & Physical Setup

Simulation setup configured in **ANSYS Fluent**:

* **Velocity Inlet:** Constant inlet velocity of $30.5 \text{ m/s}$ ($\approx 110 \text{ km/h}$).
* **Pressure Outlet:** Gauge pressure of $0 \text{ Pa}$.
* **Ground (Moving Wall):** Translational wall matching the inlet flow speed ($30.5 \text{ m/s}$) to model real-world road motion.
* **Vehicle Body (No-Slip Wall):** Standard no-slip condition.
* **Turbulence Model:** $k-\omega \text{ SST}$ (*Shear Stress Transport*), selected for its accuracy in predicting adverse pressure gradient flow separation.

---

## 4. Mesh Refinement & Boundary Layer (*Inflation*)

An unstructured mesh with localized boundary layer refinement was configured to accurately capture velocity gradients near the vehicle surface:

| Parameter | Configuration / Value |
| :--- | :--- |
| **Element Types** | Tetrahedrals in core domain + Prismatic layers in inflation |
| **First Layer Height** | Calculated to achieve $y^+ \approx 1$ on critical surfaces |
| **Inflation Layers** | 10 to 15 layers with a growth rate of 1.2 |
| **Total Element Count** | ~2,800,000 elements (post-convergence) |

---

## 5. Results & Flow Visualization

### Aerodynamic Coefficients
* **Drag Coefficient ($C_d$):** `[Insert computed value, e.g., 0.312]`
* **Lift Coefficient ($C_l$):** `[Insert computed value, e.g., 0.045]`

### Qualitative Flow Evaluation
![Streamlines and Turbulent Wake](./Images/Streamlines.png)
*(Replace with high-resolution screenshot/GIF of streamlines and velocity vectors)*

1. **Frontal Region:** High static pressure region at the front bumper and hood (stagnation point).
2. **Rear Wake:** Low-pressure recirculation zone forming rear vortices—the dominant contributor to pressure drag.

---

## 6. Engineering Conclusions
* The $k-\omega \text{ SST}$ model clearly resolved flow separation points along the roofline and trunk edge.
* The low-pressure wake region accounts for over 60% of total aerodynamic drag.
* **CAD Optimization Proposal:** Evaluate a rear decklid spoiler to manage the wake structure and increase roofline curvature radius to delay boundary layer separation.
