# home assistant and esphome configurations.
Collection of esphome and Node Red configurations for Home Assistant that I use to make my life easier
# vinden Temp

📌 Vinden Risk Sensor for ESPHome
This project provides an ESPHome template sensor that calculates a risk index for attic moisture based on temperature and humidity readings. It uses a predefined lookup table and logic adapted from a Python script.
✅ Features

Calculates a risk level (0–3) based on temperature and humidity.
Provides:

- Numeric sensor (vinden_risk) for automations.
- Text sensor (Vinden Risk Level) showing Low, Medium, High, or Critical.


Handles unavailable state gracefully by returning "Unavailable".
Includes Home Assistant-friendly icons for better dashboard integration.
Easy to customize and integrate with other ESPHome YAML files.

🔗 Use Cases

Monitor attic conditions to prevent mold or moisture damage.
Trigger alerts or automations when risk level is high.

# labcom.cloud.json
node-red flow for getting the measurements for one accountid(currently) and adding the measurements as sensors to home assistant. Depends on 
- node-red-contrib-graphql
- node-red-contrib-home-assistant-websocket

The auth token will need to be generated for your account, see https://labcom.cloud/pages/user-setting. Place the token in customHeaders.Authorization node in the flow.

# Pool Enzo
🏊 Atlas Scientific Pool Controller
ESPHome configuration for Atlas Scientific Wi-Fi Pool Kit with EZO dosing pumps for chlorine and acid.
✅ Features

- Monitors pH, ORP, and temperature sensors.
- Controls two EZO peristaltic pumps (chlorine & acid).
- Includes calibration buttons for pH and ORP sensors.
- Provides dosing controls (volume, duration, cleaning).
- Displays pump states, dosing modes, and calibration status.

⚠ Important Note
You may need to ground the system to earth for accurate pH readings:

Drive an earth rod into the ground.
Connect the rod to the GND pin on the I²C connector for the pumps.

🔗 Hardware Links

https://atlas-scientific.com/peristaltic/ezo-pmp/
https://atlas-scientific.com/kits/wi-fi-pool-kit/

# Brilix Heat Pump
❄️ Brilix Heat Pump Modbus Control (Beta)
This ESPHome configuration integrates with the BRILIX inverBOOST XHPFDPLUS 100 E 9kW R32 (Alsavo) heat pump via Modbus RTU over RS485 using a LilyGO T-CAN485 board.
✅ Features

Control Functions:

- Power On/Off
- Working modes: Silent, Smart, Powerfull
- Set temperature (18°C – 40°C)


Readings:

- Water temperature (in/out)
- Ambient temperature
- Pipe temperatures
- Compressor speed, EEV actual, and other internal parameters


Modbus Communication:

- Custom write lambdas for coils and holding registers
- Periodic re-send of coil state for reliability



⚠ Beta Notice
This code is under testing. Basic functions (On/Off, mode selection, setpoint, water temps) are working.
Advanced registers and unknown addresses are still being mapped.

# Pool Filter Tryck
🔍 Pool Filter Pressure Sensor
This ESPHome configuration uses an analog pressure sensor, a logic level converter, and an ADS1115 ADC to measure the filter pressure in a pool system.
It helps determine when to backwash the filter or detect if the pump is running dry.
✅ Features

- Reads pressure via ADS1115 on I²C.
- Converts raw voltage to PSI using linear calibration.
- Filters out noise and invalid readings.
- Includes Wi-Fi info and uptime sensors for diagnostics.

# Pool Pump Vario
⚡ iSaver Pool Pump Speed Control (ESP32)
This ESPHome configuration controls an AquaForte/iSaver variable-speed pool pump using GPIO relays to select preset RPM speeds (e.g., 1200, 2400, 2900) and On/Off functionality.
✅ Features

Relay-based control for:

- pump on/off
- pump 1200 RPM
- pump 2400 RPM
- pump 2900 RPM


Uses ESP32 GPIO pins for relay switching.
Includes Wi-Fi info and uptime sensors for diagnostics.
Compatible with Home Assistant automations.

🔗 Hardware & Documentation

https://www.allswimltd.com/pdf/iSAVER-Inverter-Instructions.pdf
https://www.upesy.com/blogs/tutorials/esp32-pinout-reference-gpio-pins-ultimate-guide
https://www.poolpowershop-forum.de/forum/thread/1145763-wie-steuert-man-eine-aqua-forte-1100-drehzahlregelung-extern-an/?pageNo=3


# IVT Relay ventilation controller
🔌 IVT VBX Relay Controller (ESP8266)
This ESPHome configuration controls a DollaTek 5V ESP8266 four-channel relay board via UART commands. It is designed for applications like IVT VBX ventilation control or other multi-voltage switching scenarios.
✅ Features

- Mode Selector (0V, 115V, 135V, 150V, 180V) using a select component.
- Automatically switches relays based on selected mode.
- UART-based relay control with custom byte sequences.
- Includes Wi-Fi info and uptime sensors for diagnostics.

# IVT 490 Twin
https://github.com/stefanh12/IVT_490_esphome

# Garage port
🚪 Garage Door Controller with Alarm Integration (ESPHome)
This project configures an ESP8266-based Shelly 1 (or similar) to control a garage door opener using ESPHome, with added safety logic to prevent opening the door when the home alarm is armed.
✅ Features

- Garage Door Control
Implements a cover entity in Home Assistant for open/close actions.
Uses a relay to send a short pulse (0.5s) to the garage door opener.
- Door State Detection
Reads a contact sensor connected to the Shelly SW input to determine if the door is open or closed.
- Alarm Integration
Checks the state of a Home Assistant alarm entity (alarm_control_panel.verisure_alarm) before opening the door.
If the alarm is armed, the open action is blocked, and an event is sent to Home Assistant.
- Wi-Fi & OTA Updates
Static IP configuration for reliable connectivity.
OTA updates enabled for easy firmware management.




✅ Safety Logic

Open Action:

- Only triggers if the alarm state is disarmed.
Otherwise, logs a warning and sends an HA event (esphome.garageport_open_when_armed).


Close Action:

- Always allowed for security reasons.



✅ Hardware Requirements

- ESP8266 board (e.g., Shelly 1 or ESP-01)
- Relay connected to GPIO4
- Contact sensor connected to GPIO5

✅ Home Assistant Integration

- Creates a cover entity named Garage Door.
- Uses device_class: garage for proper UI representation.
- Integrates with Verisure alarm entity for conditional logic.
