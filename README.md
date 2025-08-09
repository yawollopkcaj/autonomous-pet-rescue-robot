# Autonomous Search-and-Rescue Robot

_A finalist autonomous robotics project built entirely from scratch, integrating custom PCBs, embedded firmware, advanced signal processing, machine learning, and computer vision._

---

## 📌 Overview
This was a two-month, full-time capstone-style project in which our team of four designed and built a **fully autonomous robot** to compete in a “burning building rescue” challenge. The objective: **rescue the maximum number of stuffed animal "pets" from a simulated burning building in the shortest possible time**.

We designed every aspect of the robot from the ground up:
- **Custom hardware** (PCBs, circuits, mechanical systems)
- **Embedded software** (ESP-IDF + FreeRTOS in C)
- **Machine learning & computer vision** (YOLOv5 on Raspberry Pi)
- **Signal processing** (FFT-based beacon tracking, IR-based navigation)
- **Autonomous control** (line following, inverse kinematics, flywheel launching mechanism)

Our robot navigated the course, located pets via IR beacons and computer vision, used a robotic arm for retrieval, and launched them to safety with a custom flywheel shooter. We were **finalists in the competition**.

---

## 🛠️ My Contributions
I focused on **software, electrical engineering, and machine learning**:
- **Machine Learning & Computer Vision**
  - Custom-trained YOLOv5 nano model with tuned hyperparameters for detecting “pets” in real-time.
  - Ran on a Raspberry Pi 4 with Pi Camera, optimized for high FPS live inference.
  - Overclocked Pi and optimized Linux OS for reduced latency.
  - Validated and benchmarked the model for accuracy and speed.
  - Used **UART communication** between Raspberry Pi and ESP32 for command exchange.

- **Embedded Firmware**
  - Wrote firmware in **ESP-IDF** and **FreeRTOS** (C).
  - Implemented **multi-tasking control** for navigation, arm movement (inverse kinematics), and sensor fusion.
  - Developed FreeRTOS tasks for:
    - Line following (IR phototransistors + emitters).
    - FFT-based detection of a **10 kHz IR beacon** for global positioning.
    - Autonomous arm actuation and pet launching sequence.

- **Signal Processing**
  - Designed FFT pipelines to detect IR frequency magnitudes.
  - Performed frequency band isolation to reduce false triggers (see "Challenges" below).
  - Implemented filtering and signal transformations for robust navigation.

- **Electrical Design**
  - Designed and assembled **custom PCBs** for sensors, power distribution, and motor control.
  - Built custom **H-bridges** for DC motor drive systems.
  - Integrated multiple ADC inputs with careful sampling scheduling to avoid ESP32 ADC timeouts.

---

## 🔍 Challenges & Solutions

### **1. IR Interference Hell**
- **Problem:** IR systems would randomly stop working — later discovered sunlight and other environmental IR sources were saturating our sensors.
- **Solution:** Moved to narrow-band frequency detection via FFT and improved bandpass filtering to reject unwanted IR frequencies.

### **2. ADC Sampling Failures**
- **Problem:** Sampling ESP32 ADC every 0.1 ms caused timeouts, crashes, and erratic robot behavior.
- **Solution:** Allocated strategic sampling periods for different ADC tasks, preventing overload while maintaining data quality.

### **3. Concurrency & Thread Safety**
- **Problem:** Serial GUI control and robot firmware would produce garbage data or crash under concurrent access.
- **Solution:** Added mutexes and semaphores in FreeRTOS to enforce thread-safe communication.

---

## 📈 Results
- **Competition Finalist** — consistently completed course objectives under time constraints.
- Achieved **high object detection accuracy** with YOLOv5 nano on constrained hardware.
- Successful **real-time integration** of ML, embedded control, and signal processing.
- Logged hundreds of test runs, iterating on navigation accuracy and reliability.

---

## 📊 System Architecture
![System Architecture](images/system_architecture.png)  
*High-level diagram showing hardware, firmware, and ML integration.*

---

## 🖥️ Technologies Used

**Hardware & Electronics**  
- ESP32 microcontroller  
- Raspberry Pi 4 + Pi Camera  
- MG996R servo motors, DC motors, flywheel launcher  
- IR phototransistors + emitters, ToF sensors (VL6180X), Hall effect sensors  
- Custom PCBs (KiCad), H-bridges, power management  

**Software & Firmware**  
- ESP-IDF, FreeRTOS (C)  
- Python (signal processing, GUIs, ML training)  
- YOLOv5 (PyTorch → TensorFlow Lite)  
- OpenCV for image processing  
- Linux (Raspberry Pi OS), SSH control  

**Tools & Methods**  
- KiCad PCB Design  
- SolidWorks mechanical design  
- FFT signal analysis  
- UART serial communication  
- Mutex & semaphore concurrency control  
- Overclocking and OS optimization on Raspberry Pi  

---

## 📂 Project Links
- 📂 [PCB Design Repository](https://github.com/yourteam/pcb-repo)  
- 📂 [ESP-IDF Firmware Repository](https://github.com/yourteam/firmware-repo)  
- 📂 [Signal Processing Repository](https://github.com/yourteam/signal-processing-repo)  
- 📂 [Machine Learning Repository](https://github.com/yourteam/ml-repo)  
- 📹 [Demo Video](https://linktodemo.com)  
- 📄 [Full Technical Report (PDF)](docs/report.pdf)  

---

## 📷 Gallery
| Hardware Prototype | PCB Layout | Test Run |
|---|---|---|
| ![](images/hardware.jpg) | ![](images/pcb.jpg) | ![](images/test_run.gif) |

---

## 📜 License
This project is licensed under the [MIT License](LICENSE).

---
