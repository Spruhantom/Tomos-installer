# Tom OS / PunkSway Installer

A separate home for the guided installer used by Tom OS (PunkSway), an Arch Linux desktop built around Niri, DMS/Dux Shell and Ly.

## Important status

This repository contains the installer source and theme configuration. It is not a bootable ISO by itself. The installer is designed to run from the matching PunkSway Archiso live environment, which supplies the Arch installation tools and the staged theme files.

**Disk warning:** the installer repartitions and formats the selected drive. It permanently erases the selected drive after two confirmations, including typing `ERASE`. Back up data first. Use a spare virtual machine for testing.

## Supported installation

- UEFI boot only (not legacy BIOS)
- GPT partition table
- 1 GiB FAT32 EFI System Partition mounted at `/boot`
- ext4 root partition
- Arch Linux `linux` kernel
- Niri compositor, DMS/Dux Shell, Ly login manager
- NetworkManager, PipeWire, Foot terminal and Firefox by default
- UK keyboard and `Europe/London` timezone defaults
- GRUB and Tom OS Plymouth theme

## Run from the matching live ISO

Boot the PunkSway USB in UEFI mode, connect to the internet, then run:

```bash
sudo /usr/local/bin/punksway-installer
```

Do not run the installer from an ordinary installed Linux desktop. It expects the Archiso environment and staged files under `/usr/share/plymouth/themes/tomos` and `/usr/share/punksway/grub-theme`.

## Repository layout

- `installer/punksway-installer` — guided UEFI installer
- `themes/grub/theme.txt` — installed-system GRUB theme
- `themes/plymouth/tomos.plymouth` — Plymouth theme descriptor
- `themes/plymouth/tomos.script` — Plymouth splash and progress script

## Testing

Run the static checks with:

```bash
bash -n installer/punksway-installer
```

A successful syntax check does not prove a real install works. Test the complete ISO and installation in a disposable UEFI virtual machine before using it on physical hardware.

## Related project

The Archiso image, package manifest, wallpaper/splash renderers and build scripts remain in [Tom OS / PunkSway](https://github.com/Spruhantom/tomos-ubuntu).
