# Atlavox Beacon
**Sovereign Communication Node. Hardware-Enforced Trust.**

> **Project Status:** 🛠️ **In Development / Architectural Phase**
> *Atlavox Beacon is currently in the design and prototyping phase. We are laying the groundwork for a secure, auditable communication device. Contributions, feedback, and architectural discussions are highly encouraged.*

## The Mission
To provide a platform where the user controls the **Root of Trust**. We move security away from the fragile software layer and anchor it into **auditable hardware**.

## Key Features (The "Level 3" Approach)
* **Immutable Root of Trust:** Dual-chip architecture. The primary bootloader is anchored in physically write-protected hardware (Immutable), serving as the unwavering Root of Trust.
* **Verified Boot:** The immutable core cryptographically verifies the secondary BIOS/Bootloader storage before execution, ensuring a clean, verified state every time.
* **Hardware Integrity:** Integrated Secure Element (HSM) for key storage and cryptographic operations. 
* **Hardware-First Security:** Physical tamper-detection loops that purge master keys upon casing intrusion.
* **True Randomness:** Dedicated hardware TRNG (True Random Number Generator) for high-entropy, unpredictable cryptographic keys—essential for secure web browsing (HTTPS/TLS) and private communication, protecting against PRNG-based predictability attacks.
* **Privacy Kill-Switch:** Physical hardware switch to power-gate (disable) one M.2 expansion slot for ultimate privacy control.
* **Open Everything:** From KiCad schematics to U-Boot config, we share every layer. No "PDF-only" hardware here.

## Architecture
Atlavox Beacon is built on the RISC-V (TH1520) architecture, utilizing a custom-designed carrier board to enforce our security chain.

* **SoC:** T-Head TH1520 (RISC-V, Quad-core C910 @ 2.0GHz+)
* **RAM:** LPDDR4X (Integrated on SoM)
* **Boot Chain (Dual-Chip Storage):** * **1x Immutable Root Chip:** Physically write-protected storage containing the Core Root of Trust for Measurement (CRTM). This is the permanent, unalterable foundation of the system.
    * **1x BIOS/Bootloader Storage:** Writable non-volatile storage containing the secondary Bootloader/BIOS (U-Boot/OpenSBI). This code is cryptographically verified by the Immutable Root chip upon every boot.
* **Secure Element (HSM):** ATECC608B. Dedicated hardware-isolated cryptographic processor for:
    * Secure Key Storage (Master Keys never leave the chip).
    * Hardware-based TRNG (True Random Number Generator).
    * Secure cryptographic signing and verification operations.
* **Expansion:** * 2x M.2 Slots (PCIe 2.0).
    * Physical Hardware Switch to power-gate M.2 Slot 2 (Privacy Control).
* **I/O Connectivity:** 1x USB-C (Power/Data), 1x USB-A, 1x Gigabit Ethernet, 1x 3.5mm Audio.
* **Display/Camera:** 1x MIPI-DSI (Display) & 1x MIPI-CSI (Camera) interfaces.
* **OS:** Linux-first (Native Linux apps via Flatpak + Waydroid for compatibility).

## Roadmap
- [ ] Finalize Carrier Board Schematics (KiCad)
- [ ] Prototype Secure Boot-Gate Implementation
- [ ] Verify Tamper-Detection Circuitry
- [ ] Initial Bring-up (U-Boot)

## Getting Involved
We are currently in the **Architectural Phase**. We are looking for:
1. **PCB Designers** (KiCad proficiency)
2. **Firmware Engineers** (RISC-V, U-Boot experience)
3. **Security Researchers** (Threat modeling, hardening)

Check our [Issues](https://github.com/osama413/atlavox-beacon/issues) to see what we are currently working on.

## Acknowledgments
A massive thank you to the global **RISC-V community**, the developers, and all open-source contributors. This project stands on your shoulders. Your dedication to creating transparent, verifiable, and accessible technology makes the Atlavox Beacon possible. We build this together, for the benefit of everyone.

## Licensing
- **Hardware:** CERN Open Hardware License Version 2 (Strongly Reciprocal).
- **Software/Firmware:** GNU General Public License v3.0 (GPLv3).

---
*Project Lead Note: I'm Osama. I'm building this because I believe in device ownership. This is a project for those who want to reclaim their hardware.*

**This project is not mine, not yours, it's nobody's and everyone's.**
