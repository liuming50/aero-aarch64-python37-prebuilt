# aero-aarch64-python37-prebuilt
Prebuilt python3.7 modules for Aero aarch64

# Prebuilt python packages list

```
python3-adafruit-gpio
python3-adafruit-pureio
python3-asyncio
python3-audio
python3-codecs
python3-compile
python3-compression
python3-core
python3-crypt
python3-ctypes
python3-curses
python3-datetime
python3-difflib
python3-distro
python3-distutils
python3-email
python3-fcntl
python3-gpg
python3-html
python3-iniparse
python3-inputimeout
python3-io
python3-jetson-gpio
python3-jetson-stats
python3-json
python3-logging
python3-math
python3-mime
python3-misc
python3-mmap
python3-multiprocessing
python3-netclient
python3-netserver
python3-numbers
python3-pickle
python3-pi-ina219
python3-pkg-resources
python3-pkgutil
python3-plistlib
python3-pprint
python3-profile
python3-pydoc
python3-pygps
python3-pynmeagps
python3-pyrtcm
python3-pyserial
python3-pyubx2
python3-rpm
python3-setuptools
python3-shell
python3-six
python3-smbus
python3-smbus2
python3-spidev
python3-sqlite3
python3-stringold
python3-terminal
python3-threading
python3-unittest
python3-unixadmin
python3-xml
```

# How to generate it

Build qemuarm64 with the followings in local.conf:

```
DISTRO_FEATURES_remove = "wayland ptest"
DISTRO_FEATURES_append = " x11 vulkan opengl benchmark python multiarch pam systemd polkit"

VIRTUAL-RUNTIME_init_manager = "systemd"
DISTRO_FEATURES_BACKFILL_CONSIDERED = "sysvinit"
VIRTUAL-RUNTIME_initscripts = ""

IMAGE_INSTALL_append = " \
    python3-jetson-stats \
    python3-jetson-gpio \
    packagegroup-self-hosted-sdk \
    python3-distutils \
    python3-venv \
    python3-inputimeout \
    python3-pi-ina219 \
    python3-pip \
    python3-pygps \
    python3-pyserial \
    python3-pyubx2 \
    python3-smbus \
    python3-asyncio \
    python3-audio \
    python3-codecs \
    python3-gpg \
    python3-html \
    python3-iniparse \
    python3-misc \
    python3-mmap \
    python3-profile \
    python3-pydoc \
    python3-six \
    python3-sqlite3 \
    python3-2to3 \
"
```

Find all python3 binaries:

```
$ find tmp/work/aarch64-poky-linux/python3* -name "bin" | grep packages-split.*bin
tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-dbg/usr/bin
tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-pydoc/usr/bin
tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-dev/usr/bin
tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-core/usr/bin
tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-2to3/usr/bin
tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-idle/usr/bin
tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-venv/usr/bin
tmp/work/aarch64-poky-linux/python3-distro/1.7.0-r0/packages-split/python3-distro/usr/bin
tmp/work/aarch64-poky-linux/python3-jetson-stats/4.2.3-r0/packages-split/python3-jetson-stats/usr/bin
tmp/work/aarch64-poky-linux/python3-pip/19.2.3-r0/packages-split/python3-pip/usr/bin
tmp/work/aarch64-poky-linux/python3-setuptools/41.2.0-r0/packages-split/python3-setuptools/usr/bin
```

Find all python3 modules here:

```
tmp/work/qemuarm64-poky-linux/core-image-minimal/1.0-r0/rootfs/usr/lib/python3.7/
```

Copy them to this repository.

```
$ cp -rPf tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-core/usr/bin/python3.7* usr/bin
$ cp -rPf tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-dev/usr/bin/python3.7* usr/bin
$ cp -rPf tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-2to3/usr/bin/2to3-3.7 usr/bin
$ cp -rPf tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-idle/usr/bin/idle3.7 usr/bin
$ cp -rPf tmp/work/aarch64-poky-linux/python3/3.7.17-r0/packages-split/python3-venv/usr/bin/pyvenv-3.7 usr/bin
$ cp -rPf tmp/work/aarch64-poky-linux/python3-distro/1.7.0-r0/packages-split/python3-distro/usr/bin/distro usr/bin/distro3.7 usr/bin
$ cp -rPf tmp/work/aarch64-poky-linux/python3-pip/19.2.3-r0/packages-split/python3-pip/usr/bin/pip3.7 usr/bin
$ cp -rPf tmp/work/aarch64-poky-linux/python3-setuptools/41.2.0-r0/packages-split/python3-setuptools/usr/bin/easy_install-3.7 usr/bin
$ cp -rPf tmp/work/qemuarm64-poky-linux/core-image-minimal/1.0-r0/rootfs/usr/lib/python3.7 usr/lib
```
