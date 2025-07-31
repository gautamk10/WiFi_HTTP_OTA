
# 🔄 ESP32 OTA Firmware Update via GitHub (HTTP + WiFiManager)

This project demonstrates how to implement **Over-The-Air (OTA)** firmware updates on an **ESP32** board using:
- 📡 WiFi provisioning via **WiFiManager**
- 🌐 Firmware version control using a `version.json` file on **GitHub**
- 🔒 Secure OTA update using **HTTPS** with `WiFiClientSecure`
- 📦 Auto-fetching and updating binary (`.bin`) firmware if a new version is available
- 
## 🚀 Features
- Automatically connects to known WiFi or opens a captive portal for user input
- Downloads a `version.json` file from GitHub
- Compares current firmware version with the latest available version
- Downloads and installs the `.bin` file OTA if an update is available
- Reboots automatically after a successful update
- Logs progress over Serial for debugging
---

## 🧩 Libraries Used
Make sure to install the following libraries via the Arduino Library Manager:

- `WiFiManager` — [tzapu/WiFiManager](https://github.com/tzapu/WiFiManager)
- `ArduinoJson` — [bblanchon/ArduinoJson](https://arduinojson.org/)
- `HTTPClient` (built-in)
- `Update` (built-in)
- `WiFiClientSecure` (built-in)

## 🛠️ Setup Instructions
1. **Clone the Repository**  
   ```bash
   git clone https://github.com/gautamk10/WiFi_HTTP_OTA.git
````

2. **Open the Sketch in Arduino IDE**
   Ensure you have selected **ESP32 Dev Module** as the board and set the correct COM port.

3. **Update `CURRENT_VERSION`**
   In your sketch:

   ```cpp
   #define CURRENT_VERSION "1.0.1"
   ```

   Update this string with each firmware release.

4. **Create `version.json` on GitHub**

   ```json
   {
     "version": "1.0.2",
     "bin_url": "https://raw.githubusercontent.com/gautamk10/WiFi_HTTP_OTA/main/firmware_v1.0.2.bin"
   }
   ```

   Replace the version and URL according to your `.bin` firmware.

5. **Build & Upload**
   Upload the sketch via USB. Once connected to WiFi, the ESP32 will check for updates from GitHub.

---

## 🌐 WiFi Manager

If no known WiFi credentials are available, a **captive portal** named `ESP32_Setup` (password: `admin123`) will appear.

## 📁 File Structure

```
WiFi_HTTP_OTA/
│
├── firmware_v1.0.1.bin       <- Initial firmware binary
├── firmware_v1.0.2.bin       <- Updated firmware
├── version.json              <- Contains latest version info
├── WiFi_HTTP_OTA.ino         <- Main source code
└── README.md
```
## 🔐 Security Note

Currently, `client.setInsecure()` is used for simplicity.
For production, implement **certificate pinning** or use a valid root certificate for better HTTPS security.

## 🧪 Sample Serial Output

```
✅ WiFi Connected!
Current Version: 1.0.1
Latest Version : 1.0.2
⬆️  New version detected. Starting OTA...
✅ OTA successful! Rebooting...
```

---

## 📜 License

This project is licensed under the MIT License.

---

## 🙋‍♂️ Author

**Gautam Kumar**
🔗 [GitHub Profile](https://github.com/gautamk10)

---

```

Let me know if you want to include images, badges, or GitHub Actions for auto-build/firmware CI too.
```
