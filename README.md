# Makoto Glass — Public Beta

> A lightweight system shell and iPhone companion project for **Google Glass Enterprise Edition 2**.
>
> Developed independently by **MAKOTO LAB**.

<p>
  <a href="https://github.com/lancer1234/MakotoGlass-Beta/releases/download/v0.1.0-beta/MakotoGlass-0.1.0-beta.apk"><img alt="Download Makoto Glass" src="https://img.shields.io/badge/Download-v0.1.0%20Beta-2ea44f?style=for-the-badge&logo=android&logoColor=white"></a>
  <a href="https://github.com/lancer1234/MakotoGlass-Beta/releases/tag/v0.1.0-beta"><img alt="Release Notes" src="https://img.shields.io/badge/Release-Notes-555?style=for-the-badge&logo=github&logoColor=white"></a>
  <a href="https://buymeacoffee.com/makotolab"><img alt="Support MAKOTO LAB" src="https://img.shields.io/badge/Support-MAKOTO%20LAB-FFDD00?style=for-the-badge&logo=buymeacoffee&logoColor=000000"></a>
</p>

**Public Beta** — expect bugs, incomplete features, and changes between releases.

Makoto Glass is not affiliated with, endorsed by, or sponsored by Google LLC or Apple Inc. Google Glass, Android, iPhone, iOS, and related names are trademarks of their respective owners.

---

## Index

- [Overview](#overview)
- [Current Beta Features](#current-beta-features)
- [Makoto Link for iPhone](#makoto-link-for-iphone)
- [Requirements](#requirements)
- [Installation](#installation)
- [Connect an iPhone](#connect-an-iphone)
- [Updating](#updating)
- [Accessibility Control](#accessibility-control)
- [Known Limitations](#known-limitations)
- [Support MAKOTO LAB](#support-makoto-lab)
- [Reporting Bugs](#reporting-bugs)
- [About MAKOTO LAB](#about-makoto-lab)
- [License](#license)

---

## Overview

Makoto Glass started as a personal hobby project exploring how far Google Glass Enterprise Edition 2 can still be pushed as a modern wearable computer.

It is developed independently by one person under **MAKOTO LAB**, with a focus on extending unusual and discontinued computing platforms through custom software, Bluetooth integration, companion-device services, and new interaction ideas.

The current public beta targets **Google Glass Enterprise Edition 2 running Android 8.1**.

---

## Current Beta Features

- Custom Glass launcher
- Apple Notification Center Service (**ANCS**)
- iPhone notification display and history
- Supported notification actions and incoming-call handling
- Apple Media Service (**AMS**)
- Now Playing and media controls
- Camera and photo viewer
- Application launcher
- Tilt Wake
- Automatic brightness
- System status
- Accessibility-based system control foundation
- Bluetooth reconnect and recovery

Some features depend on the connected iPhone and current iOS Bluetooth state.

---

## Makoto Link for iPhone

**Makoto Link** is the companion iPhone application for Makoto Glass and is currently being prepared for TestFlight distribution.

Until it becomes publicly available, Makoto Glass can still use supported native Apple Bluetooth services such as **ANCS** and **AMS** directly with an iPhone.

The following features require Makoto Link and are not yet available in the standalone Glass beta:

- iPhone Remote
- iPhone GPS / Location Bridge
- Find Glass
- Makoto Link device management
- Companion-app configuration
- Advanced Makoto Link pairing

This README will be updated when the TestFlight beta becomes available.

---

## Requirements

### Google Glass

- Google Glass Enterprise Edition 2
- Android 8.1
- Bluetooth Low Energy
- ADB access for installation

**Root access is not required.**

### iPhone

For standalone ANCS / AMS functionality:

- Compatible iPhone
- Bluetooth enabled
- Notification access allowed for the paired Glass accessory

---

## Installation

### 1. Download Makoto Glass

<a href="https://github.com/lancer1234/MakotoGlass-Beta/releases/download/v0.1.0-beta/MakotoGlass-0.1.0-beta.apk"><img alt="Download Makoto Glass v0.1.0 Beta APK" src="https://img.shields.io/badge/Download-MakotoGlass--0.1.0--beta.apk-2ea44f?style=for-the-badge&logo=android&logoColor=white"></a>

<a href="https://github.com/lancer1234/MakotoGlass-Beta/releases/tag/v0.1.0-beta"><img alt="View v0.1.0 Beta Release" src="https://img.shields.io/badge/View-v0.1.0%20Beta%20Release-555?style=for-the-badge&logo=github&logoColor=white"></a>

The file you need is:

```text
MakotoGlass-0.1.0-beta.apk
```

Do **not** download GitHub's automatically generated `Source code (zip)` or `Source code (tar.gz)` files. Those are repository archives, not the Makoto Glass application.

The Makoto Glass source code is not distributed through this public repository.

### 2. Enable ADB on Glass

Enable **Developer options** and **USB debugging** on Google Glass, then connect it to your computer over USB.

Verify the device:

```bash
adb devices
```

You should see a device entry similar to:

```text
XXXXXXXXXXXX    device
```

Approve the ADB authorization prompt on Glass if one appears.

### 3. Install Makoto Glass

Open Terminal / Command Prompt in the folder containing the downloaded APK and run:

```bash
adb install -r MakotoGlass-0.1.0-beta.apk
```

A successful installation returns:

```text
Success
```

### 4. Set Makoto Glass as Home

If Android asks which application should be used as Home, select **Makoto Glass** and choose **Always** if available.

Makoto Glass will then act as the primary launcher.

---

## Connect an iPhone

Makoto Link is **not required** for basic ANCS / AMS operation.

### 1. Enable Bluetooth

On iPhone:

```text
Settings → Bluetooth → On
```

Keep this page open during the first pairing attempt.

### 2. Put Glass into pairing mode

Open the Bluetooth / Link screen in Makoto Glass and start pairing.

The device may advertise as:

```text
Makoto Glass
```

### 3. Pair and authorize

Select Makoto Glass from the iPhone Bluetooth interface if it appears, then complete any pairing or authorization prompts shown by iOS or Glass.

A Bluetooth connection alone does not always mean ANCS access has been authorized. Complete any notification-access or Bluetooth authorization prompts presented by iOS.

### 4. Wait for ANCS / AMS

After pairing, Makoto Glass will attempt to discover Apple's notification and media services automatically.

If notifications do not appear, confirm Bluetooth is connected and notification access is allowed. Restart Bluetooth, Makoto Glass, or the Glass device if necessary.

---

## Updating

<a href="https://github.com/lancer1234/MakotoGlass-Beta/releases"><img alt="All Releases" src="https://img.shields.io/badge/Download-Latest%20Release-2ea44f?style=for-the-badge&logo=github&logoColor=white"></a>

Download the newest APK and install it over the existing version:

```bash
adb install -r MakotoGlass-<new-version>.apk
```

Using `-r` preserves existing application data when the APK uses a compatible signing key.

Avoid uninstalling unless necessary, because uninstalling may remove local settings and stored app data.

---

## Accessibility Control

Some system-wide Remote functionality uses Android Accessibility Services so supported Android interfaces can be controlled without root access.

Compatibility depends on how each application exposes its interface. Apps using custom rendering, OpenGL, Canvas-based interfaces, or incomplete accessibility metadata may not support every Remote action.

Accessibility control is optional and does not affect basic ANCS notification functionality.

---

## Known Limitations

- Bluetooth reconnection may occasionally require restarting Bluetooth or Glass.
- ANCS availability is controlled by iOS.
- Accessibility support varies between Android applications.
- Makoto Link companion features are unavailable until the iPhone beta is released.
- GPS and Location Bridge require Makoto Link for iPhone.
- Navigation is not yet included.
- Features and protocols may change between beta releases.

Google Glass Enterprise Edition 2 is an older Android 8.1 platform, and behavior may vary between firmware versions.

---

## Support MAKOTO LAB

Makoto Glass is an independent project I build in my own time because I enjoy experimenting with unusual and discontinued computing platforms.

I am currently between jobs, and development hardware, test devices, accessories, signing, and distribution costs are funded personally.

If you enjoy the project and would like to help it continue, support makes it possible for me to purchase additional test devices, explore more firmware and hardware combinations, and expand Makoto Link support to more wearable platforms in the future.

<a href="https://buymeacoffee.com/makotolab"><img alt="Support MAKOTO LAB on Buy Me a Coffee" src="https://img.shields.io/badge/Support-MAKOTO%20LAB-FFDD00?style=for-the-badge&logo=buymeacoffee&logoColor=000000"></a>

Support is completely optional and does not purchase features, support priority, licenses, ownership, or development priority.

---

## Reporting Bugs

<a href="https://github.com/lancer1234/MakotoGlass-Beta/issues"><img alt="Report a Bug" src="https://img.shields.io/badge/GitHub-Report%20a%20Bug-d73a49?style=for-the-badge&logo=github&logoColor=white"></a>

Useful information includes the Makoto Glass version, Glass firmware / Android version, iPhone model and iOS version when relevant, steps to reproduce the problem, and relevant ADB / Logcat output.

Please remove personal information, account data, Bluetooth identifiers, and other sensitive information before posting logs publicly.

---

## About MAKOTO LAB

**MAKOTO LAB** is an independent experimental software and hardware studio focused on extending unusual, discontinued, and emerging computing platforms.

Makoto Glass explores how Google Glass Enterprise Edition 2 can continue to function as a modern wearable platform through custom software, Bluetooth integration, and companion-device services.

**Project:** Makoto Glass  
**Companion:** Makoto Link  
**Developer:** MAKOTO LAB  
**Copyright:** © 2026 MAKOTO LAB. All rights reserved.

<p>
  <a href="https://www.instagram.com/d.wang___/"><img alt="Instagram" src="https://img.shields.io/badge/Instagram-@d.wang___-E4405F?style=for-the-badge&logo=instagram&logoColor=white"></a>
  <a href="https://buymeacoffee.com/makotolab"><img alt="Support MAKOTO LAB" src="https://img.shields.io/badge/Support-Buy%20Me%20a%20Coffee-FFDD00?style=for-the-badge&logo=buymeacoffee&logoColor=000000"></a>
</p>

---

## License

Makoto Glass is proprietary software distributed under the **MAKOTO LAB Limited Beta License**.

This public repository exists for binary releases, documentation, feedback, and issue tracking. It is **not an open-source repository**.

<a href="LICENSE"><img alt="View License" src="https://img.shields.io/badge/License-MAKOTO%20LAB%20Limited%20Beta-555?style=for-the-badge"></a>
