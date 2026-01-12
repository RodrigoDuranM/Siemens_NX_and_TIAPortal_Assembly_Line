# Digital Twin: Automated Bottling & Sorting Line
**Integrated Control System using Siemens TIA Portal, NX MCD, and PLCSIM**

## 🚀 Project Overview
This project is a high-fidelity "Digital Twin" of a streamlined factory bottling line. It features a complete synchronization between a 3D physics-based simulation in **Siemens NX Mechatronics Concept Designer (MCD)** and industrial control logic running in **TIA Portal**.

The system automates the lifecycle of a bottle—from initial filling and capping to intelligent sorting via robotic arms based on package dimensions.

---

## 🛠️ Technology Stack
* **PLC Programming:** TIA Portal (S7-1500 Logic)
* **Virtual Commissioning:** Siemens NX MCD
* **Simulation & Testing:** S7-PLCSIM / PLCSIM Advanced
* **HMI:** Integrated control interface for Start/Stop/Reset and real-time monitoring.

---

## 🏗️ System Architecture & Stations

### Station 1: Filling & Capping
* **Process:** Bottles are introduced via HMI trigger, conveyed to a filling valve, and held using precise timing logic.
* **Robotic Integration:** An **ABB Robot 1** handles the capping sequence once the bottle enters its workspace, ensuring the mechanical assembly is ready for the sorting stage.

### Station 2: Sorting & Packing
* **Process:** Intelligent sorting based on bottle dimensions.
* **Vision/Sensing:** **ABB Robot 2** identifies the bottle size and, directed by the PLC, diverts it to the correct secondary conveyor.
* **End-of-Line:** Bottles are routed to specific packing crates, completing the production cycle.

---

## 🧠 Control Philosophy: Modular Finite State Machines (FSM)
The core of this program is architected using **three distinct Finite State Machines**. 

> **Engineering Insight:** A modular FSM approach was chosen over a single linear sequence to maximize throughput. 
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
* `/PLC_Program`: TIA Portal project archives (.zap) and SCL source code.
* `/NX_Model`: Siemens NX .prt files and MCD physics configurations.
* `/Documentation`: I/O mapping, state diagrams, and PDF exports of the logic.
* `/Media`: Screen recordings and screenshots of the simulation in action.

---
