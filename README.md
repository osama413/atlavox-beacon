# Forness Hardened

**Sovereign Communication Handset | 100% Open-Source Hardware**

> "If you cannot audit every gate, you do not own the device."

The **Forness Hardened** is an open-hardware RISC-V handset. Unlike "open-source" projects that hide their GPU or modem firmware in proprietary blobs, the Forness Hardened is built on **verifiable, open-silicon architectures**. We refuse to include any component that requires closed-source binary blobs.

---

## 🔒 The "Vault" Architecture
Our commitment to 100% transparency means every component, from the CPU to the GPU and modem interface, is selected based on **public RTL and open-source driver availability.**

| Component | Type | Role |
| :--- | :--- | :--- |
| **SoC/GPU** | FPGA-based (e.g., VexRiscv) | Full RTL transparency; no hidden binary blobs. |
| **Boot-Chain** | OpenSBI + Linux | Fully auditable boot-chain. |
| **HSM** | Open-source RTL HSM | Hardware-level gatekeeping, fully auditable logic. |

### The "No-Blob" Guarantee:
* **GPU Transparency:** We utilize GPU architectures with **open-source drivers (Mesa/Gallium3D)** and open-source RTL/firmware. No closed-source drivers allowed.
* **Modem Freedom:** We reject proprietary modem firmware. We utilize **SDR (Software Defined Radio)** interfaces to allow for an entirely open-source GSM/5G protocol stack implementation.
* **Boot-Chain:** The device remains in a hard-reset state until the user provides valid physical authentication, at which point an entirely open, audited boot-sequence begins.

---

## 🛠 Hardware Specifications
*Base design built for 100% auditability.*

| Subsystem | Specification | Note |
| :--- | :--- | :--- |
| **SoC/GPU** | FPGA-SoC (e.g., ECP5 or newer) | Full RTL source code provided; no binary blobs. |
| **Radio** | SDR-based (Software Radio) | Replaces proprietary modems with open-source stacks. |
| **Security** | Open-Source RTL HSM | Verifiable cryptographic hardware. |
| **Privacy** | Physical Kill-Switches | Hardwired mechanical power-gates. |

---

## 📱 Privacy-by-Design
* **Full Transparency:** Every line of code running on the hardware, including GPU acceleration and radio communication, is open-source and auditable.
* **Blob-Free:** We actively exclude any hardware requiring binary blobs (drivers provided by manufacturers without source code).
* **Hardwired Trust:** All security controls are implemented at the logic level, not via software hooks that can be bypassed.

---

## 🐧 Software Philosophy
* **Base OS:** Alpine Linux (`musl` libc).
* **Mainline-First:** Every driver must be upstreamed to the mainline Linux kernel.
* **Zero Blobs:** We prioritize hardware freedom over raw performance. If a piece of hardware is fast but "closed," it is rejected.

---
*Built for those who value freedom above all else.*

## License & Attribution
The Forness Hardened design is released under the **CERN Open Hardware License v2 (Strongly Reciprocal)** and **GPLv3**.


""we will learn a lot from existing projects like pine64 librem and many more big thanks 
