# Makoto Glass — Public Beta

**Makoto Glass** is an experimental system shell and companion software project for **Google Glass Enterprise Edition 2**.

Developed by **MAKOTO LAB**.

> **Public Beta** — expect bugs, incomplete features, and changes between releases.

Makoto Glass is an independent project and is **not affiliated with, endorsed by, or sponsored by Google LLC or Apple Inc.** Google Glass, Android, iPhone, iOS, and related names are trademarks of their respective owners.

---

## About the project

Makoto Glass started as a personal hobby project to see how far Google Glass Enterprise Edition 2 could still be pushed as a modern wearable computer.

It is currently developed independently by one person under **MAKOTO LAB**. The project is not backed by a company, manufacturer, or hardware vendor.

Development is focused on extending the useful life of discontinued and unusual computing platforms through custom software, Bluetooth integration, companion-device services, and new interaction ideas.

### Support the project

Makoto Glass is currently developed in my personal time. I am also currently between jobs, so development hardware, test devices, accessories, and platform fees are paid out of pocket.

If this project is useful or interesting to you, voluntary donations help me:

- purchase additional Glass and wearable devices for testing;
- test more firmware and hardware configurations;
- expand Makoto Link compatibility to additional devices;
- maintain development tools, signing, and distribution costs;
- keep public beta builds available while continuing independent development.

**PayPal donation link: coming soon.**

Donations are completely optional and do not purchase support, features, licenses, ownership, or development priority. The project will remain driven by technical feasibility, testing, and available development time.

---

## Current beta features

Current Glass functionality includes:

- Custom Glass launcher
- Apple Notification Center Service (ANCS)
- iPhone notification display
- Notification history
- Supported notification actions
- Incoming call notification handling
- Apple Media Service (AMS)
- Now Playing information
- Media controls
- Camera
- Photo viewer
- Application launcher
- Tilt Wake
- Automatic brightness
- System status
- Accessibility-based system-control foundation
- Bluetooth reconnect and recovery

Some functionality depends on the connected iPhone and current iOS Bluetooth state.

---

## Makoto Link for iPhone

The **Makoto Link** iPhone companion application is currently being prepared for TestFlight distribution.

Until Makoto Link is available, Makoto Glass can still use supported native Apple Bluetooth services such as:

- Apple Notification Center Service (ANCS)
- Apple Media Service (AMS)

Features that require Makoto Link are not yet available in the standalone Glass beta, including:

- iPhone Remote
- iPhone GPS / Location Bridge
- Find Glass
- Makoto Link device management
- Companion-app configuration
- Advanced Makoto Link pairing

This README will be updated when the Makoto Link TestFlight beta becomes available.

---

## Requirements

### Google Glass

- Google Glass Enterprise Edition 2
- Android 8.1
- Bluetooth Low Energy
- ADB access for installation

**Root access is not required** for the standard Makoto Glass experience.

Optional experimental functionality may support enhanced capabilities on modified devices in future releases, but root is not a requirement for Makoto Glass.

### iPhone

For standalone ANCS / AMS functionality:

- Compatible iPhone
- Bluetooth enabled
- Notification access allowed for the paired Glass accessory

Makoto Link will provide additional features when the iPhone beta becomes available.

---

# Installation

## 1. Download Makoto Glass

Open the **Releases** section of this repository and download the latest APK:

```text
MakotoGlass-<version>.apk
```

Do not use GitHub's automatically generated source archives as application packages. The Makoto Glass application source code is not distributed through this public repository.

## 2. Enable ADB on Google Glass

Developer options and USB debugging must be enabled on the Glass.

Connect the Glass to your computer by USB and verify that ADB can see the device:

```bash
adb devices
```

The Glass should appear similar to:

```text
XXXXXXXXXXXX    device
```

If an authorization prompt appears on Glass, approve the computer's ADB key.

## 3. Install the APK

From the directory containing the downloaded APK:

```bash
adb install -r MakotoGlass-<version>.apk
```

Example:

```bash
adb install -r MakotoGlass-0.1.0-beta.apk
```

A successful installation should return:

```text
Success
```

## 4. Select Makoto Glass as Home

After installation, Android may ask which application should be used as the Home application.

Select **Makoto Glass** and, if available, choose **Always**.

Makoto Glass will then act as the primary launcher for the device.

---

# Connecting an iPhone — standalone beta

Makoto Link is not required for basic ANCS / AMS operation.

## 1. Enable Bluetooth on iPhone

On the iPhone:

```text
Settings → Bluetooth → On
```

Keep the Bluetooth settings page open during initial pairing.

## 2. Open the Glass Bluetooth / Link screen

On Makoto Glass, navigate to the Bluetooth / Link pairing interface and place the Glass into pairing mode.

The Glass may advertise itself as:

```text
Makoto Glass
```

## 3. Pair the devices

If Makoto Glass appears in the iPhone Bluetooth interface, select it and complete any Bluetooth pairing or authorization prompts shown by iOS or Glass.

Pairing behavior can vary between iOS versions.

A Bluetooth connection alone does not necessarily mean ANCS has already been authorized. Complete any notification-access or Bluetooth authorization dialogs presented by iOS.

## 4. Wait for ANCS connection

After pairing, Makoto Glass will attempt to discover Apple Notification Center Service from the iPhone.

When ANCS is available, supported iPhone notifications can be displayed on Glass.

If notifications do not appear:

1. Confirm Bluetooth is connected.
2. Confirm notification access has been allowed.
3. Restart Bluetooth on the iPhone if necessary.
4. Restart Makoto Glass.
5. If necessary, reboot the Glass and reconnect the devices.

---

# Optional wireless ADB

After initially connecting Glass by USB:

```bash
adb tcpip 5555
```

Find the Glass Wi-Fi address:

```bash
adb shell ip addr show wlan0
```

Then connect wirelessly:

```bash
adb connect GLASS_IP:5555
```

Example:

```bash
adb connect 192.168.50.11:5555
```

Verify:

```bash
adb devices
```

Android 8.1 may disable TCP ADB after a reboot. If that happens, reconnect by USB and run `adb tcpip 5555` again.

---

# Updating Makoto Glass

Download the newer APK and install it using:

```bash
adb install -r MakotoGlass-<new-version>.apk
```

Using `-r` preserves existing application data when Android accepts the application signature.

Do not uninstall the existing application unless necessary, because uninstalling may erase Makoto Glass settings and stored application data.

---

# Accessibility control

Some system-wide Remote functionality uses Android Accessibility Services.

This allows Makoto Glass to interact with supported Android user interfaces without requiring root access.

Accessibility behavior depends on the application being controlled. Applications using custom rendering, OpenGL, Canvas-based interfaces, or incomplete accessibility metadata may not support every Remote action.

Accessibility control is optional and does not affect basic ANCS notification functionality.

---

# Known limitations

Makoto Glass is currently beta software.

Known limitations may include:

- Bluetooth reconnection may occasionally require restarting Bluetooth or Glass.
- ANCS availability is controlled by iOS.
- Some applications expose incomplete Accessibility information.
- System-wide Remote compatibility varies between Android applications.
- Makoto Link companion features are unavailable until the iPhone beta is released.
- GPS functionality requires Makoto Link for iPhone.
- Navigation functionality is not yet included.
- Features and protocols may change between beta releases.

Google Glass Enterprise Edition 2 is an older Android 8.1 platform, and behavior may differ between firmware versions.

---

# Reporting bugs

Please use the **Issues** section of this repository.

When reporting a problem, include when possible:

- Makoto Glass version
- Glass firmware / Android version
- iPhone model
- iOS version
- Description of the problem
- Steps to reproduce it
- Relevant ADB / Logcat output

Please remove personal information, Bluetooth identifiers, account information, and other sensitive data from logs before posting them publicly.

---

# About MAKOTO LAB

**MAKOTO LAB** is an independent experimental software and hardware studio focused on extending unusual, discontinued, and emerging computing platforms.

Makoto Glass explores how Google Glass Enterprise Edition 2 can continue to function as a modern wearable computing platform through custom software, Bluetooth integration, and companion-device services.

**Project:** Makoto Glass  
**Companion platform:** Makoto Link  
**Developer:** MAKOTO LAB  
**Instagram:** @d.wang___  
**Copyright:** © 2026 MAKOTO LAB. All rights reserved.

---

# License

Makoto Glass is proprietary software distributed under the **MAKOTO LAB Limited Beta License**.

The public repository is provided for release distribution, documentation, and issue tracking. It is **not an open-source repository**.

See [LICENSE](LICENSE) for the full terms.
