j 
 <h1 style="font-size1000px" >(っ◔◡◔)っ <img width="45" height="45" alt="image-from-rawpixel-id-6430893-png" src="https://github.com/user-attachments/assets/68af7046-94d3-46a5-a16d-fc9388d49aa5" />      PLASMAGUN PROJECT    </h1>




<img width="600" alt="1000024354" src="https://github.com/user-attachments/assets/19702215-c316-4260-9b29-5c45209e333a"/>

<img width="600" alt="1000024356" src="https://github.com/user-attachments/assets/0dc1ed63-f333-4d11-83e5-2400e4c28d3e" />






  This repository contains the **Arduino source code** and **sound files** for the **Plasmagun Project**.
 
 I've also made a **YouTube tutorial**, where I show you **how to build the device step by step**. Some **electronics parts are briefly explained**, but the main focus is on **the building process**.

---

## <img width="35" height="38" alt="Youtube_logo" src="https://github.com/user-attachments/assets/b3975ed4-adde-4141-aac9-945f6a37d26c" /> YouTube Tutorial

👉 [**Watch the tutorial on YouTube**](https://www.youtube.com/@LyTack)

---

## 📂 What’s Inside

* 	 <img width="17" height="17" alt="arduino-1-logo-png-transparent" src="https://github.com/user-attachments/assets/4795ee23-0323-4f13-8065-d5c10e393d4f" />​​ 	**Arduino Code** – Clean, structured code with helpful comments
* **🔊 DFPlayer Mini Sounds** – All required audio files
* **🧠 Simple Logic** – Easy to understand and modify

---

## 🧰 Required Arduino Libraries

Please install the following libraries in the Arduino IDE before uploading the code:

| Library               | Source/Note                                         |
| --------------------- | --------------------------------------------------- |
| `Wire`                | Built-in                                            |
| `Adafruit SSD1306`    | By Adafruit                                         |
| `Adafruit GFX`        | By Adafruit                                         |
| `DFRobotDFPlayerMini` | By DFRobot                                          |
| `SoftwareSerial`      | Built-in                                            |
| `elapsedMillis`       | By Paul Stoffregen                                  |
| `Adafruit BMP280`     | By Adafruit                                         |
| `Adafruit BusIO`      | Needed for BMP280                                   |
| `AHT20`               | By Adafruit (or compatible)                         |
| `TFLI2C`              | Benewake TFMini LiDAR Library *(available as .zip)* |

---

## 🚀 How to Run the Code

1. **Install the Arduino IDE**
   👉 [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)

2. **Prepare the IDE**
   Go to **File → Preferences** and enable:

   * ✅ Line Numbers
   * ✅ Verbose Output (optional, for debugging)

3. **Install Libraries**
   Open **Tools → Manage Libraries...** and install the libraries listed above.

4. **Load the Code**
   Copy the Arduino code from this repository into the IDE.

5. **Prepare the Sounds**
   Copy the entire `mp3` folder onto a **FAT32 formatted microSD card**.

6. **Insert the microSD card into the DFPlayer Mini.**

7. **Connect your Arduino via USB.**

8. **Select your board and COM port:**

   * **Tools → Board** → Choose your Arduino model (e.g., Uno, Nano)
   * **Tools → Port** → Select the correct COM port

9. **Upload the code**
   Press **Upload** (🔼) and wait until the transfer is complete.

---

## ⚠️ Important Notes

* The code works **out of the box**.
* Make sure the `mp3` folder is correctly placed on the microSD card.
* Insert the card into the **DFPlayer Mini** before running the system.

 ---

## 📄 Sensor Display Information

Below you can see the OLED display with the labeled values:

<img src="https://github.com/user-attachments/assets/c652e7e1-88e7-44a1-b77f-e458fdefe945" alt="1000024348" width="450">

**1. Temperature (°C / °F)**  
   Displays the chamber temperature. By default in Celsius, but you can convert to Fahrenheit with the code:

   ```cpp
   float temperatureF = temperature * 9.0 / 5.0 + 32;
   display.setCursor(2, 0);
   display.print(temperatureF, 1);
   display.print("F ");

   ```

**2. Humidity (%)**
   I have observed the following behavior inside the chamber:

   * The lower the humidity value, the louder the ignition sound.
   * Ignition will not occur if humidity exceeds \~80% RH.
   * After ignition, humidity spikes to 100% and then quickly drops again during the cooldown phase.


**3. Distance (m)**  
   Displays the measured distance in meters.  
   - Maximum range: ~8 meters.

 ---

## 📊 Technical Parameters

**Total weight:**  
5.177 lb (pounds)  
2.348 kg (kilograms)  
2348.4 g (grams)  

###  Plasma Cannon – Combustion Chamber

| Parameter | Value / Range | Unit |
|-----------|---------------|------|
| Gas mixture | H₂ + O₂ (usually 2:1, sometimes 1:1) + <9% C₃H₈ + <2% C₂H₂ | – |
| Ambient pressure | ~14.5 (1) | PSI (bar) |
| Operating pressure in chamber (pre-ignition) | Ambient pressure | – |
| Short pressure spike | 290 – 435 (17 – 21) | PSI (bar) |
| Pressure drop after explosion | <5 ms to ~14.5 (1) | PSI (bar) |
| Pressure pulse duration | 1 – 5 | ms |
| Max. temperature (ignition point) | 3200 – 3600 (1760 – 1980) | °F (°C) |
| Duration >2730 °F (1500 °C) | ~1 – 2 | ms |
| Total duration >930 °F (500 °C) | ~10 – 20 | ms |
| PVC melting point (inner chamber) | 167 – 221 (75 – 105) | °F (°C) |
| PVC softening point (inner chamber) | ~176 – 194 (80 – 90) | °F (°C) |
| Time to deformation (chamber) | >100 | ms |
| Thermal conductivity (inner wall) | ~0.104 (0.18) | BTU/(h·ft·°F) (W/(m·K)) |
| Gas volume expansion | 4 – 8× initial volume | – |
| Flashback risk | High | – |
| Max. cycles without maintenance | 146 | Ignitions |
| Heat exposure <2 ms at >3630 °F (2000 °C) | No deformation | – |
| Heat exposure >110 ms at >176 °F (80 °C) | Deformation | – |

---

###  Plasma Cannon – Hose 16×12 mm

| Parameter | Value / Range | Unit |
|-----------|---------------|------|
| Pressure | 87 – 130 (6 – 9) | PSI (bar) |
| Pressure pulse duration | 8.2 – 8.7 | ms |
| Temperature in hose center | ~752 – 1112 (400 – 600) | °F (°C) |
| Temperature at hose exit | ~212 – 302 (100 – 150) | °F (°C) |
| Duration >932 °F (500 °C) inside hose | <5 | ms |
| Gas volume expansion in hose | 8 – 9× initial volume | – |
| Gas flow velocity inside hose | ~112 – 268 (50 – 120) | ft/s (m/s) |

---

###  Plasma Cannon – Exit / Muzzle

| Parameter | Value / Range | Unit |
|-----------|---------------|------|
| End pressure at exit | 13 – 49.3 (0.9 – 3.4) | PSI (bar) |
| Pressure pulse duration | ~2 – 5 | ms |
| Temperature at exit | ~176 – 392 (80 – 200) | °F (°C) |
| Gas volume expansion | 8 – 10× initial volume | – |
| Flow velocity at exit | ~393 – 787 (120 – 240) | ft/s (m/s) |
| Sound level near muzzle (1m distance) | 114 – 138 | dB |
| Recoil effect | Slight, directed backward | – |
| Thermal load (interior wall) | Short-term <3 ms | – |

---

## 📜 License

This project is licensed under a **custom non-commercial license**:

You may **share, modify, and showcase** this project **online**, but you must **credit the original author**:
**"Coded by LyTack"**

**Commercial use is not permitted without written permission.**
Full terms are available in the [`LICENSE`](./LICENSE) file.

---

## 🙌 Credits 

 # **ＬＹＴＡＣＫ**

