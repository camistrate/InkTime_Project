
## Block Diagram

<img width="1523" height="894" alt="image" src="https://github.com/user-attachments/assets/5340bdfd-afd2-4f2b-b96d-39719dbfa883" />

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

