# **NPK-PH-CTH Soil Probe with ESP32 and ESPHome**

This project is an ESPHome configuration for monitoring soil nutrients, pH, conductivity, and temperature using an ESP32 and the NPKPHCTH-S probe. The system supports up to 13 plant profiles, allowing for specific monitoring ranges for various crops.

## **Features**
- **WiFi Connectivity**: Connects to your local WiFi network for easy control and monitoring via Home Assistant.
- **Web Server**: Provides a simple web interface for viewing sensor data and interacting with the ESP32.
- **Touchscreen Display**: Integrated ILI9341 display with touch controls to cycle through plant profiles and view real-time sensor data.
- **Modbus RTU Protocol**: Communicates with the NPKPHCTH-S soil sensor to collect data on nitrogen, phosphorus, potassium, pH, and moisture levels.
- **Home Assistant Integration**: Direct integration with Home Assistant using the ESPHome API.

## **Hardware Requirements**
- **[ESP32 Development Board](https://www.aliexpress.com/item/1005004476867346.html?spm=a2g0o.productlist.main.5.64474350phY2go&algo_pvid=35578a41-f428-4cd3-96b9-76b954324dec&algo_exp_id=35578a41-f428-4cd3-96b9-76b954324dec-2&pdp_npi=4%40dis%21CHF%211.69%211.69%21%21%211.93%211.93%21%402103963717288943888541072eec8c%2112000038614826689%21sea%21CH%212460584479%21X&curPageLogUid=6l2avpHahOaD&utparam-url=scene%3Asearch%7Cquery_from%3A)**: The primary controller of the system.

- **[NPKPHCTH-S Probe](https://www.aliexpress.com/item/1005005684119688.html?spm=a2g0o.productlist.main.1.7efer5Cmr5CmTu&algo_pvid=4df32725-4f5b-43c6-b134-97d7865aa3af&algo_exp_id=4df32725-4f5b-43c6-b134-97d7865aa3af-0&pdp_npi=4%40dis%21CHF%2114.39%2114.39%21%21%2116.44%2116.44%21%402103892f17288941402417999ed281%2112000034003757576%21sea%21CH%212460584479%21X&curPageLogUid=doID3ln0AJII&utparam-url=scene%3Asearch%7Cquery_from%3A)**: Sensor used for measuring nitrogen, phosphorus, potassium, pH, conductivity, and soil moisture.

- **[ILI9341 Touchscreen Display](https://www.aliexpress.com/item/1005006623369442.html?spm=a2g0o.productlist.main.1.142056d8e6lsSN&algo_pvid=64f34e61-3b6a-46ba-9ab7-08aa4c6c99d0&algo_exp_id=64f34e61-3b6a-46ba-9ab7-08aa4c6c99d0-0&pdp_npi=4%40dis%21CHF%215.03%215.03%21%21%2140.70%2140.70%21%402103890917288942386895941e082a%2112000037852145490%21sea%21CH%212460584479%21X&curPageLogUid=UWHplbvOcjdm&utparam-url=scene%3Asearch%7Cquery_from%3A)**: ILI9341 display used to show sensor data and interact with the system.

- **[RS485 to TTL Adapter](https://www.aliexpress.com/item/1005006027343580.html?spm=a2g0o.productlist.main.3.533d49e0J9uHdk&algo_pvid=bdb06bcb-7a54-408d-b9c5-025b5ed0023f&algo_exp_id=bdb06bcb-7a54-408d-b9c5-025b5ed0023f-1&pdp_npi=4%40dis%21CHF%212.08%212.08%21%21%212.38%212.38%21%4021038e6617288943033407003e8f9a%2112000035384149047%21sea%21CH%212460584479%21X&curPageLogUid=dIpR0R6XqHCD&utparam-url=scene%3Asearch%7Cquery_from%3A)**: Used to interface with the Modbus protocol of the NPKPHCTH-S probe.


## **Plant Profiles Supported**

The following plant profiles have been pre-configured in the system. Each plant has optimal ranges for temperature, moisture, pH, conductivity, nitrogen, phosphorus, and potassium levels. These profiles are fully customizable and can be edited to fit your specific plants or growing conditions.

### Pre-configured Profiles:
- **Tomato** (Solanum lycopersicum)
- **Cucumber** (Cucumis sativus)
- **Bell Pepper** (Capsicum annuum)
- **Devil's Ivy** (Epipremnum aureum)
- **Monstera Deliciosa**
- **Olea Europaea** (Olive)
- **Spathiphyllum** (Peace Lily)
- **Drosera Spatulata** (Carnivorous plant)
- **Raspberry** (Rubus idaeus)
- **Strawberry** (Fragaria × ananassa)
- **Lovage** (Levisticum officinale)
- **Mint** (Mentha)
- **Snake Plant** (Sansevieria trifasciata)

### Customization:
You can easily modify these plant profiles or add new ones by adjusting the ranges in the ESPHome configuration. Simply update the min and max values for temperature, moisture, pH, and nutrient levels to match your specific plants.


Each plant profile includes optimal ranges for temperature, moisture, pH, conductivity, nitrogen, phosphorus, and potassium levels.

## **Setup**

### **ESPHome Configuration**
The ESPHome configuration uses various GPIO pins to connect the ESP32 to the display, sensors, and buttons. Refer to the provided `configuration file` for the detailed setup of GPIO pins, sensors, and display configuration.

#### **Wiring Connections**
```yaml
# Display Connections
CLK:       GPIO18  # (SCK/T_CLK)
MOSI:      GPIO23  # (SDI(MOSI)/T_DIN)
MISO:      GPIO19  # (SDO(MISO)/T_DO)
DC:        GPIO05  # (DC)
RESET:     GPIO15  # (RESET)
CS:        GPIO26  # (CS)
LED:       GPIO04  # (LED)
Touch CS:  GPIO17  # (T_CS)

# Button Connections
Button UP:    GPIO02  # UP Button (Next)
Button DOWN:  GPIO03  # DOWN Button (Back)

# Modbus Connections (RS485)
RX:  GPIO32  # UART RX
TX:  GPIO33  # UART TX
```

### **WiFi Settings**
Make sure to add your WiFi credentials in the `secrets.yaml` file:

```yaml
wifi_ssid: "Your WiFi SSID"
wifi_password: "Your WiFi Password"
```

### **Web Server**
You can access the web interface via the IP address assigned to your ESP32 on your local network.

### **OTA Updates**
Over-the-air updates can be performed by adding the OTA password in the secrets.yaml:
```yaml
ota_password: "Your OTA Password"
```
### **Home Assistant Integration**
The system is integrated with Home Assistant through the native ESPHome API, providing real-time sensor data and control over the device.

### **Usage**
Once the ESP32 is powered on and connected to your WiFi network, you can:

View sensor data and cycle through plant profiles on the touchscreen.
Monitor and control the device via Home Assistant or the web server.
Update the ESP32 firmware via OTA (over-the-air) updates.
