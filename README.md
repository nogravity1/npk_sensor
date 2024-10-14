NPK-PH-CTH Soil Probe with ESP32 and ESPHome
This project is an ESPHome configuration for monitoring soil nutrients, pH, conductivity, and temperature using an ESP32 and the NPKPHCTH-S probe. The system supports up to 13 plant profiles, allowing for specific monitoring ranges for various crops.

Features
WiFi Connectivity: Connects to your local WiFi network for easy control and monitoring via Home Assistant.
Web Server: Provides a simple web interface for viewing sensor data and interacting with the ESP32.
Touchscreen Display: Integrated ILI9341 display with touch controls to cycle through plant profiles and view real-time sensor data.
Modbus RTU Protocol: Communicates with the NPKPHCTH-S soil sensor to collect data on nitrogen, phosphorus, potassium, pH, and moisture levels.
Home Assistant Integration: Direct integration with Home Assistant using the ESPHome API.
Hardware Requirements
ESP32 Development Board: The primary controller of the system.
NPKPHCTH-S Probe: Sensor used for measuring nitrogen, phosphorus, potassium, pH, conductivity, and soil moisture.
ILI9341 Touchscreen Display: Displays sensor data and allows interaction with buttons.
RS485 to TTL Adapter: Used to interface with the Modbus protocol of the NPKPHCTH-S probe.
Plant Profiles Supported
Tomato
Cucumber
Bell Pepper
Devil's Ivy
Monstera Deliciosa
Olea Europaea (Olive)
Spathiphyllum (Peace Lily)
Drosera Spatulata
Raspberry
Strawberry
Lovage
Mint
Snake Plant
Each plant profile includes optimal ranges for temperature, moisture, pH, conductivity, nitrogen, phosphorus, and potassium levels.

Setup
ESPHome Configuration
The ESPHome configuration uses various GPIO pins to connect the ESP32 to the display, sensors, and buttons. Refer to the provided configuration file for the detailed setup of GPIO pins, sensors, and display configuration.

Wiring Connections
Display:
CLK: GPIO18
MOSI: GPIO23
MISO: GPIO19
DC: GPIO05
RESET: GPIO15
CS: GPIO26
LED: GPIO04
Touch CS: GPIO17
Buttons:
UP: GPIO02
DOWN: GPIO03
Modbus:
RX: GPIO32
TX: GPIO33
WiFi Settings
Make sure to add your WiFi credentials in the secrets.yaml file:
wifi_ssid: "Your WiFi SSID"
wifi_password: "Your WiFi Password"
Web Server
You can access the web interface via the IP address assigned to your ESP32 on your local network.

OTA Updates
Over-the-air updates can be performed by adding the OTA password in the secrets.yaml:
ota_password: "Your OTA Password"
Home Assistant Integration
The system is integrated with Home Assistant through the native ESPHome API, providing real-time sensor data and control over the device.

Usage
Once the ESP32 is powered on and connected to your WiFi network, you can:

View sensor data and cycle through plant profiles on the touchscreen.
Monitor and control the device via Home Assistant or the web server.
Update the ESP32 firmware via OTA (over-the-air) updates.
License
This project is open-source and licensed under the MIT License.
