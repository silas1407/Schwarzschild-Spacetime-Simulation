# Schwarzschild Spacetime & Relativistic Orbit Simulator

A Python-based computational physics project simulating test particle trajectories, photon spheres, and gravitational lensing around a non-rotating black hole. 

👉 **[Run Live Simulation in Google Colab](https://colab.research.google.com/drive/1Vq_mvDAdXjWmERcFfAgsMCNnCr8QFpFf)**

---

## What It Does
In Newtonian gravity, orbits are stable conic sections. In General Relativity, space warps near massive objects, causing orbital precession and light bending. This project numerically integrates the exact geodesic equations for Schwarzschild spacetime to visualize those relativistic effects.

## Mathematical Model
The simulation solves the coupled ordinary differential equations (ODEs) derived from the Schwarzschild metric (setting c = G = 1):

* **Line Element (ds^2):** -(1 - Rs/r) dt^2 + (1 - Rs/r)^(-1) dr^2 + r^2 (dθ^2 + sin^2(θ) dφ^2)
* **Radial Acceleration (a_r):** -(1/2)*(Rs/r^2) + (L^2/r^3) - (3/2)*(Rs*L^2/r^4) *(Note: The final term is the General Relativistic correction driving orbital precession)*

## Implementation Details
* **Numerical Solver:** Uses SciPy's `solve_ivp` with the adaptive **RK45** method to handle steep gravitational gradients.
* **Singularity Protection:** Includes a custom terminal event function (`stop_at_horizon.terminal = True`) that stops the solver the moment a trajectory crosses the event horizon (r <= Rs) to prevent mathematical overflows.
* **Visualization:** Uses Matplotlib's `FuncAnimation` to render real-time phase portraits of orbital decay and photon capture.

## Running Locally
```bash
git clone [https://github.com/silas1407/Schwarzschild-Spacetime-Simulation.git](https://github.com/silas1407/Schwarzschild-Spacetime-Simulation.git)
cd Schwarzschild-Spacetime-Simulation
python schwarzschild_model.py
