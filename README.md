# Adaptive Timing Signal Control in Vietnam Traffic System

An intelligent, real-time traffic management system that dynamically adjusts green light durations based on traffic density and heterogeneous vehicle composition. By integrating computer vision (YOLOv8 & ByteTrack) with a localized traffic flow optimization algorithm, this system effectively mitigates urban congestion and reduces vehicle delay in high-density environments.

---

## Key Features

* **Real-Time Object Detection & Tracking:** Utilizes YOLOv8 optimized for object detection combined with ByteTrack and Supervision for robust multi-vehicle tracking, counting, and classification.
* **Localized PCU Metrics:** Implements a custom Passenger Car Unit (PCU) calculation tailored directly to Vietnamese urban traffic behavior, rather than standard international formulas.
* **Occlusion & Density Mitigation:** Designed with specialized camera calibration metrics (8m height, 200m distance) to handle high-density visual challenges and extreme vehicle occlusion.
* **Hardware Integration Ready:** Communication protocol configured via Modbus TCP to seamlessly sync vehicle metrics with industrial SCADA/PLC systems for field deployment.
* **SUMO Simulation:** Fully integrated with SUMO (Simulation of Urban Mobility) and TraCI to run dynamic traffic simulations, test edge cases, and calibrate the adaptive threshold coefficient (k).

---

## Dataset: UIT-VinaDeveS22

The model is trained and validated on the UIT-VinaDeveS22 benchmark dataset, reflecting real-world Vietnamese street conditions under various weather scenarios and diverse densities.

### Data Distribution

| Set | Number of Images | Number of Objects |
| --- | --- | --- |
| Training | 653 | 7,724 |
| Validation | 173 | 1,765 |
| Test | 538 | 5,929 |
| **Total** | **1,364** | **15,418** |

### Class Appearances

* **Motorbike:** 9,458 (Dominant mode of transport)
* **Car:** 3,967
* **Van / Truck / Bus / Bicycle / Fire truck:** 2,003

---

## System Architecture & Workflow

The adaptive control logic operates across three integrated layers:

```
[ Surveillance CCTV ] 
       │ (Captures 200m away at 8m height)
       ▼
[ Computer Vision Pipeline ] ──► YOLOv8 + ByteTrack (Vehicle Counting & Classification)
       │ 
       ▼ (Modbus TCP Transmission)
[ Industrial Controller ] ──► SCADA / PLC Memory updates
       │ 
       ▼ (Adaptive PCU Score Processing)
[ Traffic Optimization ] ──► Dynamic Green Time Extension Matrix

```

### Core Algorithm

The adaptive timing signal triggers when a lane's traffic volume exceeds the analyzed threshold. The extra green time length ($t_{\text{moreGreen}}$) is derived from:

$$t_{\text{moreGreen}} = \min(k \times (\text{lane}_{\text{WE.score}} - \text{lane}_{\text{NS.score}}), T_{\text{max}})$$

Where k represents the traffic coefficient, and scores are determined by localized vehicle weights.

---

## Tech Stack & Dependencies

* **Language:** Python 3.x
* **Computer Vision:** OpenCV, Ultralytics YOLOv8, Supervision, ByteTrack
* **Simulation:** SUMO (Simulation of Urban Mobility), TraCI API
* **Industrial Automation:** Modbus TCP Protocol, PLC/SCADA simulation environments

---

## Evaluation Metrics

The performance and robustness of the adaptive control framework are measured using both visual and traffic flow metrics:

1. **Object Detection Accuracy:** Evaluated up to 88% accuracy in heavy multi-class vehicle parsing.
2. **Average Vehicle Delay:** Measures the reduction in travel/waiting duration from intersection entrance to exit.
3. **Queue Length Stability:** Tracks bottleneck reduction and peak queue breakdown.
4. **Standard Deviation of Time:** Measures signal interval volatility to ensure smoother, predictable transitions for drivers.
