# 🧽 Sessile

![sessile render](.images/render.webp)

[![Build RMK firmware](https://img.shields.io/github/actions/workflow/status/willpuckett/sessile/rmk.yml?style=for-the-badge&logo=rust&label=RMK%20Firmware&color=orange)](https://github.com/willpuckett/sessile/actions/workflows/rmk.yml)
[![Build Case](https://img.shields.io/github/actions/workflow/status/willpuckett/sessile/case.yml?style=for-the-badge&logo=3d-printer&label=Case&color=purple)](https://github.com/willpuckett/sessile/actions/workflows/case.yml)
[![Keymap](https://img.shields.io/github/actions/workflow/status/willpuckett/sessile/keymap.yml?style=for-the-badge&logo=keyboard&label=Keymap&color=blue)](https://github.com/willpuckett/sessile/actions/workflows/keymap.yml)
[![Latest Release](https://img.shields.io/github/v/release/willpuckett/sessile?style=for-the-badge&logo=github&label=Release&color=green)](https://github.com/willpuckett/sessile/releases/latest)
[![License](https://img.shields.io/badge/License-Solderpad%20Hardware%20v2.1-blue?style=for-the-badge&logo=open-source-hardware)](LICENSE)

_Sessile_ is a further exploration of "minimal" finger travel.

## 🤔 What Even Is 'Minimal Finger Travel' Anyway?

Probably the least amount of finger travel would be not moving them at all. That
would be 10 keys...

```math
combos_{10\,keys} = \sum_{r=1}^{10} C(10, r) = 1023
```

...yielding **1023** possible combinations.

More realistically, we might consider excluding cross hand combinations so that
modifiers might be used. That would give us

```math
combos_{5\,keys} = \sum_{r=1}^{5} C(5, r) = 31
```

So, with only 5 keys on both hands, and no cross hand combos, we would have a
total of **62** possible keys per layer—more than sufficient.

I wasn't quite ready to take on learning to type on that though, so just
avoiding lateral reaches seemed like a start. 🙃

## ✨ Features

- 🧩 Sessile uses
  [KLP-Lame keycaps](https://github.com/braindefender/KLP-Lame-Keycaps). Larger
  caps may be tight, especially on the bottom row. I was lazy and didn't model
  the tilted keycaps in the rendering, but they're much nicer for the vertical
  combos.

- 🔋 Uses battery LIR1254. **DO NOT substitute LR44.**

- 🔌 The high speed pins were left available for encoders and _could_ be wired
  in a subsequent revision.

- ⚙️ Built for RMK. Configure using [Vial](https://get.vial.today).

## 🏠 Case

A 3D printable case is available in the
[latest release](https://github.com/willpuckett/sessile/releases/latest)! The
case is designed to sit as low as possible and can be secured with a stroke of
glue stick underneath. Case is generated via ergogen with jscad v2 api.
[Try it out](https://github.com/ergogen/ergogen/pull/159) it's testing 10-20x
faster than @jscad/cli@1.

[![Download Case](https://img.shields.io/badge/Download-3D%20Case-brightgreen?style=for-the-badge&logo=download&logoColor=white)](https://github.com/willpuckett/sessile/releases/latest)

## 📦 Production Files

Ready to manufacture your own board? All production files are included in the
repository:

[![Download Production Files](https://img.shields.io/badge/Download-Production%20Files-orange?style=for-the-badge&logo=file-text&logoColor=white)](board/output/pcbs/jlcpcb/production_files/)

Includes gerbers, BOM, and CPL files for JLC. Finished boards are ~~available~~
[sold out](https://octule.com/listing/1842172090/sessile) till the next batch.

## 🎨 Origin

_Sessile_ was produced using
[studyofhands](https://github.com/willpuckett/studyofhands).

![study of hands](.images/sessile_study.svg)

## 🚀 Firmware

This board is designed for RMK. 😏

### 🦀 RMK

Current RMK build is available in the
[Releases](https://github.com/willpuckett/sessile/releases/latest).

You have a few options to build the firmware yourself.

#### Dev Container + IDE

The repo includes a
[Dev Container](https://containers.dev/)
(`.devcontainer/`) with the pinned Rust toolchain, ARM target, and firmware
build tools already installed.

1. Open this repository in VS Code or Cursor with the Dev Containers extension.
2. Choose **Reopen in Container** when prompted (or run
   **Dev Containers: Reopen in Container** from the command palette).
3. Wait for the container to finish creating (dependencies are fetched
   automatically).
4. Open the **Run and Debug** view, select **Build firmware**, and start it
   (or press <kbd>F5</kbd>).

#### Command line

From a terminal:

```bash
cd rmk && cargo make uf2 --release
```

> [!TIP]
> If you haven't previously used Rust to build software for nRF52840, you may
> need to follow the
> [Setup RMK Environment](https://rmk.rs/guide/user_guide/2-2_local_compilation#setup-rmk-environment)
> instructions.

## 🗺️ Keymap

<div align="center">

![Caster Befuddle Variant](.images/keymap.svg)

Generated with
[keymap-drawer](https://github.com/caksoylar/keymap-drawer/tree/main).

Physical layout imported from KiCad via
[keymap-layout-tools](https://nickcoutsos.github.io/keymap-layout-tools/).

</div>

## 🔌 Matrix Diagram

Sessile uses the following pinout for its matrix:

![sessile_matrix](.images/matrix.svg)

> [!NOTE]
> Referencing
> [this pinout sheet provided by Seeed](https://files.seeedstudio.com/wiki/XIAO-BLE/XIAO-nRF52840-pinout_sheet.xlsx),
> the only two exposed high speed pins P0_04/SDA/D4 & P0_05/SCL/D5 have been
> left available for possible encoders in a subsequent revision.
