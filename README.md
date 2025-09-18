# Autonomous Pet-Rescue Robot

_A fully autonomous robot built entirely **from scratch** - integrating ESP-IDF/FreeRTOS firmware, Python-based signal processing, YOLOv5 computer vision, and advanced robotic control algorithms._

**Finalist** in a competitive challenge to rescue the most "pets" (stuffed animals) from a simulated burning building in the shortest time.

---

## Overview
Our team of four designed, built, and programmed an autonomous pet-rescue robot over two months, working ~80 hours/week in a dedicated project lab. The robot navigated a multi-terrain course, located "pets" via IR and computer vision, picked them up with a robotic arm, and launched them to safety via a custom flywheel mechanism.

Key features:
- **Custom hardware**: Designed and fabricated all PCBs and electrical circuits in-house.
- **Full-stack control**: Firmware in **C** using **ESP-IDF + FreeRTOS**; computer vision on Raspberry Pi 4.
- **Perception & ML**: Custom-trained **YOLOv5** Nano model for live object detection with optimized hyperparameters.
- **Signal processing**: FFT-based IR beacon tracking and frequency-specific control.
- **Multi-sensor navigation**: IR line following with phototransistors and emitters, beacon localization, and ML vision.
- **Advanced actuation**: Robotic arm with **inverse kinematics**; flywheel launcher for object evacuation.

---

## My Contributions
**Role:** Software & Electrical Systems Engineer  

- **Machine Learning & Computer Vision**
  - Custom-trained YOLOv5 Nano model for detecting pets on-course.
  - Tuned hyperparameters, validated model accuracy, and benchmarked performance.
  - Optimized Raspberry Pi OS (Linux based) for real-time inference:
    - Overclocking
    - SSH development workflow
    - Performance profiling and bottleneck removal
  - Integrated ML output with robotic arm targeting via UART communication.

- **Signal Processing**
  - Designed FFT-based algorithms to detect a 10 kHz central IR beacon for positional tracking.
  - Built FFT-based IR emission/reception for autonomous control, filtering specific frequency bands.
  - Applied convolutional signal matching on IR sensor streams to robustly identify “pet” targets and filter out environmental noise.

- **Firmware Development**
  - Wrote FreeRTOS tasks for navigation, arm control, and sensor fusion on ESP32.
  - Implemented custom sensor drivers and UART drivers for Pi–ESP32 communication.
  - Used thread-safe practices by incorperating mutexes, semephores, and event groups for inter-task dependencies
  - Developed Python GUIs for validating and testing sensor data and hardware.

- **Electrical Hardware**
  - Designed PCB layouts for motor drivers, sensor interfaces, and communication buses.
  - Built custom H-bridges for DC motor control.
  - Defined electrical architecture to integrate all subsystems safely and efficiently.

---

## Challenges & Solutions
- **IR interference from environment**  
  *Issue:* Sunlight and other IR sources caused erratic sensor behavior.  
  *Solution:* Added FFT filtering to isolate specific IR frequency bands (10 kHz), though we learned to apply stricter band-pass processing earlier in future designs.

- **ADC sampling instability in ESP-IDF**  
  *Issue:* Sampling ADC at 0.1 ms intervals caused timeouts and corrupted readings.  
  *Solution:* Rewrote sampling system with strategic task timing and priority management in FreeRTOS.

- **Concurrency & communication stability**  
  *Issue:* Serial communication between GUI and ESP32 caused data corruption and crashes.  
  *Solution:* Introduced mutexes, semaphores, and thread-safe buffers to prevent race conditions.

---

## Results
- **Finalist** in competition with consistently 60% pet rescue.
- Reduced navigation and targeting errors by 50% through sensor calibration and ML tuning.
- Integrated hardware, firmware, and ML with no major system failures during final runs.
- Achieved stable 10+ FPS real-time object detection on Raspberry Pi 4 with YOLOv5 Nano.

---

## Technologies Used
**Hardware:**  
ESP32 microcontroller, Raspberry Pi 4 + Pi Camera, MG996R servos, ToF sensors (VL6180X), Hall effect sensors, IR emitters & phototransistors, custom PCBs.

**Software & Firmware:**  
ESP-IDF, FreeRTOS, C, Python, YOLOv5, OpenCV, NumPy, Matplotlib, TensorFlow Lite.

**Signal Processing:**  
FFT-based detection & filtering, band-pass IR frequency tracking.

**Tools:**  
KiCad, OnShape, VS Code, Platform IO, GitHub, Logic Analyzer, Oscilloscope, Linux SSH.

---

## System Architecture
![System Architecture](images/system_architecture.png)  
*High-level diagram showing hardware and software integration.*

---

## Project Links
-  [ESP-IDF Firmware Repository](https://github.com/enph-summer-2025/rollingohms)
-  [Machine Learning Repository](https://github.com/enph-summer-2025/computer_vision)  
-  [PCB Design Repository](https://github.com/enph-summer-2025/rollings-ohms-pcbs)  
-  [Signal Processing Repository](https://github.com/enph-summer-2025/ir_esp) 
-  [Demo Video](https://drive.google.com/file/d/1vrrbmOzqqDvycMX8IW5s0msy8z-JhquK/view?usp=share_link)
-  [Google Drive](https://drive.google.com/drive/folders/1pfD4E5x2K_xVr7HdItIgMcFwQVXqLsNb?usp=share_link)

---

## Media Coverage
- **Interview Feature:** [UBC Engineering Physics students race to save ‘pets’ with robots](https://vancouver.citynews.ca/2025/08/07/vancouver-ubc-robots-engineering-physics/)
- **Competition Overview:** [UBC robot competition demonstrates student skill, perseverance](https://www.ctvnews.ca/vancouver/article/ubc-robot-competition-demonstrates-student-skill-perseverance/)

---
