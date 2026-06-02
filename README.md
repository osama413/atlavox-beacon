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
* **Open Everything:** From KiCad schematics to U-Boot config, we share every layer. No "PDF-only" hardware here.

## Architecture
Atlavox Beacon is built on the RISC-V (TH1520) architecture, utilizing a custom-designed carrier board to enforce our security chain.

* **SoC:** TH1520 (RISC-V)
* **Secure Element:** ATECC608B (or compatible with integrated TRNG)
* **Boot Chain:** Custom carrier board with Dual-Chip (1x Immutable Root chip, 1x BIOS Storage chip)
* **OS:** Linux-first (Native Linux apps via Flatpak + Waydroid for compatibility)

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

**this project is not mine and not your nobodys and evreones.**
## Licensing
- **Hardware:** CERN Open Hardware License Version 2 (Strongly Reciprocal).
- **Software/Firmware:** GNU General Public License v3.0 (GPLv3).
