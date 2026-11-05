<div align="center">

# TasiaOS

### An experimental, open-source NT operating system

**An independent fork of [LiberNT](https://github.com/LiberNT/LiberNT), exploring modern NT compatibility and a more customizable desktop.**

[![License: GPL 3.0](https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge&logo=gnu)](COPYING)
[![Repository](https://img.shields.io/badge/GitHub-tasia--ai%2FTasiaOS-181717?style=for-the-badge&logo=github)](https://github.com/tasia-ai/TasiaOS)

[Source code](https://github.com/tasia-ai/TasiaOS) · [Issues](https://github.com/tasia-ai/TasiaOS/issues) · [Releases](https://github.com/tasia-ai/TasiaOS/releases)

</div>

> [!IMPORTANT]
> **TasiaOS is experimental software, not a production-ready Windows replacement.**
> Test builds in a virtual machine or on spare hardware. Do not install it on a machine or drive containing data you cannot afford to lose.

## About TasiaOS

**TasiaOS** is an open-source operating-system project based on the NT architecture. It is forked from **LiberNT**, with the aim of building on upstream work while exploring TasiaOS-specific features, customization, and improvements.

The upstream project works toward Windows 11 compatibility across modern 64-bit architectures. **Compatibility is a goal, not a guarantee**: individual applications, hardware drivers, and devices may not work yet.

This repository currently inherits code, documentation, assets, and build infrastructure from LiberNT. Some internal filenames, executable names, build targets, and branding assets may therefore still say `LiberNT` or `libernt`. Those technical names have deliberately **not** been changed in this README unless the underlying implementation is known to support the change.

### Project goals

- Build an open-source NT-based operating system.
- Improve stability, compatibility, and hardware support through testing.
- Explore a customizable desktop and original TasiaOS features.
- Preserve upstream credits, license notices, and transparent development history.

## What the codebase includes

The repository is based on LiberNT and includes work in these areas. **The presence of code does not mean every feature is complete or fully operational.**

| Area | Description |
| --- | --- |
| NT architecture | Kernel, hardware abstraction layers, system services, and Win32-related components. |
| Boot support | BIOS/UEFI-related boot infrastructure and loaders. |
| Hardware | Drivers and infrastructure for storage, buses, input, networking, and other devices. |
| Architectures | Upstream build support for amd64, arm64, riscv64, and selected additional targets. |
| Desktop | User-mode components, graphical subsystem, applications, resources, and themes. |
| Build system | Configurable source builds, including Clang-based workflows. |

## Getting started

### 1. Get the source

```bash
git clone https://github.com/tasia-ai/TasiaOS.git
cd TasiaOS
```

The main development branch of this repository is currently `main-nt10`.

### 2. Install the build prerequisites

The inherited build system uses **RosBE**, alongside common build tools such as Git, CMake, Ninja, Flex, and Bison. The upstream bootstrap command is:

```bash
curl -fsSL https://raw.githubusercontent.com/LiberNT/libernt-build-toolchain/main/rosbe-unix-bootstrap.sh | sh
```

> [!NOTE]
> This downloads and executes a toolchain installer maintained by the **upstream LiberNT project**, not by TasiaOS. Review the script and its source before using it. Linux and macOS are supported by the upstream workflow; on Windows, WSL2 is recommended.

### 3. Configure a build

```bash
./configure.sh
```

The upstream default is an amd64 Debug build with Clang, configured under `output-Clang-amd64-debug`.

Examples:

```bash
./configure.sh -a arm64
./configure.sh -a amd64 --release
./configure.sh menuconfig
```

### 4. Build an image

```bash
cd output-Clang-amd64-debug
ninja liberntimg
```

The following **inherited** build targets retain their existing names:

| Command | Output | Purpose |
| --- | --- | --- |
| `ninja bootcd` | `bootcd.iso` | Boot/install CD image. |
| `ninja liberntimg` | `LiberNT.img` | Preinstalled disk image. |
| `ninja liberntvhd` | `LiberNT.vhd`, `LiberNT.vhdx` | Virtual-machine disk images. |

> [!WARNING]
> These commands and filenames describe the upstream build system. TasiaOS build results have not been independently verified by this README. Image creation and installation may overwrite disks or partitions; always double-check the target device.

For additional installation details, see [INSTALL.md](INSTALL.md) and the [upstream LiberNT documentation](https://github.com/LiberNT/LiberNT).

## Repository structure

```text
TasiaOS/
├── base/             # Applications, services, setup, and shell
├── boot/             # Boot-related components
├── bootloader/       # Boot managers and loaders
├── dll/              # User-mode libraries
├── drivers/          # Hardware drivers
├── hal/              # Hardware abstraction layers
├── media/            # Graphics, themes, fonts, sounds, and branding
├── modules/          # Optional applications and tests
├── ntoskrnl/         # NT kernel and executive
├── sdk/              # Headers, libraries, and build tools
├── submodules/       # External dependency integration
├── subsystems/       # System subsystems
├── win32ss/          # Windowing and graphics components
└── configure.sh      # Build configuration entry point
```

## Contributing

Contributions, testing, and bug reports are welcome. Please use the [TasiaOS issue tracker](https://github.com/tasia-ai/TasiaOS/issues) for this fork and review [CONTRIBUTING.md](CONTRIBUTING.md) where applicable.

**Clean-room development matters.** Do not submit proprietary or leaked Microsoft Windows source code, or code copied from protected implementations without appropriate permission and license compatibility. Follow the project's license and upstream contribution requirements.

AI-assisted coding or review is welcome when changes can be examined, tested, and attributed appropriately. AI-generated code should not be assumed correct without verification.

## License and attribution

TasiaOS is based on **[LiberNT](https://github.com/LiberNT/LiberNT)**. The original project was started by **Ahmed Arif**, with contributions and maintenance from the wider LiberNT team, including **Ostap Brehin** and **Vivyy**. The original authors and contributors retain credit for their work.

This repository includes code licensed under the **[GNU General Public License, version 3](COPYING)**, alongside components under other licenses as identified in their source files and accompanying license texts. See [CREDITS.md](CREDITS.md), [COPYING2](COPYING2), [COPYING.LIB](COPYING.LIB), and [COPYING.ARM](COPYING.ARM) where relevant.

**TasiaOS is an independent fork.** It is not presented as an official LiberNT release and is not affiliated with, endorsed by, or sponsored by Microsoft. Windows is a trademark of Microsoft Corporation.

---

<div align="center">

**TasiaOS — a new adventure built on open-source foundations.** 🍕

[GitHub](https://github.com/tasia-ai/TasiaOS) · [Report an issue](https://github.com/tasia-ai/TasiaOS/issues)

</div>
