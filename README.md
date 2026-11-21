# macOS Tahoe (Darwin 25) on ASUS VivoBook M409DA (OpenCore)

OpenCore configuration, notes, and setup documentation for running **macOS Tahoe** on the **ASUS VivoBook M409DA** (also sold as **X409DA**).

## Hardware Specifications

| Component | Specification |
| :--- | :--- |
| **Laptop** | ASUS VivoBook M409DA / X409DA |
| **CPU** | AMD Ryzen 5 3500U (Picasso) |
| **iGPU** | AMD Radeon Vega 8 |
| **Memory** | 8 GB DDR4 (2x 4 GB dual-channel) |
| **Storage** | 256 GB Samsung PM991 NVMe SSD |
| **Wi-Fi** | Intel Wireless-AC 8265 |
| **Audio** | Realtek HDA / AMD ACP (Audio CoProcessor) |

## What Works & Known Limitations

### Working
- **Boot & Graphics:** Boots macOS Tahoe via OpenCore with **NootedRed** hardware acceleration on Radeon Vega 8 (using a static wallpaper and UI motion/transparency reductions for smooth WindowServer performance).
- **Storage:** Native macOS Tahoe NVMe handling (no `nvme=-1` or `PC711ProbeForce.kext` needed on the final setup) across a full single-disk APFS layout after cloning/resizing.
- **Wi-Fi:** Intel AC 8265 connectivity via `itlwm.kext` paired with **HeliPort**.
- **Audio Output:** Speakers and 3.5mm headphone jack output (depending on audio setup/workaround used on Darwin 25).
- **DRM Streaming (Workaround):** Netflix, Prime Video, and other encrypted streams work in **Google Chrome, Microsoft Edge, or Firefox** via software **Widevine**.

### Not Working / Limitations
- **Internal Microphone:** Built-in array microphone over the AMD ACP I2S bus is unsupported on macOS (use an external mic/adapter or dual-boot/VM when needed).
- **Safari / Orion DRM:** Safari and WebKit-based browsers like Orion fail on FairPlay-protected streams due to the lack of an Apple/Intel Secure Enclave on AMD Ryzen.

## Repository Structure

```text
.
├── EFI/
│   ├── BOOT/
│   └── OC/
│       ├── ACPI/
│       ├── Kexts/
│       ├── Tools/
│       └── config.plist
├── .gitignore
└── README.md

