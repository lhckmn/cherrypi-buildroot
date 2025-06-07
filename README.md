# Old archived version! See new repo with containerized setup: ![v3s_cherrypi_builroot](https://github.com/lhckmn/v3s_cherrypi_builroot)


# LCTech CherryPi Allwinner V3s Buildroot Config

## Brief description
This is an external configuration for building a minimal Linux for the [LCTech CherryPi](https://linux-sunxi.org/CherryPi_PC_V3S) based on the Allwinner V3s SoC.

So far it boots into the shell and outputs the logs of U-Boot and Linux to a LCD connected via the 40-pin connector.\
The LCD is enabled and initialized in U-Boot and the simple-framebuffer is then handed over to Linux.\
Linux is configured to use the simple-framebuffer with DRM.

## Features
The following features of the board are integrated or to be integrated:
- [x] LCD support
- [ ] Wifi (onboard ESP8089)
- [ ] Audio
- [ ] Ethernet
- [ ] Buttons
- [ ] Flash (onboard W25Q128)

## Using the external config
To use this external config, clone this repo and your favourite version of Buildroot (2025.02 should work) next to it.\
Execute this to start your build:
```console
builduser@debian:~$ cd buildroot

builduser@debian:~$ make BR2_EXTERNAL=../external_configs/cherrypi cherrypi_defconfig

builduser@debian:~$ make
```

## Credits
The patch for the integration of the LCD into U-Boot is fully based on the great work of mcerveny. I adapted his patch to work with U-Boot 2025.04.\
See his repo: [mcerveny/u-boot/tree/simplefb_v3s_v2](https://github.com/mcerveny/u-boot/tree/simplefb_v3s_v2)
