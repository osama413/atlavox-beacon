# Atlavox Beacon

**Sovereign Communication Node. Hardware-Enforced Trust.**

> "This project is not mine, not yours, it's nobody's and everyone's."

Atlavox Beacon is an open-hardware communication device built on RISC-V. We move security away from the fragile software layer and anchor it into **auditable hardware**. Our goal is to reclaim device ownership through transparent design and privacy-by-design.

---

## 🛠 Project Status
**Phase:** Architectural Design & Prototyping
We are currently finalizing the carrier board schematics in KiCad. All architectural decisions are open for community review.

## 🚀 The Architecture

| Component | Specification | Purpose |
| :--- | :--- | :--- |
| **SoC** | T-Head TH1520 (RISC-V Quad-core) | Processing Power |
| **Boot Chain** | Immutable Root + Writable BIOS | Hardware-Enforced Boot |
| **Security** | ATECC608B (HSM) | Key Storage & True Randomness |
| **Connectivity** | M.2 Key B Slot | 5G/LTE (Quectel RM500Q Series) |
| **Storage** | M.2 Key M Slot | NVMe SSD Expansion |
| **Privacy** | Physical Kill-Switch | Power-gating (Modem/M.2) |

## 🔒 Security Features
* **Immutable Root of Trust:** A physically write-protected chip serves as the unalterable foundation for boot verification.
* **Hardware-First Security:** Physical tamper-detection loops that trigger key erasure upon casing intrusion.
* **Secure Element (HSM):** Dedicated hardware isolation for Master Keys. Master Keys never leave the ATECC608B chip.
* **True Randomness:** Dedicated hardware TRNG for high-entropy cryptographic operations.

## 📱 Connectivity & Expansion
* **WWAN:** M.2 Key B Slot designed for high-speed 5G modules (e.g., Quectel RM500Q).
* **Storage:** M.2 Key M Slot for high-speed NVMe storage.
* **Physical Privacy:** Hardware-level power-gating switches to physically disconnect the 5G modem from the power rail when privacy is required.

## 🐧 The Software Vision
We target **Alpine Linux** as the native OS foundation due to its small footprint, security-first design, and `musl` libc efficiency. 
* **Native:** No proprietary blobs. We aim for full mainline kernel support.
* **Compatible:** Waydroid and Flatpak support for legacy application compatibility.
* **Community-Driven:** We rely on and contribute back to the global RISC-V upstream development efforts.

## 🤝 Getting Involved
We are currently in the **Architectural Phase**. We are looking for contributors with expertise in:
1. **PCB Design (KiCad):** Routing high-speed differential pairs (PCIe/USB 3.0).
2. **Firmware Engineering:** RISC-V U-Boot and OpenSBI implementation.
3. **Security Research:** Hardening our boot-gate logic.

*Check our [Issues](https://github.com/osama413/atlavox-beacon/issues) to start contributing.*

## 📜 Licensing
* **Hardware:** CERN Open Hardware License Version 2 (Strongly Reciprocal).
* **Software/Firmware:** GNU General Public License v3.0 (GPLv3).

---
*Built for those who want to reclaim their hardware.*
