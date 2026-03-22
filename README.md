# 📡 ESP32 + DHT22 + MQTT + Node-RED Dashboard

<img width="972" height="282" alt="image" src="https://github.com/user-attachments/assets/5b1bd539-ffcf-4b6f-94b6-bbeb9e241038" />

## 📌 Project Description

This project demonstrates how to send **Temperature and Humidity data from DHT22 sensor using ESP32** to an **MQTT broker**, and visualize the data on a **Node-RED Dashboard**.

The ESP32 reads data from the DHT22 sensor and publishes it using MQTT protocol.
Node-RED subscribes to the MQTT topics and displays the values in real-time using gauges and charts.

This project is useful for:

* IoT beginners
* MQTT learning
* Node-RED dashboard projects
* Home automation
* Environmental monitoring
* Embedded + Cloud integration

---

## ⚙️ Technologies Used

* ESP32
* DHT22 Sensor
* MQTT Protocol
* Node-RED
* Node-RED Dashboard
* Arduino IDE
* HiveMQ Public Broker

---

## 📊 Flow Diagram of the Project

<img width="972" height="282" alt="image" src="https://github.com/user-attachments/assets/5b1bd539-ffcf-4b6f-94b6-bbeb9e241038" />

Flow:

```
DHT22 → ESP32 → MQTT Broker → Node-RED → Dashboard UI
```

1. ESP32 reads temperature & humidity
2. ESP32 publishes data to MQTT topics
3. MQTT broker sends data to subscribers
4. Node-RED receives data
5. Dashboard shows live values

---

## 📡 What is MQTT?

MQTT (Message Queuing Telemetry Transport) is a lightweight communication protocol used in IoT.

Features:

* Publish / Subscribe model
* Very low bandwidth
* Fast communication
* Works over internet
* Used in IoT devices

Example in this project:

```
Topic: Temperature
Topic: Humidity
Broker: broker.hivemq.com
Port: 1883
```

ESP32 → Publish
Node-RED → Subscribe

---

## 🧠 What is Node-RED?

Node-RED is a flow-based programming tool used for IoT, automation, and dashboards.

Uses:

* Connect devices
* Process data
* Create dashboards
* MQTT integration
* Cloud integration

Node-RED Dashboard allows:

* Gauges
* Charts
* Buttons
* Switches
* Graphs

---

## Step 1: Install the Required Libraries

Open Arduino IDE

Go to:

```
Tools → Manage Libraries
```

Install:

```
pubsubclient
WiFi
DHT sensor library for ESPx
```

---

## Step 2: Hardware Schematic

DHT22 → ESP32 connection

| DHT22 | ESP32         |
| ----- | ------------- |
| VCC   | 3.3V          |
| GND   | GND           |
| DATA  | GPIO 4        |
| NC    | Not Connected |

Four pin DHT22 sensor is used.

---

## Step 3: Running the program

1. Copy the code to Arduino IDE
2. Select ESP32 board
3. Select COM port
4. Connect ESP32 to USB
5. Upload code
6. Open Serial Monitor
7. Check temperature & humidity values

ESP32 will publish data to MQTT broker.

---

## Step 4: Setup the Node-RED flow

Open Node-RED in browser

```
http://localhost:1880
```

Click:

```
Menu → Manage Palette
```

Search and install:

```
node-red-dashboard
```

Import the flow using the following code

⚠️ Do not change this flow

```
[{"id":"5e04b9dd.81c658","type":"tab","label":"MQTT Dashboard","disabled":false,"info":""},{"id":"235eb13c.0e6e6e","type":"mqtt in","z":"5e04b9dd.81c658","name":"","topic":"Temperature","qos":"2","datatype":"auto-detect","broker":"6ec4dcef.913b24","nl":false,"rap":false,"inputs":0,"x":144,"y":347,"wires":[["7e75f56e.a3ef1c","125d1072.694a2"]]},{"id":"7e75f56e.a3ef1c","type":"debug","z":"5e04b9dd.81c658","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","statusVal":"","statusType":"auto","x":341,"y":314,"wires":[]},{"id":"98d00e19.a6762","type":"mqtt in","z":"5e04b9dd.81c658","name":"","topic":"Humidity","qos":"2","datatype":"auto-detect","broker":"6ec4dcef.913b24","nl":false,"rap":false,"inputs":0,"x":130,"y":120,"wires":[["07048bb50e4963b7","89bc352.e41bac8"]]},{"id":"89bc352.e41bac8","type":"ui_gauge","z":"5e04b9dd.81c658","name":"Humidity","group":"92a9cd27.99b9d","order":0,"width":0,"height":0,"gtype":"gage","title":"Humidity","label":"%","format":"{{value}}","min":0,"max":"100","colors":["#00b3d9","#0073e6","#001bd7"],"seg1":"33","seg2":"66","diff":false,"className":"","x":340,"y":180,"wires":[]},{"id":"125d1072.694a2","type":"ui_chart","z":"5e04b9dd.81c658","name":"Temperature","group":"92a9cd27.99b9d","order":1,"width":0,"height":0,"label":"Temperature","chartType":"line","legend":"false","xformat":"HH:mm","interpolate":"linear","nodata":"","dot":false,"ymin":"","ymax":"","removeOlder":1,"removeOlderPoints":"","removeOlderUnit":"3600","cutout":0,"useOneColor":false,"useUTC":false,"colors":["#1f77b4","#aec7e8","#ff7f0e","#2ca02c","#98df8a","#d62728","#ff9896","#9467bd","#c5b0d5"],"outputs":1,"useDifferentColor":false,"className":"","x":341,"y":374,"wires":[[]]},{"id":"07048bb50e4963b7","type":"debug","z":"5e04b9dd.81c658","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","statusVal":"","statusType":"auto","x":350,"y":100,"wires":[]},{"id":"6ec4dcef.913b24","type":"mqtt-broker","name":"","broker":"broker.hivemq.com","port":"1883","clientid":"","autoConnect":true,"usetls":false,"protocolVersion":"4","keepalive":"15","cleansession":true,"birthTopic":"","birthQos":"0","birthPayload":"","birthMsg":{},"closeTopic":"","closePayload":"","closeMsg":{},"willTopic":"","willQos":"0","willPayload":"","willMsg":{},"userProps":"","sessionExpiry":""},{"id":"92a9cd27.99b9d","type":"ui_group","name":"Temperature and Humidity","tab":"6f670e80.d2e0f","order":1,"disp":true,"width":"6","collapse":false,"className":""},{"id":"6f670e80.d2e0f","type":"ui_tab","z":"5e04b9dd.81c658","name":"Dashboard","icon":"dashboard"}]
```

---

## Step 5: Deploy the flow

Click:

```
Deploy
```

Open dashboard:

```
http://localhost:1880/ui
```

or

```
http://<your IP address>:1880/ui
```

You will see:

* Temperature chart
* Humidity gauge
* Live data

---

## ✅ Output

* Real-time temperature
* Real-time humidity
* MQTT communication working
* Node-RED dashboard working

---

## ⭐ Features

* Real-time IoT dashboard
* MQTT communication
* ESP32 WiFi
* Node-RED UI
* Public broker support
* Beginner friendly
