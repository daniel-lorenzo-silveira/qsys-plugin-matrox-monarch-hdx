# Q-SYS Plugin | Matrox Monarch HDX Dual Encoder Control

##  Project Overview

This plugin provides **centralized control and monitoring** for the **Matrox Monarch HDX** dual-encoder within the Q-SYS ecosystem. Designed for professional AV environments, this solution allows independent management of both encoders (ENC1 and ENC2), supporting simultaneous or individual control of Recording and Streaming (RTMP/RTSP) tasks.

The plugin features a **Resilient Communication Engine** with smart retry logic and a "Semaphore-style" visual feedback system to ensure the operator always knows the exact state of the hardware.

### Key Features:
* **Dual-Channel Support:** Independent control and status for Encoder 1 and Encoder 2.
* **Adaptive UI:** The interface automatically switches icons and colors based on the Matrox configuration (Recording vs. Streaming).
* **Smart Visual Feedback:** * **Active States:** Recording/Streaming activity is indicated by pulsating colors (Blinking logic).
    * **Connectivity Semaphore:** HTTP status uses a Green/Yellow/Red logic for instant network diagnostics.
* **High Resilience:** Configurable `MaxRetries` and `PollingInterval` to handle network instability.
* **Modern API Handling:** Secure HTTPS communication for a clean and reliable UI.

---

## 📽️ Video Tutorial & Demonstration

Learn how to install, configure, and operate the plugin in this step-by-step guide:

<a href="https://youtu.be/OmUnig05Kg0">
    <img src="tutorial_thumbnail.png" alt="Watch Tutorial" width="600"/>
</a>

---

## ⚙️ Installation & Configuration

### 1. Requirements
* **Q-SYS Designer:** v9.4.8 (not tested in another versions).
* **Hardware:** Matrox Monarch HDX (Firmware with SDK enabled).
* **Network:** HTTPS (Port 443) access between the Q-SYS Core and the Matrox unit.

### 2. Configuration Properties
After adding the plugin to your schematic, configure the following properties:

| Property | Description | Default |
| :--- | :--- | :--- |
| `HostIP` | IP Address of the Matrox unit. | `172.16.16.46` |
| `MatroxPort` | HTTPS Port (Default is 443). | `443` |
| `Username` | Authentication username. | `admin` |
| `Password` | Authentication password. | `****` |
| `PollingInterval`| Time between status updates (seconds). | `10` |
| `MaxRetries` | Max failed attempts before declaring "Timeout". | `4` |

---

## 🎨 Visual States Reference

The plugin uses an intuitive color-coding system for immediate operator awareness:

| Mode | State | Button Color | Icon |
| :--- | :--- | :--- | :--- |
| **Record** | Idle | Maroon | `Record` |
| **Record** | Active | Red/Orange (Blinking) | `Stop` |
| **Streaming** | Idle | Dark Blue | `RSS/Antenna` |
| **Streaming** | Active | Light Blue (Blinking) | `Stop` |
| **HTTP Status** | OK | **Green** | "OK" |
| **HTTP Status** | Retrying| **Yellow** | "RETRY (X/N)" |
| **HTTP Status** | Offline | **Red** | "TIMEOUT" |

---

## 🛠️ Technical Details
* **Protocol:** HTTPS GET requests via `HttpClient`.
* **Data Parsing:** Lua Pattern Matching to extract real-time data from Matrox SDK strings.
* **UI Engine:** Dynamic manipulation of object properties (`Color`, `Style`, `Legend`).

---

## 📜 Licensing and Credits

### Credits
* **Lead Developer:** Daniel Lorenzo Silveira Alves.
* **Project Idealization:** Bruno Mariani de Melo.

### License
Distributed under the **MIT License**. See the `LICENSE` file for more information. 

> *Disclaimer: This plugin is provided "as is", without warranty of any kind. It is not an official product of Matrox.*

---
*Developed with ❤️ for the AV Community.*
