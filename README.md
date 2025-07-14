# OpenWRT Image Builder for homelab

A repository with scripts and GitHub Action for automatic builds of a customized OpenWRT image for homelab purposes (router and app server).

IMPORTANT: This repository is NOT a fork of OpenWRT and NOT intended for a wide audience or production environments.

## Motivation

While an official (OpenWRT Firmware Selector)[https://firmware-selector.openwrt.org] provides an option for building customized images,
it has a limitation on a system partition which is 104 MByte.
This imposes a limit on how many packages image can contain.
If you add a "docker", for instance, you immediately hit this limit.
This is a "no go" situation if your aim is to get a ready-to-go image with a lot of packages.

This image builder removes these limits and also provides an offsite place for downloading latest images ready for consumption.

New images are generated on a weekly basis:
GitHub Actions do a weekly checks for a latest OpenWRT release and if there are new, a newer image is built and released.

## Image

The builder produces only images with the following characteristics:

- Image type: Combined-EFI (EXT4)
- System partition size: 512 MByte
- Architecture: Generic x86/64

Images of other type out of scope for this builder.

## Packages

On top of standard OpenWRT packages, these packages added to the images:

- `luci-app-dockerman`: Docker with Web UI
- `luci-app-samba4`: Samba with Web UI
- `luci-app-ddns`: Dynamic DNS with Web UI
- `luci-proto-wireguard`: Wiregward VPN with Web UI
- `btrfs-progs`: BTRFS support
- `avahi-dbus-daemon`: Avahi daemon for mDNS/ZeroConfig
- `kmod-i40e`: Intel X710 network adapter drivers
- `kmod-r8125`: Realtek rtl81925 driver
- `ds-lite`: Support for Dual-Stack Lite (ipv4 in ipv6 tunnel)
- `ethtool-full`: Utility for examining and tuning your ethernet-based network interface
- `btop`: Resource monitor that shows usage and stats for processor, memory, disks, network and processes
- `htop`: Process viewer with terminal UI
- `powertop`: A Linux tool to diagnose issues with power consumption and power management.
- `kitty-terminfo`: Terminfo for kitty, an OpenGL-based terminal emulator
- `nano-full`: A small and simple text editor for use on the terminal.
- `ncdu`: A ncurses-based disk usage viewer.
- `hdparm`: Info and managment of SATA/IDE device parameters
- `nvme-cli`: NVM-Express user space tooling for Linux
- `smartmontools`: Disk SMART info monitoring 
- `mtr-json`: Full screen ncurses traceroute tool With JSON
- `lm-sensors`: Hardware sensors monitoring (temp, fan, etc.)
- `ripgrep`: Search text over files recursively
- `curl`: A HTTP/FTP downloader tool
- `jq`: Lightweight and flexible command-line JSON processor.
- `yq`: Query YAMLs in  comman-line
