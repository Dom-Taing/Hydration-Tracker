# Hydration Tracker (Sensor + Display)

The goal of this product is to track how much water a user drink in a day. The sensor device would be a sleeve that can be worn onto a water bottle, it'll detect the water level in the bottle and convert that into volume of water. The display device would be a box where the gauge will measure if the user reach daily hydration goal. 

**Overall form factor (concept sketch):**
- **Sensor device:** sleeve that can be worn onto a water bottle (water level sensing + BLE)
- **Display device:** small desktop box with a water-drop window and NeoPixel gradient + top button

![Sensor Device](images/sensor_device_detail.jpeg)  
![Physical Features](images/display_physical_features.jpg)  
*The look and form factor of the product*


## Slide 2 — Sensor device (water level + BLE)

![Sensor Device](images/sensor_device_detail.jpeg)  
*The look and form factor of the Sensor device*

It's 4 rod containing the capacitive water level sensor connected with a stretchy fabric to wrap around the bottle.

### How it works
- The sensor device measures water level using a **No Contact Capacitive water level sensor**. 
- The **ESP32-C3** reads the digitized water level, filters noise, computes volume (consumed water), and save the data.
- It then sends updates to the display using **Bluetooth Low Energy (BLE)** when it's connected.

### Key parts (with part numbers)
- **Water sensor**: We'll be building our own using a copper strip + high value resistor + laminated sheets.
- **MCU**: [ESP32C3](datasheets/esp32-c3_datasheet_en.pdf)
- **Battery**: [Lipo Battery](datasheets/C101-_Li-Polymer_503562_1200mAh_3.7V_with_PCM_APPROVED_8.18.pdf)
---

## Slide 3 — Display device (NeoPixel gauge + Wi-Fi + button)

![Display Device](images/display_device_detail.jpeg)  
*The look and form factor of the display device*

### How it works
- The display device runs an **ESP32C3** that:
  1. Connects to the sensor over **BLE** to receive weight/consumption updates
  2. Move the **motor** to reflect current consumption toward daily goal
  3. Updates the **NeoPixel** gauge behind a water-drop window (green→yellow→red)
  4. Syncs daily usage to the cloud over **Wi-Fi** 
  5. Holding the **top button** will tare/calibrate the sensor for an empty bottle

### Key parts (with part numbers)
- **MCU**: [ESP32C3](datasheets/esp32-c3_datasheet_en.pdf)
- **LED gauge**: [XL-5050RGBC-WS2812B](datasheets/WS2812B.pdf)
- **Battery**: [Lipo Battery](datasheets/C101-_Li-Polymer_503562_1200mAh_3.7V_with_PCM_APPROVED_8.18.pdf)
- **Boost regulator**: [TPS61023](datasheets/tps61023.pdf)
- **Button**: [PTS636](datasheets/pts636.pdf)
- **Motor**: [28BYJ-48 – 5V Stepper Motor](datasheets/step-motor-5v-28byj48-datasheet.pdf)
---

## Slide 4 — Communication + system flow (2 figures)

### Figure A: Device communication (block diagram)

![Communication Diagram](images/Communication_diagram.jpg)  
*Diagram displaying how the device communicates*

### Figure B: Detailed data flow (how the system works)

![Communication Diagram](images/System_diagram.jpg)  
*Diagram displaying how the data flows in the system*

---

## Repo structure
- `README.md`
- `images/`
- `datasheets/`
  - (PDFs for each part)
