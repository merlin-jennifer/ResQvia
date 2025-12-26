# ResQvia
A standalone SOS emergency device built on ESP32 using GSM and GPS for instant alerts, with on-device TinyML wake-word detection enabling hands-free, offline SOS triggering. Designed for low power, reliability, and real-world scalability.

# Problem Statement:

In emergency situations such as accidents, medical crises, or personal safety threats, victims often cannot access or operate smartphones due to panic, injury, or time constraints.
Most existing solutions rely on mobile apps, internet connectivity, or manual interaction, making them unreliable during critical moments.

There is a strong need for a dedicated, always-available, hardware-based SOS system that works independently, responds instantly, and is suitable for mass adoption.

#  Solution Overview:

ResQviia is a standalone embedded SOS device that:

->Instantly sends alerts via GSM

->Shares real-time GPS location

->Supports manual and voice-based triggering

->Operates offline, without smartphones or internet

->Is designed to be compact, low-power, and PCB-ready

# System Architecture
Core Modules:
1) ESP32 — Main controller & logic

2) A9G module — GSM (SMS/Call) + GPS

3) Microphone — Voice / wake-word detection

4) Push Button — Manual SOS trigger

5) Li-ion Battery + TP4056 — Portable power management

# Key Features

-Live GPS location tracking

-SOS alerts via SMS and call

-Hands-free wake-word activation (TinyML)

-Low-power portable operation

-Modular design for easy scaling

-Designed for custom PCB & manufacturing

# Hardware Components
Component	Purpose
ESP32: Main controller
A9G GSM+GPS: Communication & location
Microphone module: Audio input
Push button: Manual SOS
TP4056:	Battery charging
3.7V Li-ion battery:	Power source

# Firmware Overview

Developed using Arduino / ESP-IDF

GSM handled using AT commands

GPS parsed via NMEA sentences

Modular firmware separating:

  a) Communication

  b) Sensor input

  c) ML inference

  d) Power management

# On-Device Wake-Word Detection (TinyML)

ResQviia integrates TinyML-based wake-word detection to allow hands-free SOS activation using a predefined keyword (e.g., “help”).

The ML system runs entirely on the ESP32, ensuring:

->No cloud dependency

->Ultra-low latency

->User privacy

->Reliable offline operation

# ML Pipeline

Inference Flow:

1. Microphone captures short audio frames

2. Audio converted to MFCC features

3. Lightweight neural network performs inference

4. Wake-word probability crosses threshold

5. SOS routine triggered automatically

# ML Performance Targets
<img width="693" height="332" alt="image" src="https://github.com/user-attachments/assets/651b177e-0afb-4eb6-9170-08e49546c091" />

# ML Training & Deployment Workflow

1. Dataset Collection

Wake-word samples from multiple speakers

Background noise & negative samples

2. Feature Extraction

MFCCs (20–40 coefficients)

Frame size: ~20 ms, 50% overlap

3. Model Training

Framework: TensorFlow

Architecture: DS-CNN

Quantization: INT8 (post-training)

4. Deployment

Convert to .tflite

Run inference using TensorFlow Lite Micro

Integrated directly into ESP32 firmware

# Power Optimization

-ESP32 operates in light-sleep mode

-Audio + ML inference runs in periodic windows

-SOS triggers immediately override sleep states

# Future Enhancements

a) Speaker-independent multi-language wake words

b) Adaptive noise-based thresholding

c) Migration to ESP32-S3 for ML acceleration

d) Emergency service API integration

e) Ultra-low-power always-on listening

# Tools & Technologies

-ESP32 (Arduino / ESP-IDF)

-TensorFlow & TensorFlow Lite for Microcontrollers

-Python (training & preprocessing)

-Embedded C/C++

-GSM AT command interface
