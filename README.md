# Rheinmetall Control Board App

Rheinmetall Control App is the official companion app for the Rheinmetall controller board. Using a wireless Bluetooth connection, it allows you to adjust output voltage, fine-tune PWM frequency and duty cycle, and customize RGB lighting styles directly from your device.

## Downloads
* **Android App (APK):** [Download Latest Release](https://github.com/danieladven0772-lgtm/Rheinmetal-Control-Board-App/releases/latest)
* **3D File Board:** [Download on Printables](https://www.printables.com/model/1903467-board-decoy-pd-trigger-5-15v-bp-v1)

---

##  Safety Warnings
> **CRITICAL:** Read these precautions carefully before wiring or powering up the board:
> * **Load Limit Warning:** **NEVER** connect a Peltier module or any heavy load exceeding **1A** to the **PWM (Fan)** or **RGB** outputs. High-current loads must only be connected to the dedicated Peltier output.
> * **Polarity Check:** Double-check all positive (`+`) and negative (`-`) connections before applying power. Reverse polarity will permanently damage the board.

---

## Quick Start Guide
1. **Solder Wiring:** Solder each component to its dedicated output pads (**RGB**, **Fan/PWM**, and **Peltier** separately). Verify that all polarities (`+` / `-`) are correct before proceeding.
2. **Install the App:** Download and install the `.apk` file on your Android device from the link above.
3. **Power On the Board:** Connect the board using a **USB Power Delivery (PD)** compatible adapter and cable rated for **5–15V 3A**.
4. **Enable Phone Permissions:** Turn on both **Bluetooth** and **GPS / Location Services** on your smartphone (required by Android for Bluetooth device scanning).
5. **Pair & Control:** Open the Rheinmetall Control App, connect to the board, and configure your desired output voltage, PWM frequency/duty cycle, and RGB lighting style.

---

## ©️ License & Usage Terms
**All Rights Reserved.**  
The software (`.apk`) and documentation provided in this repository are strictly for personal use with official **Rheinmetall** hardware products. You may **not** modify, reverse-engineer, redistribute, or use these files for commercial purposes without explicit written permission from the author.
