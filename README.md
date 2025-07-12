# Strain Gauge-Based Torque Sensor  
*University of Moratuwa – EN2160 Electronic Design Realization*

---

## Overview  
This project is a strain gauge-based torque sensor designed for accurate, robust, and wireless torque measurement in industrial settings. It employs dual-grid shear strain gauges in a full Wheatstone bridge configuration, advanced signal conditioning, wireless power and data transmission, and a compact shaft-mounted PCB.

---

## Features
- **Measurement Range:** Up to 50 N·cm  
- **Wireless Power & Data:** Inductive power transfer and Bluetooth Low Energy (BLE) transmission  
- **High Sensitivity:** Full-bridge Wheatstone configuration with dual-grid strain gauges  
- **Robust Construction:** Stainless steel enclosure, precision shaft, and flex PCB  
- **Real-Time Monitoring:** BLE-enabled, compatible with mobile and desktop visualization tools  

---

## Hardware Architecture

| Subsystem          | Key Components                    | Description                                        |
|--------------------|---------------------------------|--------------------------------------------------|
| **Sensing**        | SGT-2DC/350-SY11 Dual-Grid Strain Gauges | Measures torsional strain on shaft at ±45°       |
| **Signal Conditioning** | INA333 Instrumentation Amplifier, OPA336 Offset Circuit | Amplifies and zeroes bridge output for ADC        |
| **Data Acquisition**| HX711 24-bit ADC                 | High-resolution digitization of analog signal    |
| **Processing & BLE**| DA14531 BLE MCU                 | Reads ADC, processes data, transmits via Bluetooth |
| **Power**          | Inductive Tx/Rx coils, Boost Converter | Wireless power delivery to rotating shaft electronics |
| **Enclosure**      | Stainless Steel, Bearings, Flex PCB | Protects internals, enables rotation, houses electronics |

---

## Getting Started

### 1. Hardware Assembly  
- Mount dual-grid strain gauges at ±45° on the shaft’s central region, 180° apart.  
- Assemble the two-part stainless steel enclosure with bearings securing the shaft ends.  
- Attach the flex PCB and receiver coil to the shaft; mount the transmitter coil concentrically inside the enclosure.

### 2. Powering the System  
- Connect a 5V DC supply to the transmitter PCB via USB.  
- The transmitter coil wirelessly powers the shaft electronics via inductive coupling.

### 3. Firmware & Programming  
- Program the DA14531 BLE MCU using Keil MDK and SmartBond Flash Programmer.  
- MCU reads HX711 ADC data and streams torque values over BLE.  
- Device advertises as BLE peripheral for real-time data transmission.

### 4. Data Visualization  
- Use a BLE-enabled app or custom software to receive and display real-time torque data.  
- Data format: 24-bit signed values scaled through calibration.

---

## Calibration & Testing

- **Zero Calibration:** Use the OPA336 offset circuit to zero output with no torque applied.  
- **Span Calibration:** Apply known torques and record output to create calibration curves.  
- **Validation:** Verify accuracy by comparing with reference torque instruments.

---

## Bill of Materials (Key Items)

| Category           | Item/Model                   | Qty | Notes                      |
|--------------------|------------------------------|-----|----------------------------|
| Strain Gauge       | SGT-2DC/350-SY11             | 1   | Omega Engineering          |
| Instrumentation Amp | INA333, OPA336               | 2   | Signal conditioning        |
| ADC                | HX711                        | 1   | 24-bit, digital            |
| MCU                | DA14531                      | 1   | BLE, ultra-compact         |
| Power              | Inductive Tx/Rx coils        | 2   | Wireless power             |
| Enclosure          | Stainless steel, bearings    | 1   | Robust protection          |
| PCB                | Flex PCB                     | 1   | Shaft-mounted              |

---

## Schematic & PCB Design  
- Detailed schematics cover transmitter, receiver, booster, instrumentation amplifier, offset circuit, ADC, and MCU.  
- Two-layer polyimide flex PCB designed with a component-free center area for shaft mounting and teardrop pads for mechanical strength.

---

## Software Structure

- **BLE Service:** Custom GATT profile for torque data streaming.  
- **GPIO Setup:** Dedicated pins for HX711, status LED, SPI flash.  
- **HX711 Integration:** Timer-based data acquisition with endian conversion and BLE notifications.

---

## Maintenance & Troubleshooting

- **Enclosure Access:** Loosen bolts to open and service internal components.  
- **PCB/Flex Issues:** Inspect for cracks or delamination, especially near bends.  
- **Wireless Power:** Ensure proper coil alignment for optimal power transfer.  
- **Signal Noise:** Use shielded cables and proper grounding to minimize interference.

---

## References  
- Component datasheets: OPA336, INA333, HX711, DA14531  
- Manufacturer application notes: Omega Engineering, Flintec  
- Project design report for detailed theory, calculations, and simulations  

---

## Authors  
Aashir M.R.M., Basith M.N.A., Kumarage R.V., Manawadu D.N., Manawadu M.D., Munavvar M.A.A., Ransika L.G.C., Samuditha H.K.P.

---

## License  
This project is for academic and research purposes at the University of Moratuwa. For reuse or adaptation, please contact the project authors or supervising faculty.

