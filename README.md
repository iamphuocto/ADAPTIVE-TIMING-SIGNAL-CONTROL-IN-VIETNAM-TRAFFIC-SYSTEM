# Adaptive Timing Signal Control in the Vietnam Traffic System

An intelligent, real-time traffic management system that dynamically adjusts green light durations based on traffic density and heterogeneous vehicle composition. By integrating computer vision (YOLOv8 & ByteTrack) with a localized traffic flow optimization algorithm, this system effectively mitigates urban congestion and reduces vehicle delay in high-density environments.

---

## Key Features

**Real-Time Object Detection & Tracking:** Utilizes **YOLOv8** optimized for object detection combined with **ByteTrack** and **Supervision** for robust multi-vehicle tracking, counting, and classification.
***Localized PCU Metrics:** Implements a custom Passenger Car Unit (PCU) calculation tailored directly to Vietnamese urban traffic behavior, rather than standard international formulas.
* **Occlusion & Density Mitigation:** Designed with specialized camera calibration metrics (8m height, 200m distance) to handle high-density visual challenges and extreme vehicle occlusion.
* **Hardware Integration Ready:** Communication protocol configured via **Modbus TCP** to seamlessly sync vehicle metrics with industrial **SCADA/PLC** systems for field deployment.
*  **SUMO Simulation:** Fully integrated with **SUMO (Simulation of Urban Mobility)** and **TraCI** to run dynamic traffic simulations, test edge cases, and calibrate the adaptive threshold coefficient ($k$).

---

## 📊 Dataset: UIT-VinaDeveS22

The model is trained and validated on the **UIT-VinaDeveS22** benchmark dataset, reflecting real-world Vietnamese street conditions under various weather scenarios and diverse densities.

### [cite_start]Data Distribution 
| Set | Number of Images | Number of Objects |
| :--- | :---: | :---: |
| Training | 653 | 7,724 |
| Validation | 173 | 1,765 |
| Test | 538 | 5,929 |
| **Total** | **1,364** | **15,418** |

### [cite_start]Class Appearances 
* [cite_start]**Motorbike:** 9,458 (Dominant mode of transport) 
* [cite_start]**Car:** 3,967
* [cite_start]**Van / Truck / Bus / Bicycle / Fire truck:** 2,003 
---

## 🛠️ System Architecture & Workflow

[cite_start]The adaptive control logic operates across three integrated layers[cite: 139]:
