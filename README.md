# GA-B75M-D3H Hackintosh

An OpenCore configuration for my custom build with a Gigabyte GA-B75M-D3H motherboard.

## Specs

| Category    | Component                                                    |
| ----------- | ------------------------------------------------------------ |
| Motherboard | Gigabyte GA-B75M-D3H                                         |
| CPU         | Intel® Core™ i5-3470                                         |
| iGPU        | Intel® HD Graphics 2500                                      |
| dGPU        | NVIDIA GeForce GT 730 (GK208B)                               |
| RAM         | 2x 8GB DDR3 1600MHz Kingston KHX1600C10D3L/8GX<br />2x 2GB DDR3 1333MHz Kingston KP223C-ELD |
| Ethernet    | Realtek RTL8111                                              |
| Audio       | Realtek ALC887                                               |
| SATA        | 1x SATA 3, 5x SATA 2                                         |
| USB         | 2x ECHI 7 Series/C216 Chipset Family USB Enhanced Host Controller (0x8086:0x1E26, 0x8086:0x1E2D)<br />1x XHCI controller (macOS won't boot with this enabled) |

## Usage

1. Copy the contents of this repo to your EFI partition.
2. The `config.plist` is missing `PlatformInfo` details. Follow the [Dortania guide](https://dortania.github.io/OpenCore-Install-Guide/config.plist/ivy-bridge.html#platforminfo) to generate serials, using the `iMac15,1` model.
3. Update any kexts that you want to update.
4. Check the included SSDTs to make sure they match your ACPI information (it can change between motherboard variants and UEFI versions). Use the [Dortania guide](https://dortania.github.io/Getting-Started-With-ACPI/).
5. If you plan to use this on a USB drive, temporarily change [ScanPolicy](https://dortania.github.io/OpenCore-Install-Guide/config.plist/ivy-bridge.html#misc) to `0`.
6. Add `\EFI\OC\OpenCore.efi` as a UEFI boot option with a tool like `efibootmgr` on Linux.
7. Set the UEFI settings described below.

## Required UEFI settings

- Enable Internal Graphics: Yes (required for things like hardware video decoding)
- Pre-allocated IGPU memory (DVMT-Prealloc): 64MB
- CSM: Never
- XHCI mode: Disabled (macOS will not boot otherwise)

## Known issues

- USB 3 does not work; if XHCI is enabled, macOS refuses to boot.