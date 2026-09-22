# Adaptive Precision Reconfigurable TinyML CNN Accelerator

An FPGA-based TinyML CNN accelerator designed for efficient edge AI applications using **adaptive precision computation**.

The proposed accelerator supports **1-bit, 4-bit, and 8-bit precision modes**, providing flexibility between model accuracy, memory usage, hardware resources, and power consumption. The hardware architecture is implemented using **Verilog HDL** and evaluated on a **Xilinx Artix-7 XC7A35T FPGA** using Xilinx Vivado.

---

## 📌 Project Overview

Deep learning models can require significant computational and memory resources, making them difficult to deploy on resource-constrained edge devices.

This project explores an **Adaptive Precision Reconfigurable CNN Accelerator** that allows different numerical precision levels to be selected according to application requirements.

The CNN model was trained using the **LeapGestRecog dataset** for gesture recognition and evaluated at different quantization levels.

### Supported Precision Modes

| Precision | Accuracy | Model Size |
| --------- | -------- | ---------- |
| 8-bit     | 100.00%  | 812 KB     |
| 4-bit     | 99.94%   | 406 KB     |
| 1-bit     | 28.25%   | 101 KB     |

The **4-bit model** provides a high classification accuracy while reducing the model size compared with the 8-bit version.

---

## 🏗️ Hardware Architecture

The accelerator consists of the following major modules:

```text
Input Pixel
     │
     ▼
Input Memory
     │
     ▼
Window Generator
     │
     ▼
Precision Controller
     │
     ▼
Adaptive MAC Unit
     │
     ▼
ReLU Activation
     │
     ▼
Max Pooling
     │
     ▼
Final Output
```

### Main RTL Modules

* `cnn_accelerator.v` — Top-level accelerator module
* `precision_controller.v` — Selects the operating precision
* `input_memory.v` — Stores input pixel data
* `window_generator.v` — Generates the CNN input window
* `mac_unit.v` — Performs precision-dependent multiplication
* `relu.v` — Implements ReLU activation
* `pooling.v` — Performs maximum pooling
* `cnn_accelerator_tb.v` — Verilog testbench for simulation

---

## 💻 Technologies Used

* **Verilog HDL**
* **Xilinx Vivado**
* **Xilinx Artix-7 XC7A35T FPGA**
* **TensorFlow / TensorFlow Lite**
* **CNN Quantization**
* **TinyML**
* **FPGA-based Hardware Acceleration**

---

## 📊 FPGA Implementation Results

The proposed accelerator was implemented on a Xilinx Artix-7 XC7A35T FPGA.

| Parameter           | Result                 |
| ------------------- | ---------------------- |
| FPGA                | Xilinx Artix-7 XC7A35T |
| Operating Frequency | 100 MHz                |
| Slice LUTs          | 175                    |
| Slice Registers     | 68                     |
| DSPs                | 0                      |
| BRAM                | 0                      |
| Total On-Chip Power | 79 mW                  |
| Timing Violations   | 0                      |

The implementation achieved the required **100 MHz operating frequency without timing violations**.

### Module-wise LUT Utilization

| Module                | LUTs |
| --------------------- | ---- |
| MAC Unit              | 91   |
| Input Memory          | 8    |
| Pooling Unit          | 73   |
| Top-Level Accelerator | 175  |

---

## ⚡ Power Analysis

The Vivado power analysis reported a total on-chip power consumption of approximately:

**79 mW**

The design was evaluated using randomly generated test activity to estimate switching behavior and power consumption.

The reported power components include:

* Static Power: 60 mW
* Dynamic Power: 18 mW
* Clock Power: 1 mW
* Signal Power: 2 mW
* Logic Power: 2 mW
* I/O Power: 14 mW

---

## 🧪 Simulation

A Verilog testbench was developed to verify the accelerator.

The testbench applies randomly generated:

* Input pixels
* Weights
* Precision modes

A total of **10,000 test cases** were applied during the simulation and used for switching-activity analysis.

### Testbench

```text
Simulation/
└── cnn_accelerator_tb.v
```

---

## 📁 Repository Structure

```text
Adaptive-Precision-Reconfigurable-TinyML-Accelerator/
│
├── README.md
│
├── cnn_accelerator.v
├── cnn_accelerator_tb.v
├── input_memory.v
├── mac_unit.v
├── pooling.v
├── precision_controller.v
├── relu.v
├── window_generator.v
│
├── RESULTS_f.pdf
│
└── Project_Report.pdf
```

---

## 🎯 Objectives

* Develop a lightweight CNN accelerator for TinyML applications.
* Support multiple precision levels: **1-bit, 4-bit, and 8-bit**.
* Reduce memory and hardware requirements.
* Implement the accelerator using Verilog HDL.
* Evaluate the design on an Artix-7 FPGA.
* Analyze FPGA resource utilization, timing, and power consumption.
* Explore efficient hardware architectures for edge AI applications.

---

## 🌐 Application

The accelerator is targeted toward **low-power edge AI and TinyML applications**, particularly applications where computational resources, memory, and power consumption are limited.

The project demonstrates how precision selection and FPGA-based acceleration can be combined for efficient neural-network inference.

---

## 👥 Team

**Project Team**

* Akula Manasa Reddy
* Priashrinagalosini S
* Veligatla Pardhu Sai Harsha

---

## 📄 Documentation

The repository includes the project report and implementation results containing:

* CNN model and quantization results
* FPGA implementation
* Resource utilization
* Timing analysis
* Power analysis
* Module-wise utilization
* Comparison with existing CNN accelerator designs

---

## 🚀 Future Scope

Future improvements can include:

* Implementing a complete multi-pixel convolution datapath
* Improving the 1-bit binary computation architecture
* Supporting larger CNN models
* Adding more efficient on-chip memory architectures
* Hardware-software co-design for real-time gesture recognition
* Further optimization of power and FPGA resource utilization
* Deployment on additional edge-AI FPGA platforms

---

## 📌 Keywords

`TinyML` `CNN` `FPGA` `Xilinx` `Artix-7` `Vivado` `Edge AI` `Quantization` `Verilog` `Hardware Accelerator` `Deep Learning` `Reconfigurable Architecture` `Low Power AI`

---

## ⭐ Project Highlights

* **1-bit / 4-bit / 8-bit adaptive precision**
* **99.94% accuracy with 4-bit quantization**
* **175 LUTs**
* **68 registers**
* **79 mW total on-chip power**
* **100 MHz operating frequency**
* **0 DSPs**
* **0 BRAMs**
* **No reported timing violations**
* FPGA-based TinyML implementation
