# EFI-Hackintosh-for-Asus-X505ZA-macOS-Sequoia-
This repository contains a pre-configured EFI folder for the Asus X505ZA laptop with an AMD Ryzen processor. The EFI files are designed to enable the installation and operation of macOS Sequoia on this device. This project is intended for advanced users who are familiar with Hackintosh setups and OpenCore bootloader configurations.

---

## Laptop Specifications
- **Model**: Asus X505ZA
- **Processor**: AMD Ryzen 3 2200U (Base 2,5 GHz/Turbo Boost 3,4 GHz)
- **Integrated GPU**: AMD Radeon Vega 3
- **RAM**: 8GB DDR4 (Upgradable)
- **Storage**: 256GB SSD (Replaceable)
- **Display**: 15.6" FHD (1920x1080) IPS
- **Networking**: Realtek Ethernet + Wi-Fi (Non-compatible with macOS, replacement recommended)
- **Audio**: Realtek ALC256 (Supported with AppleALC)
- **Input**: Keyboard and Touchpad (Supported with VoodooPS2)

---

## What Works
- **Processor**: Full support for AMD Ryzen CPUs with proper kernel patches.
- **Integrated Graphics**: AMD Vega 8 iGPU is partially supported with WhateverGreen.kext, but hardware acceleration is limited due to macOS's lack of native support for AMD GPUs.
- **Audio**: Internal speakers and headphone jack work using AppleALC.kext.
- **Networking**: Ethernet works with RealtekRTL8111.kext. Wi-Fi requires a compatible external dongle (e.g., Broadcom-based cards).
- **Bluetooth**: Works with compatible external dongles.
- **Touchpad**: Basic gestures and multi-touch are supported with VoodooPS2Controller.kext.
- **USB Ports**: All USB ports are functional after proper mapping using USBInjectAll.kext and custom SSDTs.
- **Battery Status**: Battery percentage and power management are supported with ACPIBatteryManager.kext.

---

## What Doesn't Work
- **AMD Vega 3 iGPU**: No hardware acceleration for AMD GPUs in macOS. This limits graphical performance and compatibility with certain apps.
- **Internal Wi-Fi Card**: Most stock Wi-Fi cards in laptops are not supported in macOS. A replacement or external dongle is required.
- **HDMI Output**: HDMI output is not functional due to the lack of AMD GPU support.
- **Fingerprint Sensor**: Not supported in macOS.

---

## Installation Guide
### Prerequisites
1. **USB Flash Drive**: A 16GB or larger USB drive.
2. **macOS Installer**: Download macOS Sequoia from the App Store (requires a real Mac or existing Hackintosh).
3. **OpenCore Bootloader**: Familiarize yourself with OpenCore by reading the [official guide](https://dortania.github.io/OpenCore-Install-Guide/).

### Steps
1. **Create macOS Installer**:
   - Use a tool like [GibMacOS](https://github.com/corpnewt/gibMacOS) to download the macOS installer.
   - Format the USB drive as GUID Partition Map (GPT) and create a bootable installer using Terminal or a tool like [BalenaEtcher](https://www.balena.io/etcher/).

2. **Replace EFI Folder**:
   - Mount the EFI partition of the USB drive.
   - Replace the existing EFI folder with the one provided in this repository.

3. **Configure BIOS Settings**:
   - Disable **Secure Boot**.
   - Enable **AHCI Mode** for SATA.
   - Set the boot mode to **UEFI**.
   - Disable **CSM (Compatibility Support Module)**.

4. **Boot from USB**:
   - Insert the USB drive into your laptop.
   - Boot into the OpenCore boot menu and select the macOS installer.

5. **Install macOS**:
   - Follow the on-screen instructions to install macOS Sequoia.
   - After installation, boot into macOS and complete the initial setup.

6. **Post-Installation**:
   - Mount the EFI partition of your internal drive.
   - Copy the EFI folder from the USB drive to the EFI partition of your internal drive.
   - Install necessary kexts for Wi-Fi, Bluetooth, or other peripherals if needed.

---

## EFI Folder Structure
The EFI folder is organized as follows:
- **ACPI**: Contains SSDT and DSDT files for power management, USB mapping, and other hardware-specific fixes.
- **Kexts**: Includes essential kernel extensions for hardware compatibility:
  - **Lilu.kext**: A foundational kext for many other extensions.
  - **WhateverGreen.kext**: Handles GPU-related fixes.
  - **AppleALC.kext**: Enables audio support.
  - **VoodooPS2Controller.kext**: Enables touchpad and keyboard support.
  - **RealtekRTL8111.kext**: Enables Ethernet support.
  - **VirtualSMC.kext**: Emulates Apple's SMC for better compatibility.
- **Drivers**: Contains OpenCore drivers such as:
  - **OpenRuntime.efi**: Required for memory management.
  - **HfsPlus.efi**: Required for reading HFS+ file systems.
- **Tools**: Includes utilities like **OpenShell.efi** for debugging.
- **Config.plist**: The main configuration file for OpenCore. It includes settings for boot arguments, kernel patches, and device properties.

---

## Credits
This project would not be possible without the efforts of the following individuals and communities:
- **OpenCore Team**: For developing the OpenCore bootloader.
- **AMD OS X Community**: For providing kernel patches and support for AMD CPUs.
- **Apple**: For macOS (obviously).
- **Kext Developers**: For creating and maintaining essential kernel extensions.

---

## Disclaimer
This project is provided **as-is**, without any warranties or guarantees. Hackintoshing is an experimental process and may result in data loss, hardware damage, or other issues. Proceed at your own risk. I am not responsible for any problems that may arise from using this EFI configuration.

---

## How to Contribute
If you encounter any issues or have suggestions for improvement, feel free to:
- Open an **Issue** on GitHub.
- Submit a **Pull Request** with your changes.
- Share your experience and feedback in the **Discussions** section.

---

## License
This repository is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for more details.

---

## Final Notes
- **Regular Updates**: macOS updates may break functionality. Always back up your data before updating.
- **Customization**: This EFI is tailored for the Asus X505ZA. If you have a different laptop or hardware configuration, adjustments may be necessary.
- **Community Support**: Join Hackintosh communities like [r/Hackintosh](https://www.reddit.com/r/hackintosh/) or [InsanelyMac](https://www.insanelymac.com/) for additional help and resources.
