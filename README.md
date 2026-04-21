# TSC-homework - Istrate Camelia-Elena 334CC
# InkTime Watch

## Block Diagram

<img width="1523" height="894" alt="image" src="https://github.com/user-attachments/assets/5340bdfd-afd2-4f2b-b96d-39719dbfa883" />

## Bill of Materials (BOM)

The table below lists the main active components, connectors, and critical electromechanical parts used in the design. Standard passives, RF matching parts, and decoupling capacitors are included in the manufacturing BOM.

| Component / Module | Function | Package / Footprint | JLC / LCSC Part | Datasheet |
|---|---|---|---|---|
| **nRF52840-QIAA-R** | Main BLE MCU | aQFN73 (7x7) | [C190794](https://jlcpcb.com/partdetail/NordicSemicon-NRF52840_QIAAR/C190794) | [Nordic nRF52840 Product Specification](https://docs.nordicsemi.com/) |
| **BQ25180YBGR** | LiPo charger / power-path management | DSBGA-9 | [C3682423](https://jlcpcb.com/partdetail/TexasInstruments-BQ25180YBGR/C3682423) | [TI BQ25180 Datasheet](https://www.ti.com/lit/ds/symlink/bq25180.pdf) |
| **RT6160AWSC** | 3.3V buck-boost regulator | WLCSP-15 | [C7065276](https://jlcpcb.com/partdetail/Richtek_Tech-RT6160AWSC/C7065276) | [Richtek RT6160A Datasheet](https://www.richtek.com/assets/product_file/RT6160A/DS6160A-05.pdf) |
| **MAX17048G+T10** | 1-cell LiPo fuel gauge | DFN-8 (2x2) | [C2682616](https://jlcpcb.com/partdetail/AnalogDevices-MAX17048G_T10/C2682616) | [MAX17048 / MAX17049 Datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/MAX17048-MAX17049.pdf) |
| **BMA421** | IMU / motion sensing / step counter | LGA-12 (2x2) | [C5242966](https://jlcpcb.com/partdetail/Bosch_Sensortec-BMA421/C5242966) | [Bosch BMA421 Datasheet](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bma421-ds004.pdf) |
| **DRV2605YZFR** | Haptic driver for ERM motor | VSSOP-10 / DSBGA-9 variant used in sources | [C81079](https://jlcpcb.com/partdetail/TexasInstruments-DRV2605YZFR/C81079) | [TI DRV2605 Datasheet](https://www.ti.com/cn/lit/ds/symlink/drv2605.pdf) |
| **2450AT18B100E** | 2.4 GHz chip antenna | SMD 3216 / 1206 class | [C5179427](https://jlcpcb.com/partdetail/Johanson_Technology-2450AT18B100E/C5179427) | [Johanson 2450AT18B100E Datasheet](https://www.johansontechnology.com/datasheets/2450AT18B100/2450AT18B100.pdf) |
| **USBLC6-2SC6Y** | USB ESD protection | SOT-23-6 | [C7519](https://jlcpcb.com/partdetail/Stmicroelectronics-USBLC6_2SC6Y/C7519) | [ST USBLC6-2 Datasheet](https://www.st.com/resource/en/datasheet/usblc6-2.pdf) |
| **KH-TYPE-C-16P** | USB Type-C connector | 16-pin SMD | [C2765186](https://jlcpcb.com/partdetail/Kinghelm-KH_TYPE_C_16P/C2765186) | [Kinghelm KH-TYPE-C-16P Datasheet](https://datasheet.lcsc.com/lcsc/2012121836_Kinghelm-KH-TYPE-C-16P_C2765186.pdf) |
| **503480-2400** | 24-pin 0.5 mm FPC connector for E-paper display | 24-pin FPC | [C2857168](https://jlcpcb.com/partdetail/Molex-5034802400/C2857160) | [Molex 503480-2400 Datasheet](https://www.molex.com/en-us/products/part-detail/5034802400) |
| **DMG2305UX** | P-channel MOSFET for E-paper power control | SOT-23 | [C2940629](https://jlcpcb.com/partdetail/TECHPUBLIC-DMG2305UX/C2940629) | [DMG2305UX Datasheet](https://www.diodes.com/assets/Datasheets/DMG2305UX.pdf) |
| **SI1308EDL-T1-GE3** | MOSFET used in display drive stage | SOT-23 | [C469327](https://jlcpcb.com/partdetail/VishayIntertech-SI1308EDL_T1GE3/C469327) | [SI1308EDL Datasheet](https://www.vishay.com/doc?63399) |
| **MBR0530** | Schottky diode used in E-paper pump circuit | SOD-123 | [C77336](https://jlcpcb.com/partdetail/78464-MBR0530/C77336) | [MBR0530 Datasheet](https://www.onsemi.com/pdf/datasheet/mbr0530t1-d.pdf) |
| **EVP-AKE31A / tactile switch** | User input buttons | SMD tactile | [C2845028](https://jlcpcb.com/partdetail/Panasonic-EVP_AKE31A/C2845028) | [Panasonic Tactile Switch Datasheet](https://industrial.panasonic.com/cdbs/www-data/pdf/ATV0000/ATV0000CE3.pdf) |
| **LCM1027B3605F** | Vibration motor | Wire leads | [C7528806](https://jlcpcb.com/partdetail/7528806-LCM1027B3605F/C7528806) | [LCM1027B3605F Datasheet](https://datasheet.lcsc.com/lcsc/2310131633_LCM-LCM1027B3605F_C7528806.pdf) |
| **TC2030-IDC** | SWD programming / debug interface | Tag-Connect 6-pin footprint | [Tag-Connect Product Page](https://www.tag-connect.com/product/tc2030-idc-nl) | [TC2030 Documentation](https://www.tag-connect.com/product/tc2030-idc-6-pin-tag-connect-plug-of-nails-spring-pin-cable-with-ribbon-connector) |
| **32 MHz Crystal** | Main high-frequency crystal for nRF52840 | 2016 | [C5265841](https://jlcpcb.com/partdetail/Huiyuancrystal-HY32MSMD2016CA1R30/C5265841) | [32 MHz Crystal Datasheet](https://www.lcsc.com/product-detail/C7275071.html) |
| **32.768 kHz Crystal** | Low-frequency RTC crystal | 3215 | [C70509](https://jlcpcb.com/partdetail/NDK-NX3215SA_32_768KHZ_EXS00AMU00466/C70509) | [32.768 kHz Crystal Datasheet](https://ro.mouser.com/ProductDetail/NDK/NX3215SA-32.768K-STD-MUS-2) |
| **E-Paper Display 1.54 inch** | Main display module | 24-pin FPC | [C359944](https://jlcpcb.com/partdetail/Waveshare-4_2inch_e_PaperModule/C359944) | [WSH-12561 Datasheet](https://www.tme.eu/Document/0ca57a8ffbcd57b5bca53252eb9d6ec3/WSH-12561.pdf) |
| **LiPo Battery 250 mAh** | Main energy storage | Battery pack | - | [AKY0106 Datasheet](https://www.tme.eu/Document/b9e12bf26ad0ba929a22ab5d58f022cd/AKY0106.pdf) |

## Hardware Description

### MCU - nRF52840

The **nRF52840** is the central processing unit of the system. It integrates:

* ARM Cortex-M4F running at 64 MHz with FPU
* Bluetooth Low Energy (BLE 5.0)
* USB 2.0 Full Speed interface
* 1 MB Flash / 256 KB RAM

All major peripherals are connected directly to the nRF52840 through SPI, I2C, and GPIO interfaces.

---

## Power Path

```text
USB-C --> BQ25180 (charger) --> LiPo battery
                             --> VSYS
VSYS --> RT6160 (buck-boost) --> 3.3V rail (VDD_3V3)
```

### BQ25180

The **BQ25180** is used as the battery charger and power-path management IC. It:

* charges the LiPo battery
* provides the system rail (VSYS)
* communicates with the MCU over I2C
* raises an interrupt for charger or fault events

### RT6160

The **RT6160** is the main buck-boost regulator. It converts VSYS to a stable **3.3V rail**, which powers:

* the nRF52840
* the sensors
* the display logic
* the haptic driver

### MAX17048

The **MAX17048** is used as a fuel gauge. It monitors battery voltage and state of charge and communicates with the MCU over I2C. It also provides an **ALERT** signal for low-battery or battery-status events.

---

## E-Paper Display

The e-paper display is controlled through SPI and additional GPIO control signals.

| Signal   | Direction     | Description           |
| -------- | ------------- | --------------------- |
| SCK      | MCU → Display | SPI clock             |
| MOSI     | MCU → Display | SPI data              |
| EPD_CS   | MCU → Display | Chip select           |
| EPD_DC   | MCU → Display | Data / Command select |
| EPD_RST  | MCU → Display | Display reset         |
| EPD_BUSY | Display → MCU | Busy/status signal    |

The display power circuit includes:

* inductors
* Schottky diodes
* MOSFET switching elements

This stage generates the voltages required by the e-paper panel, such as **PREVGH** and **PREVGL**.

---

## IMU - BMA421

The **BMA421** is the motion sensor used in the design.

* Interface: **I2C**
* Functions:

  * acceleration sensing
  * motion detection
  * step-related events
* Interrupt outputs:

  * **INT1**
  * **INT2**

---

## Haptic Driver - DRV2605

The **DRV2605** is used to drive the vibration motor.

* Interface: **I2C**
* Enable signal: **HAPTIC_EN**
* Function: haptic feedback generation

---

## USB Interface

The board uses a **USB Type-C connector** together with an **USBLC6-2SC6Y** ESD protection device.

Signals:

* **VBUS**
* **D+**
* **D-**

This interface is used for:

* charging input
* USB detection by the MCU

---

## RF and Antenna

A **2450AT18B100E 2.4 GHz chip antenna** is connected to the RF output of the nRF52840.

The RF section includes:

* matching network components
* antenna keepout area
* no copper/traces under the antenna region

---

## User Interface

The design includes three push buttons:

* Up
* Down
* Enter / Esc

These are connected to GPIO pins of the MCU and used as active-low digital inputs.

---

## Debug Interface

Programming and debugging are performed through the **TC2030 SWD interface**, using:

* SWDIO
* SWDCLK
* RESET
* SWO
* 3.3V
* GND

---

## nRF52840 Pin Mapping

### Shared I2C Bus

* **P0.06** - SDA
  Used for communication with:

  * BMA421
  * MAX17048
  * BQ25180
  * RT6160
  * DRV2605

* **P0.07** - SCL
  Shared I2C clock line for all I2C peripherals

### SPI Bus (E-Paper Display)

* **P0.02** - SCK
* **P0.03** - MOSI
* **P0.05** - EPD_CS
* **P0.15** - EPD_DC
* **P0.16** - EPD_RST
* **P0.17** - EPD_BUSY

### Display Power Control

* **P1.01** - PFET gate control for display power enable

### Interrupts and Peripheral Control

* **P0.08** - BMA421 INT1
* **P1.08** - BMA421 INT2
* **P0.10** - MAX17048 ALERT
* **P0.11** - BQ25180 PMIC interrupt
* **P0.12** - DRV2605 enable

### Buttons

* **P0.13** - Up button
* **P0.14** - Down button
* **P1.00** - Enter / Esc button

### USB

* **D+** - USB data positive
* **D-** - USB data negative
* **VBUS** - USB power detection

### RF

* **ANT** - connected to the 2.4 GHz antenna through the matching network

### Debug and Clocks

* **SWDIO** - debug data
* **SWDCLK** - debug clock
* **RESET** - hardware reset
* **SWO** - debug trace output
* **XC1 / XC2** - 32 MHz crystal
* **XL1 / XL2** - 32.768 kHz crystal

---

## Design Rationale for Pin Selection

The selected pins were chosen to:

* use dedicated hardware interfaces for I2C and SPI
* keep related signals grouped logically
* simplify PCB routing
* support interrupt-driven operation for low-power behavior
* provide a clean debug and programming interface

---

## Power Consumption Considerations

The hardware is designed for low-power operation:

* **nRF52840** supports sleep and low-power modes
* **E-paper display** only consumes significant power during refresh
* **BMA421** is a low-power motion sensor
* **DRV2605 + motor** draw higher current only during short haptic events

Power efficiency is improved by:

* enabling only the peripherals that are needed
* using a regulated 3.3V rail
* controlling display-related power stages separately


## PCB Top View
<img width="1301" height="995" alt="image" src="https://github.com/user-attachments/assets/8c29f26a-2f69-4ea7-9701-aaf8c5347d34" />


## 3D PCB Render
<img width="1730" height="1071" alt="image" src="https://github.com/user-attachments/assets/9f602845-7f0a-4885-ba5c-ade7dfb72cb7" />



