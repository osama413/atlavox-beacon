# Atlavox Beacon

**Sovereign Communication Node | Hardware-Enforced Trust**

> "This project is not mine, not yours, it's nobody's and everyone's."

The **Atlavox Beacon** is an open-hardware RISC-V communication device designed to reclaim sovereignty over personal hardware. We eliminate proprietary black boxes by anchoring the entire boot-chain and security lifecycle in auditable, physical hardware.

---

## 🔒 The "Vault" Architecture
We move beyond software-based security. The Atlavox Beacon utilizes a tripartite boot architecture to ensure your device is immune to compromise, even with physical access.

| Component | Type | Function |
| :--- | :--- | :--- |
| **Primary BIOS** | Writable | Standard boot sequence for daily operations & updates. |
| **Recovery BIOS** | WORM | Immutable, fail-safe environment for system recovery. |
| **HSM (ATECC608B)** | Cryptographic Gate | The "Vault Key." Physically gates access to the Recovery BIOS. |

### The Boot Flow:
1. **Integrity Check:** Upon power-on, the device performs a hardware-level integrity check.
2. **Gated Recovery:** If the Primary BIOS fails or a recovery is triggered, the system attempts to boot the WORM-Recovery environment. 
3. **The Lock:** The HSM blocks access to the Recovery bus until a valid authentication code is provided, preventing unauthorized tampering.

---

## 🛠 Hardware Specifications

| Subsystem | Specification | Note |
| :--- | :--- | :--- |
| **SoC** | T-Head TH1520 (RISC-V) | Quad-core, mainline kernel targeted. |
| **Connectivity** | M.2 Key B Slot | Optimized for Quectel RM500Q (5G/LTE). |
| **Storage** | M.2 Key M Slot | NVMe expansion. |
| **Security** | Microchip ATECC608B | HSM for keys, TRNG, and boot-gating. |
| **Privacy** | Physical Kill-Switches | Mechanical power-gates for complete modem isolation. |

---

## 📱 Privacy-by-Design
* **Physical Kill-Switches:** Dedicated power-gating circuitry allows for the physical disconnection of the 5G modem. No software exploit can bypass a broken circuit.
* **Hardened Boot:** By combining WORM (Write Once) memory for recovery and HSM-gated access, we ensure that "Evil Maid" attacks cannot re-flash or bypass your recovery environment.

## 🐧 Software Philosophy
We prioritize long-term maintainability and digital freedom:
* **Base OS:** Alpine Linux (Security-focused, `musl` libc).
* **Upstream First:** We aim for mainline Linux kernel support to ensure device longevity.
* **No Proprietary Blobs:** If we cannot audit it, we do not use it.

## 🤝 Join the Project
We are currently in the **Architectural Design Phase**, finalizing KiCad schematics and the cryptographic gate logic.

* **We need help with:**
  * **PCB Design:** High-speed differential signaling (PCIe/USB 3.0).
  * **Firmware:** RISC-V U-Boot and OpenSBI implementation.
  * **Security:** Fault injection analysis and tamper-protection hardening.

---
*Built for those who value absolute control over their digital footprint.*

**License:** CERN Open Hardware License v2 (Strongly Reciprocal) | GPLv3
