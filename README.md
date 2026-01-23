# Digital Twin and Virtual Commisioning: Automated Bottling & Sorting Line
**Integrated Control System using Siemens TIA Portal, NX MCD, and PLCSIM**

## 🚀 Project Overview
This project presents a **two-station bottling assembly line** developed as part of a *Flexible Production Systems* course. It features a complete synchronization between a 3D physics-based simulation in **Siemens NX Mechatronics Concept Designer (MCD)** and industrial control logic running in **TIA Portal**.

The production line handles bottles of **different sizes (tall and short)** and performs filling, capping, sorting, and packing operations using conveyors and ABB industrial robots.

---

## 🎥 System Demonstration

[![Digital Twin Bottling Assembly Line](https://img.youtube.com/vi/aL4MK4sE2Zc/0.jpg)](https://youtu.be/aL4MK4sE2Zc)

▶️ *Click the image to watch the full simulation of the bottling assembly line, including filling, capping, sorting, and packing operations.*


https://github.com/user-attachments/assets/ccd8905e-a6a6-4d93-acb2-e09ce5c52804


## 🛠️ Software and Tools
* **PLC Programming:** TIA Portal (S7-1500 Logic)
* **Virtual Commissioning:** Siemens NX MCD
* **Simulation & Testing:** S7-PLCSIM / PLCSIM Advanced

---

## 🏗️ System Architecture & Stations

### Station 1: Filling & Capping
- **L-shaped conveyor**
- Bottles are introduced from an external source
- Process flow:
  1. Bottle enters the conveyor
  2. Stops at the **filling valve** for a fixed time to simulate filling
  3. Moves toward the **capping robot**

- **Capping Robot**
  - ABB **IRB 920T**
  - Sensors detect bottle height (tall or short)
  - Robot performs the appropriate capping motion based on bottle size

### Station 2: Sorting & Packing
- **T-shaped conveyor layout** with three belts
- Process flow:
  1. Bottle moves along the main belt
  2. Stops at the **sorting robot**

- **Sorting Robot**
  - ABB **IRB 920T**
  - Sensors detect bottle size
  - Robot places bottles onto the corresponding belt based on size

- Bottles are finally transported to **packing boxes**

---

## 🧠 Control Philosophy: Modular Finite State Machines (FSM)
The core of this program is architected using **three distinct Finite State Machines**.

* **Concurrency:** By separating Filling, Capping, and Sorting logic, the system processes multiple bottles simultaneously at different stages.
* **Efficiency:** Instead of tracking a single bottle from start to finish, the PLC manages "zones," allowing the line to run continuously without waiting for a single cycle to complete.

---

## 🕹️ HMI & Interconnectivity
Despite the modularity, the system is unified through a global control layer:
* **Global Controls:** Start, Stop, and Reset commands synchronized across all FSMs.
* **Real-time Monitoring:** Tracking of robot states, belt speeds, and sensor feedback directly from the HMI.
* **Safety & Synchronization:** Hardcoded interlocks ensure that while FSMs operate independently, they respect the physical occupancy of the conveyors to prevent collisions.

---

## 📂 Project Structure
* `/PLC_Program`: TIA Portal project (.zap)
* `/NX_Model`: Siemens NX .prt files, divided into Station 1, Station 2, and COMPLETE (assembly)
* `/Videos`: MP4 version of video demo.

---
