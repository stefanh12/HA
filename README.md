# HA
home assistant and esphome configurations.

# vinden Temp

📌 Vinden Risk Sensor for ESPHome
This project provides an ESPHome template sensor that calculates a risk index for attic moisture based on temperature and humidity readings. It uses a predefined lookup table and logic adapted from a Python script.
✅ Features

Calculates a risk level (0–3) based on temperature and humidity.
Provides:

Numeric sensor (vinden_risk) for automations.
Text sensor (Vinden Risk Level) showing Low, Medium, High, or Critical.


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

Monitors pH, ORP, and temperature sensors.
Controls two EZO peristaltic pumps (chlorine & acid).
Includes calibration buttons for pH and ORP sensors.
Provides dosing controls (volume, duration, cleaning).
Displays pump states, dosing modes, and calibration status.

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

Power On/Off
Working modes: Silent, Smart, Powerfull
Set temperature (18°C – 40°C)


Readings:

Water temperature (in/out)
Ambient temperature
Pipe temperatures
Compressor speed, EEV actual, and other internal parameters


Modbus Communication:

Custom write lambdas for coils and holding registers
Periodic re-send of coil state for reliability



⚠ Beta Notice
This code is under testing. Basic functions (On/Off, mode selection, setpoint, water temps) are working.
Advanced registers and unknown addresses are still being mapped.

# Pool Filter Tryck
🔍 Pool Filter Pressure Sensor
This ESPHome configuration uses an analog pressure sensor, a logic level converter, and an ADS1115 ADC to measure the filter pressure in a pool system.
It helps determine when to backwash the filter or detect if the pump is running dry.
✅ Features

Reads pressure via ADS1115 on I²C.
Converts raw voltage to PSI using linear calibration.
Filters out noise and invalid readings.
Includes Wi-Fi info and uptime sensors for diagnostics.
