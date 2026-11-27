# Rheinmetall Control Board — User Guide

**Rheinmetall Control App** is the official Android companion app for the **Rheinmetall Control Board (RHV1)**. Using a wireless Bluetooth connection, it lets you monitor real-time board temperature and input voltage, switch USB PD output voltage levels, fine-tune PWM fan frequency and duty cycle, and customize advanced 5V 3-pin addressable RGB lighting directly from your smartphone.

## Key Features

* **Live Telemetry Monitoring:** View real-time **Board temperature (°C)** and **Input Voltage (V)** directly on the dashboard.
* **4-Stage USB PD Output Control:** Switch instantly between **Quiet (5V)**, **Balanced (9V)**, **Fast (12V)**, and **Boost (15V)**.
* **Precision PWM Fan Tuning:** Adjust both **Fan duty cycle (0%–100%)** and **PWM frequency** to match your specific fan for quiet, efficient cooling.
* **Advanced 5V 3-Pin RGB Lighting Engine:** Full control over brightness, frame rate, active LED count (up to 22 LEDs), multiple animation modes, local phone presets, and 3 onboard hardware memory slots with customizable startup slot.

## Downloads & Resources

| Resource | Link | Notes |
| ----- | ----- | ----- |
| **Android App (APK)** | [Download Latest Release](https://github.com/danieladven0772-lgtm/Rheinmetal-Control-Board-App/releases/latest) | Official `.apk` installer for Android |
| **3D Board File** | [Download on Printables](https://www.printables.com/model/1903467-board-decoy-pd-trigger-5-15v-bp-v1) | 3D model for case/enclosure design |

## Technical Specifications & Requirements

| Parameter | Specification |
| ----- | ----- |
| **Supported Hardware** | Rheinmetall Control Board (`Rheinmetall RHV1`) |
| **Power Input** | USB Power Delivery (PD), **5–15V 3A** |
| **Output Voltage Levels** | Quiet (**5V**), Balanced (**9V**), Fast (**12V**), Boost (**15V**) |
| **Peltier Output** | Dedicated high-current output pad (rated up to USB PD supply) |
| **PWM (Fan) Output Limit** | **< 1A max** (never exceed 1A) |
| **Recommended PWM Frequency** | **500 Hz – 5 kHz** (`0.5 – 5.0 kHz` in app) |
| **RGB Output** | **5V 3-pin** addressable RGB (`5V`, `Data`, `GND`), **< 1A max**, up to **22 Active LEDs** |
| **Wireless Interface** | Bluetooth (requires Bluetooth + GPS/Location enabled on Android) |

## Safety Warnings

> **CRITICAL:** Read these precautions carefully before soldering, wiring, or powering on the board.

* **Load Limit Warning:** **NEVER** connect a Peltier module or any heavy load exceeding **1A** to the **PWM (Fan)** or **RGB** outputs. High-current loads must only be connected to the dedicated **Peltier** output pads.
* **Polarity & RGB Voltage Check:** Double-check all positive (`+`) and negative (`-`) connections before applying power. Reverse polarity will permanently damage the board and connected components. The RGB output uses **5V 3-pin** LEDs only—do **not** connect 12V 4-pin RGB strips.
* **PWM Frequency Heat Warning:** Operating the PWM output **above the recommended 500 Hz – 5 kHz (`0.5 – 5.0 kHz`) range** will generate **excessive heat** on the board. Keep your frequency within the recommended range and monitor **Board temperature** in the app.
* **Power Off Before Wiring:** Always disconnect the USB PD cable before soldering or modifying connections, and inspect solder joints for bridges or shorts before powering on.
* **Peltier Thermal Management:** Never power a Peltier module without a properly mounted heatsink and cooling fan on its hot side.
* **Certified USB PD Adapter & Cable:** Use a USB PD adapter and USB-C cable rated for **5–15V 3A**. Standard 5V chargers will not trigger higher output levels (`Balanced`, `Fast`, or `Boost`).

## Hardware Output Pads Overview

Solder each component to its dedicated output pads on the board:

| Output Pad | Intended Component | Current Limit | Notes |
| ----- | ----- | ----- | ----- |
| **Peltier** | Peltier thermoelectric module / high-current load | Dedicated high-current | Verify `+` / `-` polarity; requires heatsink + fan |
| **Fan / PWM** | Cooling fan | **Max 1A** | Controlled via Fan duty cycle (`0%–100%`) and PWM frequency |
| **RGB** | **5V 3-pin** addressable RGB LED strip / ring (up to 22 LEDs) | **Max 1A** | **5V 3-pin (`5V`, `Data`, `GND`)** only; verify pin alignment before powering on |

## Quick Start Guide

1. **Solder Wiring:** Disconnect power, then solder each component to its dedicated output pads (**Peltier**, **Fan/PWM**, and **5V 3-pin RGB** separately). Verify all `+` / `-` polarities and check for solder bridges.
2. **Install the App:** Download and install the `.apk` file on your Android device from the [GitHub Releases page](https://github.com/danieladven0772-lgtm/Rheinmetal-Control-Board-App/releases/latest). If prompted, enable **Install unknown apps** for your browser or file manager.
3. **Power On the Board:** Connect the board using a **USB Power Delivery (PD)** compatible adapter and cable rated for **5–15V 3A**.
4. **Enable Phone Permissions:** Turn on both **Bluetooth** and **GPS / Location Services** on your smartphone (required by Android for Bluetooth scanning), and allow **Nearby Devices** permission if prompted.
5. **Pair & Control:** Open the **Rheinmetall Control App**, select **Rheinmetall RHV1** from the device selector, wait until the status shows **Connected**, and configure your output level, fan PWM, and RGB lighting.

## App Dashboard & Controls

### 1. Device Status & Live Telemetry

* **Device Selector (`Rheinmetall RHV1`):** Switch between boards or check connection status (`Connected` vs. `UI preview · no Bluetooth connection`).
* **Board temperature (`°C`):** Displays the live temperature of the control board. Keep an eye on this reading when running **Boost (15V)** or testing PWM settings.
* **Input Voltage (`V`):** Shows the active USB PD voltage supplied to the board so you can confirm your selected output level is active.

### 2. Output Control (Output Level)

Select one of four USB PD output voltage presets depending on your cooling and noise needs:

| Output Level | Voltage | Best Used For |
| ----- | ----- | ----- |
| **Quiet** | **5V** | Low power, minimal heat, quietest operation / standby cooling |
| **Balanced** | **9V** | Everyday cooling with a good balance of performance and thermal output |
| **Fast** | **12V** | Strong active cooling for heavier workloads |
| **Boost** | **15V** | Maximum cooling performance (requires a 15V-capable USB PD 3A charger; monitor board temperature) |

### 3. Fan Controls (PWM Frequency & Duty Cycle)

Tap **Fan controls** on the main screen to open the PWM tuning panel.

#### What Are PWM Frequency and Duty Cycle?

* **PWM Frequency (`kHz`):** How many times per second the board rapidly switches power to the fan on and off. Frequency affects motor smoothness, startup behavior, and whether the fan makes an audible whining/buzzing sound.
* **Fan Duty Cycle (`0% – 100%`):** The percentage of time power stays "on" during each cycle. A higher duty cycle spins the fan faster; a lower duty cycle slows it down (`0%` = off, `100%` = full speed).

> **HEAT DISCLAIMER:** Use **500 Hz – 5 kHz (`0.5 – 5.0 kHz` in the app's `kHz` field)** as your operating range. **Setting the PWM frequency above 5 kHz (`5.0 kHz`) will generate excessive heat** on the control board and is not recommended.

#### How to Tune Your Fan Step-by-Step

Because **every fan model responds differently** to PWM signals, you should experiment to find the sweet spot for your specific fan:

1. **Set a Starting Frequency:** Enter a value between **`0.5` and `5.0` kHz** (500 Hz – 5 kHz) in the **PWM frequency** box—for example, start at **`1.0` kHz** or **`2.0` kHz**—and tap **Apply**.
2. **Test the Duty Cycle:** Slowly drag the **Fan duty cycle** slider from `0%` upward until the fan starts spinning smoothly. Note the minimum percentage your fan needs to start reliably (many fans require ~20%–40% to start).
3. **Fine-Tune for Noise & Smoothness:** If you hear an annoying whine/hum or the fan stutters at low speeds, try adjusting the frequency in small steps within **`0.5 – 5.0` kHz** (always tapping **Apply**) until the fan runs smoothly and quietly.
4. **Check Board Temperature:** After dialing in your settings, verify that **Board temperature** on the dashboard stays stable during sustained operation.

### 4. Lighting & Advanced RGB Controls

The RGB output supports **5V 3-pin addressable RGB** LED strips or rings (up to **22 LEDs**, max **1A**). Use the **Lighting** toggle on the main screen to turn RGB LEDs on or off, and tap **Effects and settings** to open the **Advanced lighting** editor.

#### Basic Settings (Applies to All Modes)

| Control | Function & Purpose | Recommendation |
| ----- | ----- | ----- |
| **Brightness (`0% – 100%`)** | Adjusts overall LED light intensity. | Use **40%–75%** for daily use to reduce heat, keep current draw well below the 1A limit, and extend LED lifespan. Use **100%** only when maximum visibility is needed. |
| **Frame rate (`fps`)** | Controls how many animation frames per second are rendered (e.g., `10 fps`). Higher values make motion smoother and faster. | Start around **10–20 fps** for smooth, low-overhead animations without jitter. |
| **Active LEDs (`1 – 22`)** | Sets how many LEDs on your connected 5V 3-pin strip or ring are active (up to 22 LEDs). | Set this to the **exact physical LED count** installed on your build so patterns like Rotation and Mirror align cleanly without dead gaps. |
| **Local works** | Opens presets saved locally on your smartphone so you can reload them anytime. | Use this to store a library of custom themes beyond the board's 3 onboard slots. |
| **Save locally** | Saves your current lighting configuration as a local preset on your phone. | Save your draft locally before experimenting with major changes so you can easily revert. |

#### Lighting Modes (1-by-1 Guide)

| Mode | Controls & Functions | Best Used For & Recommendations |
| ----- | ----- | ----- |
| **Global** (Solid Color) | **Color Wheel**, **Hue (`0°–360°`)**, **Saturation (`0%–100%`)**, **RGB (`0–255`)**, **HEX (`#RRGGBB`)**, and **Pastel colors** toggle (softens colors into lighter pastel shades). | Clean, static single-color lighting or matching an exact brand/setup color via HEX/RGB. Turn on **Pastel colors** for softer, less harsh ambient lighting. |
| **Breathing** | **Brightness step** (`Smooth` to `Strong` fade curve), **Color cycling** toggle (cycles through sequence automatically), **Color sequence (`1`–`7`)** slots, and per-slot **Hue** slider. | Relaxed pulsing ambient glow. Keep **Brightness step** toward **Smooth** (low value) for a gentle, natural fade; enable **Color cycling** with 2–4 complementary hues for subtle color shifts. |
| **Strobe** | **Flash count (`1`–`5`)** per burst, **Flash interval (`ms`)** between flashes, **Pause (`ms`)** between bursts, **Color count (`1`–`5`)**, and **Color sequence** + **Hue** per slot. | High-visibility alert or beacon effects. Start with a moderate **Flash interval** (`60–100 ms`) and a longer **Pause** (`2000–3000 ms`) so the effect looks crisp without being overly harsh on the eyes. |
| **Rotation** | **Interactive LED Ring & Color Wheel** (click LEDs to assign colors), **Direction** (`Stop` / `CW` / `CCW`), **Pastel colors** toggle, **Trail length (`5`–`9` LEDs)**, and **Turn off slot** (disables selected LED slot). | Spinning ring/comet effects on circular LED rings. Set **Trail length** to **6–7** for a balanced comet tail, and use **CW** or **CCW** to match your fan's rotation direction. |
| **Rainbow** | **Hue range (`0°–360°`)** dual slider (limits color spectrum), **Flow speed** (`Slow` to `Fast`), **Saturation** (`Soft` to `Vivid`, `0–255`), **Phase (`0°–359°`)** starting offset, **Mirror** toggle (symmetrical from center), and **Fade** toggle (soft brightness wave). | Classic flowing spectrum or custom 2-tone gradients. Narrow the **Hue range** (e.g., `180°–300°` for cyan-to-magenta) and enable **Mirror** for a sleek, modern dual-tone look instead of full rainbow. |

#### Lighting Slots (Saving to Board Memory)

The banner **`Device lighting settings are not synced`** appears whenever you edit settings while disconnected or before saving. To store settings directly on the board:

* **Slots `0`, `1`, `2`:** Three onboard hardware memory slots. Tap a slot number to select where you want to store or load a preset.
* **Save:** Writes your current lighting configuration to the selected onboard slot (`0`, `1`, or `2`).
* **Set startup slot:** Sets the selected slot as the default lighting preset that automatically loads every time the board powers on.
* **Recommendation:** Save your three favorite everyday looks in Slots `0`, `1`, and `2` (for example: `0` = subtle solid color, `1` = breathing, `2` = rainbow/rotation), then tap **Set startup slot** on your preferred default so the board remembers it without needing to reconnect your phone.

## Troubleshooting

| Issue | Possible Cause | Recommended Fix |
| ----- | ----- | ----- |
| **Board does not appear in Bluetooth scan** | Bluetooth or Location Services disabled, or missing app permissions | Turn on **Bluetooth** and **GPS / Location Services**, grant **Nearby Devices** permission in Android Settings, and confirm the board is powered on. |
| **App shows "UI preview · no Bluetooth connection"** | App is not paired/connected to a board | Tap the **Rheinmetall RHV1** selector at the top to scan and connect via Bluetooth. |
| **Cannot install the `.apk` file** | Android blocks sideloaded apps by default | Enable **Install unknown apps** for your browser or file manager in Android Settings, then open the `.apk` again. |
| **Balanced / Fast / Boost voltage does not activate** | Charger or cable does not support USB PD (5–15V 3A) | Switch to a certified USB PD adapter and USB-C cable rated for **5–15V 3A**, then check **Input Voltage** on the dashboard. |
| **Board gets unusually hot during fan operation** | PWM frequency set too high (> 5 kHz) or heavy load on wrong pad | Lower **PWM frequency** back into **0.5 – 5.0 kHz** and tap **Apply**. Confirm no Peltier or >1A load is connected to the Fan/PWM or RGB pads. |
| **Fan whines, buzzes, or won't spin at low %** | Frequency mismatch or duty cycle below fan startup threshold | Test different frequencies within **0.5 – 5.0 kHz** (tap **Apply** after each change) and raise **Fan duty cycle** slightly until startup is smooth. |
| **RGB LEDs do not light up or show wrong colors** | Wrong LED type (e.g., 12V 4-pin), reversed wiring, or wrong Active LEDs count | Confirm you are using a **5V 3-pin** addressable RGB LED (`5V`, `Data`, `GND`), verify solder joints, and match **Active LEDs** to your strip/ring. |
| **RGB settings reset after unplugging power** | Settings were not saved to an onboard slot or startup slot not set | Select Slot **0**, **1**, or **2**, tap **Save**, then tap **Set startup slot** while connected. |

## License & Usage Terms

**All Rights Reserved.**

The software (`.apk`) and documentation provided in this repository are strictly for personal use with official **Rheinmetall** hardware products. You may **not** modify, reverse-engineer, redistribute, or use these files for commercial purposes without explicit written permission from the author.
