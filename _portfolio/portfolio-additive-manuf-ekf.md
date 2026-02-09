---
title: "Online Temperature Prediction for Additive Manufacturing (EKF)"
excerpt: "Physics-informed time-series modeling and state estimation for process monitoring."
collection: portfolio
order: 2
---

### Overview
I developed a physics-informed modeling framework for **fast temperature prediction** in an additive manufacturing process (Additive Friction Stir Deposition), with the goal of supporting real-time monitoring and future control.

This project focused on **state estimation under noisy measurements**, rather than long-horizon forecasting or deployment.

### Data & Setting
- Time-series process data including tool temperature, spindle speed, and torque
- Nonlinear differential governing equations describing temperature evolution
- Measurement noise and regime-dependent dynamics

### Approach
- Formulated a **state-space model** grounded in known process physics
- Implemented an **Extended Kalman Filter (EKF)** to assimilate temperature measurements online
- Evaluated prediction bias, stability, and sensitivity to model parameters
- Explored extensions toward control-oriented formulations

### Outcomes
- Demonstrated improved online temperature tracking relative to open-loop prediction
- Identified regimes where model mismatch dominates measurement noise
- Established a foundation for eventual closed-loop control and uncertainty-aware monitoring

This work strengthened my experience with **time-series modeling**, **state estimation**, and **physics-informed machine learning**, and informs how I approach modeling problems with strong structural constraints.
