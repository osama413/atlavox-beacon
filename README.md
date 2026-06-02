# Atlavox Beacon

**Sovereign Communication Node | Hardware-Enforced Trust**

> "Security is not a feature; it is an architecture."

The Atlavox Beacon is a RISC-V based communication device designed to reclaim sovereignty over personal hardware. We eliminate proprietary black boxes by anchoring the entire boot-chain and security lifecycle in auditable, physical hardware.

---

## 🔒 The "Vault" Architecture (Secure Boot Chain)
We move beyond software-based security. The Atlavox Beacon utilizes a tripartite boot architecture to ensure your device is impossible to compromise, even with physical access.

| Component | Type | Role |
| :--- | :--- | :--- |
| **Primary BIOS** | Writable | Standard boot sequence for daily operations and updates. |
| **Recovery BIOS** | WORM (Write Once) | Immutable, fail-safe environment for system recovery. |
| **HSM (ATECC608B)** | Cryptographic Gate | The "Vault Key." Physically gates access to the Recovery BIOS. |

### The Boot Flow:
1. **Verification:** Upon power-on, the device performs a hardware-level integrity check.
2. **Gated Recovery:** If the Primary BIOS fails or a recovery is triggered, the system attempts to boot the WORM-Recovery environment. 
3. **The Lock:** Access to the Recovery BIOS bus is physically/logically blocked by the HSM until a valid user-authentication code is processed. This prevents unauthorized tampering or recovery-mode exploits.

---

## 🛠 Hardware Specifications

| Subsystem | Specification | Note |
| :--- | :--- | :--- |
| **SoC** | T-Head TH1520 (RISC-V) | Quad-core, mainline kernel targeted. |
| **Connectivity** | M.2 Key B Slot | Designed for Quectel RM500Q (5G/LTE). |
| **Storage** | M.2 Key M Slot | NVMe expansion. |
| **Security** | Microchip ATECC608B | HSM for keys, TRNG, and boot-gating. |
| **Privacy** | Physical Power-Gates | Mechanical switches to cut power to modems. |

---

## 📱 Privacy-by-Design
* **Physical Kill-Switches:** Dedicated power-gating circuitry allows for the physical disconnection of the 5G modem. No software exploit can bypass a broken circuit.
* **Hardened Boot:** By combining WORM (Write Once) memory for recovery and HSM-gated access, we ensure that an "Evil Maid" attack cannot re-flash or bypass your recovery environment.

## 🐧 Software Philosophy
We prioritize long-term maintainability and freedom:
* **Base OS:** Alpine Linux (Security-focused, `musl` libc).
* **Upstream First:** We aim for mainline Linux kernel support to ensure device longevity.
* **No Proprietary Blobs:** If we cannot audit it, we do not use it.

## 🤝 Project Status & Contribution
We are currently in the **Architectural Design Phase**, finalizing KiCad schematics and the cryptographic gate logic.

* **Looking for:** PCB designers (High-speed differential signaling), Firmware engineers (RISC-V/OpenSBI/U-Boot), and Security Researchers (Fault injection/Tamper analysis).

---
*Built for those who value absolute control over their digital footprint.*

**License:** CERN Open Hardware License v2 (Strongly Reciprocal) | GPLv3
