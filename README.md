# 🏭 Laporan Produksi
### Industrial Production Reporting using ESP8266 & MQTT

![IoT](https://img.shields.io/badge/IoT-ESP8266-blue?style=plastic&logo=espressif)
![Protocol](https://img.shields.io/badge/Protocol-MQTT-orange?style=plastic&logo=eclipsemosquitto)
![System](https://img.shields.io/badge/System-SCADA-green?style=plastic)
![Status](https://img.shields.io/badge/Status-Active-success?style=plastic)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=plastic)

Industrial **SCADA-based production monitoring system** that collects machine production data using **ESP8266**, sends it via **MQTT**, and displays it on a **real-time production dashboard**.

This system is designed for **Industrial IoT (IIoT)**, **factory automation**, and **production reporting systems**.

---

# 📊 System Overview

Production data flows through the following pipeline:

```
Machine → ESP8266 → MQTT Broker → UI Dashboard → Production Report
```

---

# 🧠 System Architecture

```mermaid
flowchart LR

Machine[Production Machine]
ESP[ESP8266 Controller]
MQTT[MQTT Broker]
UI[Production Dashboard]
DB[(Production Database)]
Report[Reports & Analytics]

Machine -->|Pulse / Sensor Signal| ESP
ESP -->|Publish Data| MQTT
MQTT -->|Subscribe| UI
UI --> DB
DB --> Report
```

---

# ⚙️ Production Data Flow

```mermaid
flowchart TD

Start([Machine Running])

Sensor[Machine Sensor / Pulse Output]
ReadESP[ESP8266 Reads Signal]
Counter[Update Production Counter]
Publish[Publish Data via MQTT]
Broker[MQTT Broker Server]
Dashboard[Production Dashboard UI]
Report[Generate Production Report]

Start --> Sensor
Sensor --> ReadESP
ReadESP --> Counter
Counter --> Publish
Publish --> Broker
Broker --> Dashboard
Dashboard --> Report
Report --> End([Monitoring Complete])
```

---

# 🔁 ESP8266 Firmware Workflow

```mermaid
flowchart TD

Boot([Boot ESP8266])
WiFi[Connect to WiFi]
MQTT[Connect to MQTT Broker]
ReadSignal[Read Machine Signal]
Process[Process & Update Counter]
Publish[Publish Production Data]
Loop{Continue Monitoring?}

Boot --> WiFi
WiFi --> MQTT
MQTT --> ReadSignal
ReadSignal --> Process
Process --> Publish
Publish --> Loop
Loop -->|Yes| ReadSignal
Loop -->|No| End([Stop])
```
---

# 🏗 SCADA Layer Architecture

```
┌─────────────────────────────┐
│     Application Layer       │
│   Production Dashboard UI   │
└──────────────▲──────────────┘
               │
┌──────────────┴──────────────┐
│    Communication Layer      │
│        MQTT Broker          │
└──────────────▲──────────────┘
               │
┌──────────────┴──────────────┐
│        Control Layer        │
│          ESP8266            │
└──────────────▲──────────────┘
               │
┌──────────────┴──────────────┐
│         Field Layer         │
│      Machine Sensors        │
└─────────────────────────────┘
```

---

# 🔧 Hardware Components

| Component | Description |
|------|------|
| ESP8266 | Microcontroller for machine interface |
| Machine Sensor | Pulse / proximity / limit switch |
| Power Supply | 5V regulated |
| WiFi Network | Communication network |
| Industrial Machine | Production equipment |

---

# 💻 Software Stack

| Layer | Technology |
|------|------|
| Firmware | Arduino / ESP8266 SDK |
| Communication | MQTT |
| Broker | Mosquitto / EMQX |
| Backend | C# |
| Database | MySQL |
| UI | VB.NET |

---

# 📡 MQTT Topic Structure

Example topic structure used for machine monitoring.

```
factory/line1/machine1/information
factory/line1/machine1/counter
factory/line1/machine1/operator
```

Example payload:

```json
{
  "uid": "123",
  "count": 350,
  "operator": "mr. x",
  "total":1000,
  "timestamp": "2026-03-13T14:22:00"
}
```
---

# 🔁 ESP8266 Firmware Workflow

```mermaid
flowchart TD

A[Boot ESP8266]
B[Connect WiFi]
C[Connect MQTT Broker]
D[Read Machine Signal]
E[Update Production Counter]
F[Publish MQTT]
G[Repeat Loop]

A --> B
B --> C
C --> D
D --> E
E --> F
F --> G
G --> D
```

---

# 🧾 Example ESP8266 MQTT Publish

```cpp
#include <ESP8266WiFi.h>
#include <PubSubClient.h>

void publishProduction(int count) {

  String payload = "{";
  payload += "\"machine\":\"M01\",";
  payload += "\"count\":" + String(count);
  payload += "}";

  client.publish("factory/machine1/production", payload.c_str());
}
```

---

# 📈 System Features

- Real-time production monitoring
- MQTT-based industrial communication
- Lightweight IoT architecture
- Multi-machine scalability
- Production data logging
- Dashboard visualization

---

# 🏭 Industrial Use Cases

This system can be implemented for:

- Factory production monitoring
- Industrial IoT implementation
- Manufacturing analytics
- Machine utilization tracking
- Smart factory dashboards

---

# 📜 License

[**MIT License**](LICENSE)

---

# 👨‍💻 Author
**STEFFAN U**  
Industrial IoT & Automation Engineering Project  
SCADA • Embedded Systems • MQTT • Factory Automation
