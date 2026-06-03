# Forness Hardened

**Sovereign Communication Node | Hardware-Enforced Trust**

> "This project is not mine, not yours, it's nobody's and everyone's."

The **Forness Hardened** is an open-hardware RISC-V communication device designed to reclaim sovereignty over personal hardware. We eliminate proprietary black boxes by anchoring the entire boot-chain and security lifecycle in auditable, physical hardware.

---
## 🤝 Join the Project
We are currently in the **Architectural Design Phase**, finalizing KiCad schematics and the cryptographic gate logic.

* **We need help with:**
  * **PCB Design:** High-speed differential signaling (PCIe/USB 3.0).
  * **Firmware:** RISC-V U-Boot and OpenSBI implementation.
  * **Security:** Fault injection analysis and tamper-protection hardening.

## 🔒 The "Vault" Architecture
We move beyond software-based security. The Forness Hardened utilizes a tripartite boot architecture to ensure your device is immune to compromise, even with physical access. 

**Zero-Boot Policy:** The device remains in a hard-reset state until the user provides a valid authentication code.

| Component | Type | Role |
| :--- | :--- | :--- |
| **Primary BIOS** | Writable | Standard boot sequence. Locked until user authentication. |
| **Recovery BIOS** | WORM | Immutable, fail-safe environment. Locked until user authentication. |
| **HSM (ATECC608B)** | Cryptographic Gate | The "Vault Key." Physically isolates the bus from the CPU until authenticated. |

### The Boot Flow:
1. **Power-On:** Processor is held in **Hard Reset**. Only the HSM and the Authentication Interface (Keypad/Input) are active.
2. **Authentication:** The user provides a valid code. 
3. **Verification:** The HSM validates the code and the cryptographic signature of the chosen BIOS (Primary or Recovery).
4. **Hardware Interlock:** Upon success, the HSM closes the physical gate (via MUX/Load Switch) to the SPI/QSPI bus.
5. **Boot:** The processor is released from reset and executes the BIOS.

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
* **Hardened Boot:** By combining WORM (Write Once) memory for recovery and HSM-gated access, we ensure that "Evil Maid" attacks cannot re-flash or bypass your environment.

## 🐧 Software Philosophy
We prioritize long-term maintainability and digital freedom:
* **Base OS:** Alpine Linux (Security-focused, `musl` libc).
* **Upstream First:** We aim for mainline Linux kernel support to ensure device longevity.
* **No Proprietary Blobs:** If we cannot audit it, we do not use it.

---
*Built for those who value absolute control over their digital footprint.*

## Third-Party Component Attribution & Disclaimer and License(s)

The Forness Hardened design (schematics, PCB layout, and firmware architecture) is released under the **CERN Open Hardware License v2 (Strongly Reciprocal)** and **GPLv3**.

Please note that this license applies exclusively to the Forness Hardened design files and our original work. All third-party hardware components (such as the T-Head TH1520 SoC, Quectel RM500Q modem, Microchip ATECC608B HSM, and others) are the intellectual property of their respective manufacturers.

* **No Ownership Claims:** We make no claims of ownership, rights, or control over these third-party components.

* **Component Licenses:** Use of these components is subject to the terms, intellectual property rights, and licenses provided by their respective manufacturers. 

* **Disclaimer:** We are not affiliated with, endorsed by, or representing these manufacturers. References to these components are provided solely for technical identification.
