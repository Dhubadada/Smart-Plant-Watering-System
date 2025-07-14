# 🌱 Smart Plant Watering System with NodeMCU ESP8266 and Blynk IoT

<img width="500" height="500" alt="ChatGPT Image Jul 14, 2025, 03_23_59 PM" src="https://github.com/user-attachments/assets/2bf91d4b-c45c-4787-822d-deddbd8f832f" />


An automated plant watering system with real-time soil monitoring and remote control via Blynk IoT platform.

## 📋 Features
- Real-time soil moisture percentage display
- Manual/automatic pump control
- LCD local interface
- Remote monitoring via Blynk web/mobile apps
- Low-water alerts (optional)

## 📦 Hardware Components
| Component | Quantity |
|-----------|----------|
| NodeMCU ESP8266 | 1 |
| Capacitive Soil Moisture Sensor | 1 |
| 5V Relay Module | 1 |
| 16x2 LCD with I2C | 1 |
| DC Water Pump (3-6V) | 1 |
| Breadboard | 1 |
| Jumper Wires | 10+ |
| 9V Battery + Connector | 1 |

## 🔌 Circuit Diagram & Connections

### Wiring Diagram
![Circuit Diagram](https://i.imgur.com/CircuitDiagram.png)

### Connection Table
| NodeMCU | Connected To |
|---------|-------------|
| 3.3V    | Soil Sensor VCC, LCD VCC |
| GND     | Soil Sensor GND, Relay GND, LCD GND |
| A0      | Soil Sensor OUT |
| D1 (GPIO5) | LCD SCL |
| D2 (GPIO4) | LCD SDA |
| D3 (GPIO0) | Relay IN |
| Vin      | Relay VCC |

> 💡 **Note:** Use a separate power source (9V battery) for the water pump connected through the relay.

## 🛠️ Setup Process

### 1. Hardware Assembly
1. Place NodeMCU on breadboard
2. Connect soil sensor:
   - VCC → 3.3V
   - GND → GND
   - OUT → A0
3. Connect relay:
   - VCC → Vin (5V)
   - GND → GND
   - IN → D3
4. Connect LCD via I2C:
   - SDA → D2
   - SCL → D1

### 2. Blynk IoT Dashboard Setup
1. Go to <img width="1332" height="553" alt="image" src="https://github.com/user-attachments/assets/7fc5cccf-2bb9-4327-98f3-be90396f8731" />

2. Create new template:
   - Name: "PlantWaterSystem"
   - Hardware: ESP8266
   - Connection: WiFi

#### Datastreams Configuration:
| Virtual Pin | Name | Type | Values |
|------------|------|------|--------|
| V0 | Moisture | Integer | 0-100% |
| V1 | Pump Control | Integer | 0-1 |

#### Web Dashboard:
![Blynk Web Dashboard](https://i.imgur.com/WebDashboard.png)
- Add SuperChart widget for moisture history
- Add Button widget for manual control
- Add Label widget for status display

#### Mobile Dashboard:
![Blynk Mobile Dashboard](https://i.imgur.com/MobileDashboard.jpg)

### 3. Uploading the Code
1. Install required libraries:
   ```bash
   ESP8266 Board Package (Arduino IDE)
   Blynk Library v1.0.1+
   LiquidCrystal_I2C


## 📝 License
This project is open-source and available under the [MIT License](LICENSE).
