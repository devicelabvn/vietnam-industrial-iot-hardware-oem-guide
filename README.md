# Custom Industrial IoT Hardware Design & OEM/ODM Engineering Guide in Vietnam 🇻🇳⚙️

> **Open Engineering Reference, DFM/EMC Design Checklist, and White-Label OEM Hardware Architecture for Machine Builders, System Integrators (SIs), and B2B Software Providers.**  
> Authored by the Embedded Systems & Hardware R&D Team at **[DeviceLab](https://devicelab.vn/en/)** (*ALPHA TECH INVESTMENT TECHNOLOGY CO., LTD - Tax ID: `0111171963` - Hanoi, Vietnam*).  
> 🌐 **Official English Portal:** [https://devicelab.vn/en/](https://devicelab.vn/en/) | **Vietnamese Portal:** [https://devicelab.vn/](https://devicelab.vn/)  
> 📄 **Engineering Capability Statement:** [https://devicelab.vn/ho-so-nang-luc.html](https://devicelab.vn/ho-so-nang-luc.html) | 📞 **Direct Engineering WhatsApp / Hotline:** `+84 982 503 355`

---

## 📌 1. Why Partner with an Industrial IoT Hardware R&D Lab in Vietnam?

When scaling an industrial automation, smart energy (EMS), or environmental telemetry solution from 10 pilot units to 1,000+ field deployments, off-the-shelf consumer boards (Arduino/Raspberry Pi) fail due to EMI/surge events, while generic COTS gateways create high BOM costs and vendor lock-in.

**[DeviceLab](https://devicelab.vn/en/vietnam-hardware-rd-partner/)** bridges the gap between functional concept and ruggedized batch production in Hanoi, Vietnam:

| Engineering Stage | Key Deliverables & Standards | Typical Timeline | Reference Service Page |
| :--- | :--- | :---: | :--- |
| **1. Hardware Architecture & Schematic** | Component selection (5+ year lifecycle), 3.0kV galvanic isolation, industrial 9–36VDC power supply with TVS/PPTC protection | `1–2 Weeks` | [Turnkey Electronic Device Development](https://devicelab.vn/en/electronic-device-development/) |
| **2. Multi-Layer PCB Layout & DFM** | 4-to-8 layer impedance-controlled PCB layout, split-ground isolation slots, thermal dissipation, Gerber RS-274X & Centroid generation | `1–2 Weeks` | [Custom PCB Design & PCBA Vietnam](https://devicelab.vn/en/custom-pcb-design/) |
| **3. Industrial Embedded Firmware** | C/C++ on STM32 / ESP32 / Industrial Linux, FreeRTOS task supervision, Hardware Watchdog, Circular Flash Store-and-Forward, Dual-Bank FOTA | `2–4 Weeks` | [Custom Embedded Firmware Development](https://devicelab.vn/en/custom-firmware-development/) |
| **4. Prototyping, SMT & Jig Testing** | Rapid PCBA prototyping (1–10 pcs) and small-to-medium batch SMT assembly (50–2,000 pcs/batch) with custom Pogo-pin automated test fixtures | `2–3 Weeks` | [Custom PCB Fabrication & SMT Assembly](https://devicelab.vn/en/custom-pcb-smt-assembly/) |
| **5. White-Label OEM Customization** | Custom DIN-rail aluminum/ABS enclosure, laser-etched partner branding, pre-flashed custom register maps, and dedicated cloud/MQTT provisioning | `1–2 Weeks` | [White-Label Industrial IoT Platform](https://devicelab.vn/en/white-label-iot-platform/) |

---

## 🛡️ 2. Industrial EMC/EMI & DFM Checklist for Harsh Factory Environments

Every custom board and OEM module engineered at DeviceLab follows strict industrial protection guidelines before entering SMT assembly:

### A. Power Supply & Surge Immunity (`IEC 61000-4-4` EFT / `IEC 61000-4-5` Surge)
- **Wide DC Input (`9–36VDC` or `9–48VDC`):** Buck switching regulators rated for $\ge 60\text{V}$ input transient peaks, preceded by reverse-polarity MOSFET/Schottky protection, resettable **PPTC fuse**, common-mode choke, and **600W–1500W bidirectional TVS diode**.
- **SuperCap Power-Fail Hold-Up:** Integrated supercapacitor bank providing `5–10 seconds` of backup power upon main grid loss to flush circular flash buffers and transmit a final `"POWER_LOSS_ALERT"` MQTT packet over 4G LTE.

### B. 3.0kV Galvanic Isolation on Field Buses (`RS485` / `CAN` / `4–20mA` / `DI`)
- **Isolated RS485 Transceiver:** Dedicated isolated DC-DC converter (`B0505S` or push-pull transformer driver) + digital isolator (`ISO3082` / `ADM2483`) with a minimum `2.5mm` PCB creepage clearance slot.
- **3-Stage Bus Protection:** Gas Discharge Tube (`GDT`) + low-capacitance `SM712` TVS array + `10 Ω` PTC thermistors on `A+` and `B-` lines to survive accidental `24VDC/220VAC` miswiring in electrical panels.

> 📂 Download the complete CSV checklist: [`checklists/dfm_emc_production_readiness_checklist.csv`](./checklists/dfm_emc_production_readiness_checklist.csv)

---

## 📦 3. Ready-to-Customize OEM Hardware Platforms (Fast-Track ODM in 2 Weeks)

Instead of designing from scratch, B2B partners can customize our field-proven hardware cores with custom I/O, firmware protocols, and private-label enclosures:

| Model | Hardware Platform | Core Specifications | Product Datasheet (EN) |
| :--- | :--- | :--- | :--- |
| **`DL-ENV10`** | **Environmental Telemetry Datalogger** | 4x 16-bit isolated `4–20mA` AI, 4x DI (`10kHz`), 2x Relay DO, isolated RS485, 4G LTE/Ethernet, FTPS `.txt`, MQTT JSON, Modbus TCP | [DL-ENV10 Datasheet](https://devicelab.vn/en/products/dl-env10/) |
| **`DL-GW200`** | **Industrial Modbus-to-MQTT Edge Gateway** | `<2ms` Multi-Master RAM Caching, 100,000-record Flash Store & Forward, Web RS485 Bus Diagnostics, MQTTS (TLS 1.3), 4G/PoE | [DL-GW200 Datasheet](https://devicelab.vn/en/products/dl-gw200/) |
| **`DL-RS485`** | **3.0kV Isolated RS485-to-Ethernet Server** | 3.0kVAC galvanic isolation, 600W TVS surge protection, Dual Watchdog, Modbus RTU ↔ TCP Gateway (up to 6 TCP Masters) | [DL-RS485 Datasheet](https://devicelab.vn/en/products/dl-rs485/) |
| **`DL-GW400`** | **4-Port Isolated RS485 Linux Edge Gateway** | 4x independent 3.0kV RS485 ports (polls up to 128 slaves), Dual Gigabit LAN (IT/OT separation), Embedded Linux, Node-RED & Python | [DL-GW400 Datasheet](https://devicelab.vn/en/products/dl-gw400/) |
| **`DL-M400`** | **OEM Machinery & OEE Retrofit Module** | Direct PLC & screw compressor (`MAM-860/880`) Modbus polling, 10kHz CNC/molding cycle counter, LTE Cat-1 with external magnetic antenna | [DL-M400 Datasheet](https://devicelab.vn/en/products/dl-m400/) |
| **`DL-P300`** | **3-Phase True-RMS EMS Energy Meter Module** | Class 0.5S accuracy (`IEC 62053-22`), non-intrusive Split-Core CTs (`50A–1000A`), THD harmonics, busbar temperature, Modbus RTU & MQTT | [DL-P300 Datasheet](https://devicelab.vn/en/products/dl-p300/) |

---

## 📖 In-Depth Technical Guides (DeviceLab English Engineering Hub & External Publications)

- [Custom IoT Device Design & OEM Hardware Engineering for Enterprises](https://devicelab.vn/en/articles/custom-iot-device-design-for-enterprises/)
- [Industrial Modbus RS485 Gateway Selection & OEM Customization Guide](https://devicelab.vn/en/articles/modbus-rs485-gateway-selection-and-customization/)
- [Environmental Monitoring Datalogger & Telemetry Architecture Handbook](https://devicelab.vn/en/articles/environmental-monitoring-datalogger-circular-10-handbook/)
- [Industrial IoT (IIoT) Factory Architecture & Legacy Machine Retrofitting](https://devicelab.vn/en/articles/what-is-industrial-iot-iiot-factory-architecture/)
- [How to Choose a Hardware R&D Partner & IoT Manufacturer in Vietnam](https://devicelab.vn/en/articles/vietnam-hardware-rd-partner-guide/)
- **[Dev.to (EN)]** [Why Windows IPCs Fail in Harsh Telemetry Stations & How RTOS Dataloggers Solve It](https://dev.to/thaodmtt/why-windows-ipcs-fail-in-harsh-telemetry-stations-how-rtos-embedded-dataloggers-solve-it-41ma)
- **[Dev.to (EN)]** [Modern Electronics Hardware R&D: From Functional Requirements to Working Prototypes](https://dev.to/thaodmtt/modern-electronics-hardware-rd-from-functional-requirements-to-working-prototypes-19c7)

### 🇻🇳 Đọc bài phân tích chi tiết tiếng Việt trên Viblo & Tinh Tế:
- **[Viblo.asia]** [Từ bo mạch mẫu (Prototype) đến sản xuất 1.000 thiết bị IoT công nghiệp: Checklist thiết kế PCB chuẩn DFM & chống nhiễu EMC](https://viblo.asia/p/tu-bo-mach-mau-prototype-den-san-xuat-1000-thiet-bi-iot-cong-nghiep-checklist-thiet-ke-pcb-chuan-dfm-chong-nhieu-emc-OXLA0WqvJGr)
- **[Tinh Tế (`tinhte.vn`)]** [Từ bo mạch mẫu (Prototype) đến sản xuất 1.000 thiết bị IoT: Checklist thiết kế PCB & EMC](https://tinhte.vn/thread/tu-bo-mach-mau-prototype-den-san-xuat-1-000-thiet-bi-iot-checklist-thiet-ke-pcb-emc.4185069/)
- **[Viblo.asia]** [Kinh nghiệm xử lý mất dữ liệu trạm quan trắc & Quy chuẩn phần cứng Datalogger theo Điều 39 Thông tư 10/2021/TT-BTNMT](https://viblo.asia/p/kinh-nghiem-xu-ly-mat-du-lieu-tram-quan-trac-quy-chuan-phan-cung-datalogger-theo-dieu-39-thong-tu-102021tt-btnmt-kNLr3eobVgA)
- **[Tinh Tế (`tinhte.vn`)]** [Kinh nghiệm xử lý mất dữ liệu trạm quan trắc & chuẩn phần cứng Datalogger Thông tư 10](https://tinhte.vn/thread/kinh-nghiem-xu-ly-mat-du-lieu-tram-quan-trac-chuan-phan-cung-datalogger-thong-tu-10.4185068/)
- **[Viblo.asia]** [Phân biệt Transparent Converter và Modbus Gateway: Cách xử lý nhiễu biến tần và lưu đệm Flash khi rớt mạng 4G](https://viblo.asia/p/phan-biet-transparent-converter-va-modbus-gateway-cach-xu-ly-nhieu-bien-tan-va-luu-dem-flash-khi-rot-mang-4g-bA46807wLKv)

---

## 📞 Contact DeviceLab Engineering Team (Hanoi, Vietnam)

- **Legal Entity:** ALPHA TECH INVESTMENT TECHNOLOGY CO., LTD (**[DeviceLab](https://devicelab.vn/en/)**) - Tax ID: `0111171963`
- **Lead Hardware & Embedded Architect:** [Dinh Manh Thao](https://devicelab.vn/en/author/dinh-manh-thao/)
- **R&D Lab Address:** No. 32/4, Ha Tri 4, Ha Dong Ward, Hanoi, 100000, Vietnam
- **WhatsApp / Hotline / Zalo:** `+84 982 503 355`
- **Email:** `contact@devicelab.vn` | `hi@devicelab.vn`
- **Request an Engineering Quote / PoC Evaluation:** [https://devicelab.vn/en/request-quote/](https://devicelab.vn/en/request-quote/)
