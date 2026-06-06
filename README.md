# Windows-bitperfect-tidal-asio-bridge-rme
🎧 Bit-Perfect Audio on Windows with TIDAL (ASIO + RME + VB-Audio Bridge)  

This guide explains how to achieve bit-perfect audio playback from streaming services like TIDAL (or Spotify, etc.) on Windows using ASIO drivers, even when the application does not natively support them.

  ⚠️ Why this setup is needed

By default, applications like **TIDAL** or **Spotify** do not use **ASIO drivers** directly.

This creates a limitation:

* Windows audio stack (WASAPI shared mode) resamples audio
* Your DAC / audio interface (e.g. RME) does NOT automatically switch sample rate
* Result: audio is not truly bit-perfect

To solve this, we bypass the Windows mixer using a virtual ASIO bridge.

---

  🧰 What you need

* TIDAL (or any streaming app)
* A DAC / audio interface with ASIO drivers (e.g. **RME MADIface**, Babyface, etc.)
* VB-Audio Hi-Fi Cable & ASIO Bridge
  [https://vb-audio.com/Cable/](https://vb-audio.com/Cable/)
* Windows PC

---

  🔧 Step 1 — Install VB-Audio Hi-Fi Cable

1. Download and install **VB-Audio Hi-Fi Cable**
2. Reboot your system after installation

This creates a **virtual audio device** that will act as your system output.

---

  🔧 Step 2 — Install ASIO Bridge (VB-Audio)

Install **Hi-Fi Cable & ASIO Bridge** from VB-Audio.

This tool allows routing:

> Windows audio → Virtual cable → ASIO driver (RME interface)

---

  🔧 Step 3 — Set VB-Audio Cable as default output

Go to:

> Windows Sound Settings → Output Device

Select:

* **CABLE Input (VB-Audio Hi-Fi Cable)** as default output

This ensures all system audio (including TIDAL) goes through the virtual cable.

---

## 🔧 Step 4 — Configure ASIO Bridge

Open **VB-Audio ASIO Bridge Control Panel**

Set:

* **Input device:** VB-Audio Hi-Fi Cable
* **Output device (ASIO):** your audio interface ASIO driver
  (e.g. *RME MADIface ASIO*)

---

## 🔧 Step 5 — Configure buffer size

Inside ASIO Bridge:

* Start with **256 samples**
* If stable → try 128 for lower latency
* If you hear clicks/pops → increase buffer

💡 Goal: stable playback without dropouts

---

## 🔧 Step 6 — Configure TIDAL

Open TIDAL settings:

* Activate **Exclusive Mode**
* Disable all software volume normalization / processing
* Ensure output device is:

  * **VB-Audio Hi-Fi Cable**

---

## 🎯 Result: Bit-Perfect Playback

Once everything is configured correctly:

✔ TIDAL sends audio in original quality
✔ ASIO Bridge bypasses Windows resampling
✔ RME interface receives native sample rate
✔ DAC automatically switches frequency (44.1 / 48 / 96 / 192 kHz depending on track)

You now have **true bit-perfect playback** on Windows.

---

## 🧠 Notes

* Spotify does NOT support exclusive mode or true bit-perfect playback
* TIDAL is required for proper sample-rate switching
* Some system sounds may also go through the chain depending on configuration
* Keep Windows sound enhancements disabled

---

## 🚀 Summary

```
TIDAL (Exclusive Mode)
        ↓
VB-Audio Hi-Fi Cable (Virtual Device)
        ↓
VB-Audio ASIO Bridge
        ↓
RME ASIO Driver (MADIface / Fireface / etc.)
        ↓
DAC (Bit-Perfect Output)
