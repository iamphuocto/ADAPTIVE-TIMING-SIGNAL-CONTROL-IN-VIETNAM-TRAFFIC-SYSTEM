# Adaptive Timing Signal Control in Vietnam Traffic System

An intelligent, real-time traffic management system that dynamically adjusts green light durations based on traffic density and heterogeneous vehicle composition. [cite_start]By integrating computer vision (YOLOv8 & ByteTrack) with a localized traffic flow optimization algorithm, this system effectively mitigates urban congestion and reduces vehicle delay in high-density environments[cite: 16, 17, 18, 141, 147].

---

## 🚀 Key Features

* [cite_start]**Real-Time Object Detection & Tracking:** Utilizes **YOLOv8** optimized for object detection combined with **ByteTrack** and **Supervision** for robust multi-vehicle tracking, counting, and classification[cite: 17, 139, 141, 143].
* [cite_start]**Localized PCU Metrics:** Implements a custom Passenger Car Unit (PCU) calculation tailored directly to Vietnamese urban traffic behavior, rather than standard international formulas[cite: 18, 107, 108].
* [cite_start]**Occlusion & Density Mitigation:** Designed with specialized camera calibration metrics (8m height, 200m distance) to handle high-density visual challenges and extreme vehicle occlusion[cite: 145, 147].
* [cite_start]**Hardware Integration Ready:** Communication protocol configured via **Modbus TCP** to seamlessly sync vehicle metrics with industrial **SCADA/PLC** systems for field deployment[cite: 160, 163].
* [cite_start]**SUMO Simulation:** Fully integrated with **SUMO (Simulation of Urban Mobility)** and **TraCI** to run dynamic traffic simulations, test edge cases, and calibrate the adaptive threshold coefficient ($k$)[cite: 60, 132, 192].

---

## 📊 Dataset: UIT-VinaDeveS22

[cite_start]The model is trained and validated on the **UIT-VinaDeveS22** benchmark dataset, reflecting real-world Vietnamese street conditions under various weather scenarios and diverse densities[cite: 19, 82, 86, 87].

### [cite_start]Data Distribution [cite: 100]
| Set | Number of Images | Number of Objects |
| :--- | :---: | :---: |
| Training | 653 | 7,724 |
| Validation | 173 | 1,765 |
| Test | 538 | 5,929 |
| **Total** | **1,364** | **15,418** |

### [cite_start]Class Appearances [cite: 93]
* [cite_start]**Motorbike:** 9,458 (Dominant mode of transport) [cite: 90, 93]
* [cite_start]**Car:** 3,967 [cite: 93]
* [cite_start]**Van / Truck / Bus / Bicycle / Fire truck:** 2,003 [cite: 93]

---

## 🛠️ System Architecture & Workflow

[cite_start]The adaptive control logic operates across three integrated layers[cite: 139]:
