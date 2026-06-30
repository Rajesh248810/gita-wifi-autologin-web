# ⚡ GITA Wi-Fi Auto-Login Configurator

[![Netlify Status](https://api.netlify.com/api/v1/badges/8ba47864-4e2b-4d43-85f2-53b0dfb2f3fb/deploy-status)](https://gitaconnection.online)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

A premium, client-side web application built for students of **GITA Autonomous College, Bhubaneswar** to automate and stabilize network connections to the campus Sophos/Cyberoam captive portal. 

🔗 **Live Portal:** [https://gitaconnection.online](https://gitaconnection.online)

---

## ❌ The Daily Problems We Faced
* **Browser Requirement:** Constantly having to open a web browser and re-type credentials to log in.
* **Keep-Alive Issues:** If the Sophos page/tab was closed, the gateway automatically disconnected the user.
* **Laptop Sleep & Boot:** Closing the laptop or booting up required going through the manual login ritual again.
* **Frequent Session Drops:** Getting kicked off the network during large downloads, coding sessions, or video streams.

## ✅ The Automated Solutions
* **No Browsers Opened:** Connects your device completely in the background.
* **One-Time Config:** Enter your credentials once, generate the custom installer, and let it handle the rest.
* **Keep-Alive Heartbeat:** Sends a status check request every **30 seconds** to prevent timeouts.
* **Instant Reconnect:** Scans connectivity every **5 seconds** and logs back in immediately if disconnected.
* **Device Sleep Detection:** Re-authenticates automatically the moment your laptop wakes up.
* **Negligible Footprint:** Background script runs on a sleep timer, using 0.0% CPU and less than 15MB of RAM.

---

## 📂 Project Architecture

```directory
gita-wifi-autologin-web/
├── index.html         # Portal User Interface (HTML5 layout)
├── style.css          # Visual styling system (Responsive glassmorphism UI)
├── app.js             # Configuration logic + Bundled JSZip + Installer scripts
├── DEPLOYMENT.md      # Static hosting deployment guide
└── README.md          # Project documentation
```

### Generated Installer ZIP Structure (Windows)
When a user inputs their credentials and downloads the zip, the web portal uses client-side compression to dynamically package:
1. `config.json` - Custom config storing Sophos credentials and gateway IP.
2. `autologin.ps1` - Active monitoring PowerShell loop (5s checks, 30s heartbeats).
3. `run_hidden.vbs` - Visual Basic script to launch PowerShell silently in the background.
4. `install.ps1` - Installer to register task scheduler with `-MultipleInstances IgnoreNew`.
5. `setup.bat` - UAC-elevation wrapper script to run the installer with Admin privileges.
6. `uninstall.ps1` / `uninstall.bat` - Cleaner to completely stop tasks and wipe folder contents.

---

## 🚀 Setup Instructions

### 💻 Windows Laptop Setup (Recommended)
1. Open the [GITA Configurator](https://gitaconnection.online), type your Sophos ID & Password, and download the custom installer ZIP.
2. **Extract** the ZIP folder (Right-click -> *Extract All...*).
3. Open the folder and double-click **`setup.bat`** (Click **Yes** to run as Administrator).
4. That's it! The script registers a background task that starts automatically on logon and Wi-Fi connect events.

### 🤖 Android Setup (MacroDroid)
*Note: Mobile users do not need to download the ZIP file.*
1. Download **MacroDroid** from the Google Play Store.
2. Create a macro with:
   * **Trigger:** WiFi Connection -> Connects to GITA Wi-Fi.
   * **Action:** Applications -> HTTP Request. Method: **POST**. URL: `http://20.2.0.1:8090/login.xml`. Body: `mode=191&username=YOUR_ID&password=YOUR_PASS&producttype=2`.
   * **Heartbeat:** Set an action to trigger every **30 seconds** when connected: HTTP **GET** to `http://20.2.0.1:8090/live?mode=192&username=YOUR_ID&producttype=2` to maintain the session.

### 🍎 iOS / iPhone Setup (Shortcuts)
1. Open the built-in **Shortcuts** app.
2. Go to **Automation** -> **+** -> **Create Personal Automation** -> **Wi-Fi** -> Select GITA Wi-Fi -> Next.
3. Add Action -> search **Get Contents of URL**.
4. Configure as: URL: `http://20.2.0.1:8090/login.xml` -> Method: **POST** -> Form Fields: `mode=191`, `username=YOUR_ID`, `password=YOUR_PASS`, `producttype=1`.
5. Disable "Ask Before Running" so it fires instantly when you connect.

---

## 🔒 Security & Privacy
* **100% Client-Side:** All ZIP compression and script generation happen entirely in your web browser. No credential data is ever uploaded to a server.
* **Local Storage:** On Windows, credentials are stored locally inside `%APPDATA%\HostelWifiAutoLogin\config.json`.
* **Open Source:** Feel free to audit all background script codes inside `app.js` or within your extracted ZIP before running the setup.

---

## 👤 Author
* **Gyanaranjan Sahoo**
* GitHub: [@Rajesh248810](https://github.com/Rajesh248810)
* LinkedIn: [Gyanaranjan Sahoo](https://www.linkedin.com/in/gyanaranjan-sahoo-596998217/)
* Email: [sahoogyanaranjan480@gmail.com](mailto:sahoogyanaranjan480@gmail.com)

---

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
