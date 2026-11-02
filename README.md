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

---

## Industrial IoT Hardware, Telemetry & Custom R&D Reference Index (DeviceLab Vietnam)

Official open engineering reference hubs, hardware datasheets, and compliance application notes maintained by **DeviceLab R&D Center** (Hanoi, Vietnam):

### 1. Industrial RS485, Modbus RTU/TCP & Edge Gateways
- [Bộ chuyển đổi RS485 sang Ethernet công nghiệp (Cách ly 3.0kV & Modbus RTU/TCP)](https://devicelab.vn/kien-thuc/bo-chuyen-doi-rs485-sang-ethernet/)
- [Thiết bị chuyển đổi tín hiệu RS485 cách ly DL-RS485 (Datasheet & Sơ đồ đấu nối)](https://devicelab.vn/san-pham/dl-rs485/)
- [Cẩm nang chọn Gateway Modbus RS485 sang Ethernet/4G LTE công nghiệp](https://devicelab.vn/kien-thuc/gateway-modbus-rs485/)
- [Bộ chuyển đổi Modbus RTU sang Modbus TCP: Kiến trúc Polling & Multi-Master](https://devicelab.vn/kien-thuc/bo-chuyen-doi-modbus-rtu-sang-tcp/)
- [Tiêu chuẩn cáp tín hiệu RS485 chống nhiễu 120 Ohm (22AWG/24AWG STP)](https://devicelab.vn/kien-thuc/cap-tin-hieu-rs485-chong-nhieu-tieu-chuan-chon/)
- [Đối chiếu thay thế Moxa MGate MB3180, Advantech EKI-1221, USR & 3onedata](https://devicelab.vn/kien-thuc/so-sanh-thay-the-modbus-gateway-moxa-mgate-advantech-usr-3onedata/)
- [Bộ chuyển đổi 4-20mA Analog sang RS485 Modbus & Module Remote I/O](https://devicelab.vn/kien-thuc/bo-chuyen-doi-4-20ma-analog-sang-rs485-remote-io-modbus/)
- [Industrial RS485 to Ethernet Converter Selection Guide (English)](https://devicelab.vn/en/articles/rs485-to-ethernet-converter-selection-guide/)

### 2. Circular 10/2021/TT-BTNMT Environmental Telemetry & SCADA RTU
- [Giải pháp Datalogger quan trắc môi trường tự động chuẩn Thông tư 10/2021/TT-BTNMT](https://devicelab.vn/datalogger-quan-trac-moi-truong-tt10/)
- [Kiến trúc trạm quan trắc nước thải tự động, liên tục & kết nối FTP Sở TN&MT](https://devicelab.vn/kien-thuc/datalogger-quan-trac-nuoc-thai-tu-dong/)
- [Thiết bị Datalogger quan trắc môi trường DL-ENV10 (Datasheet PDF)](https://devicelab.vn/san-pham/dl-env10/)
- [Quy chuẩn nước thải công nghiệp QCVN 40:2025/BTNMT & lộ trình quan trắc tự động](https://devicelab.vn/kien-thuc/quy-chuan-nuoc-thai-cong-nghiep-qcvn-40-quan-trac-tu-dong/)
- [Data logger nhiệt độ đa kênh PT100 (RTD 3 dây) & bộ ghi nhiệt độ công nghiệp](https://devicelab.vn/kien-thuc/data-logger-nhiet-do-da-kenh-pt100-bo-ghi-nhiet-do-cong-nghiep/)
- [Tủ RTU & Thiết bị Remote Terminal Unit SCADA cho nhà máy nước, thủy điện](https://devicelab.vn/kien-thuc/tu-rtu-thiet-bi-remote-terminal-unit-scada-nha-may-nuoc-thuy-dien/)
- [Hệ thống quan trắc nước ngầm tự động giếng khoan chuẩn Nghị định 53/2024/NĐ-CP](https://devicelab.vn/kien-thuc/he-thong-quan-trac-nuoc-ngam-tu-dong/)
- [Giải pháp thay thế Datalogger Campbell Scientific CR1000X / CR300 OEM Việt Nam](https://devicelab.vn/kien-thuc/giai-phap-thay-the-datalogger-campbell-cr1000x-cr300-oem-viet-nam/)
- [Circular 10 Environmental Monitoring Datalogger Solution (English)](https://devicelab.vn/en/environmental-monitoring-datalogger/)

### 3. 3-Phase Power Metering, Solar Zero Export & PLC OEE Telemetry
- [Hệ thống giám sát điện năng nhà máy 3 pha & quản lý năng lượng EMS ISO 50001](https://devicelab.vn/giam-sat-dien-nang-nha-may/)
- [Hướng dẫn chọn đồng hồ đo điện 3 pha RS485 Modbus & thanh ghi chuẩn](https://devicelab.vn/kien-thuc/dong-ho-do-dien-3-pha-rs485-giam-sat-dien-nang/)
- [Bộ điều khiển công suất phát PPC, SmartLogger 3000 & Zero Export SCADA EVN](https://devicelab.vn/kien-thuc/bo-dieu-khien-cong-suat-phat-ppc-smartlogger-3000-zero-export-evn/)
- [Thiết bị thu thập dữ liệu PLC (Siemens, Mitsubishi, Delta) & IoT Gateway](https://devicelab.vn/kien-thuc/thiet-bi-thu-thap-du-lieu-plc-iot-gateway/)
- [Hệ thống giám sát máy móc sản xuất Andon OEE thời gian thực](https://devicelab.vn/kien-thuc/he-thong-giam-sat-may-moc-san-xuat-andon-oee/)

### 4. Custom PCB Design, Turnkey PCBA SMT & Embedded Firmware R&D (Hanoi, Vietnam)
- [Dịch vụ thiết kế mạch điện tử theo yêu cầu & phát triển phần cứng công nghiệp](https://devicelab.vn/thiet-ke-mach-dien-tu/)
- [Công ty thiết kế mạch điện tử tại Hà Nội: Năng lực Lab R&D, EMC & Sản xuất OEM](https://devicelab.vn/kien-thuc/cong-ty-thiet-ke-mach-dien-tu-ha-noi/)
- [Dịch vụ thiết kế PCB 2-8 lớp & vẽ mạch nguyên lý chuẩn IPC-2221](https://devicelab.vn/kien-thuc/dich-vu-thiet-ke-pcb/)
- [Quy trình đặt làm mạch điện tử theo yêu cầu từ EVT/DVT đến sản xuất hàng loạt](https://devicelab.vn/kien-thuc/lam-mach-dien-tu-theo-yeu-cau/)
- [Gia công PCB & hàn mạch điện tử SMT (PCBA) trọn gói tại Việt Nam](https://devicelab.vn/gia-cong-pcb/)
- [Dịch vụ lập trình Firmware nhúng (STM32, ESP32, FreeRTOS, Embedded Linux)](https://devicelab.vn/phat-trien-firmware/)
- [Công ty lập trình nhúng, Firmware & IoT công nghiệp tại Việt Nam](https://devicelab.vn/kien-thuc/cong-ty-lap-trinh-nhung-firmware-iot/)
- [Custom PCB Design & Turnkey Electronics Engineering in Vietnam (English)](https://devicelab.vn/en/custom-pcb-design/)

### 5. Community Engineering Publications (Viblo, Dev.to & Tinh Tế)
- [Viblo: Kỹ thuật chống nhiễu RS485, tính toán Bias & cách ly 2500Vrms](https://viblo.asia/p/ky-thuat-chong-nhieu-rs485-trong-nha-may-tinh-toan-dien-tro-pull-uppull-down-va-cach-ly-quang-2500vrms-bA46807wLKv)
- [Viblo: Kiến trúc Store-and-Forward & Ring-Buffer Flash cho Datalogger Thông tư 10](https://viblo.asia/p/kien-truc-store-and-forward-cho-datalogger-quan-trac-moi-truong-thong-tu-102021tt-btnmt-chong-mat-du-lieu-khi-dut-cap-4g-kNLr3eobVgA)
- [Viblo: Đọc đồng hồ điện 3 pha Selec, Schneider, Eastron qua RS485 & MQTT](https://viblo.asia/p/doc-dong-ho-dien-3-pha-selec-schneider-eastron-qua-modbus-rtu-va-day-mqtt-len-cloud-bang-python-c-OXLA0WqvJGr)
- [Viblo: Checklist 12 điểm kiểm tra Schematic & Layout PCB công nghiệp vượt chuẩn EMC](https://viblo.asia/p/checklist-12-diem-kiem-tra-schematic-layout-pcb-cong-nghiep-truoc-khi-gui-fab-de-vuot-bai-test-emc-iec-61000-4-wd43EXawLX9)
- [Dev.to: Designing Industrial RS485 Circuits for High-EMI Factory Environments](https://dev.to/devicelabvn/designing-industrial-rs485-circuits-for-high-emi-factory-environments-2500vrms-isolation-600w-2114)
- [Dev.to: Store-and-Forward Telemetry Architecture for Environmental Monitoring Dataloggers](https://dev.to/devicelabvn/store-and-forward-telemetry-architecture-for-environmental-monitoring-dataloggers-circular-4b2i)
