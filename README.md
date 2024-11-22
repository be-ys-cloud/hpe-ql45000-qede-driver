# Patched qed driver for linux

**Current kernel version: 6.1**

## Installation

### Dependencies

Install dependencies to build the driver on the system:
build tools and kernel headers.

```sh
apt install build-essential linux-headers-amd64
```

### Install driver

1. Clone this git repository into `/usr/src/qed-6.1`
2. Add driver to dkms: `dkms add -m qed -v 6.1`
3. Build driver for current kernel: `dkms build -m qed -v 6.1`
4. Install driver for current kernel: `dkms install -m qed -v 6.1`

### Reload the driver if replacement needed

```sh
modprobe -vr qede
modprobe -vr qed
modprobe -v qed
modprobe -v qede
```

## Kernel upgrades

When apt updates the linux kernel, it will automatically rebuild the
driver. This is because the custom driver is registered with dkms.

This is a driver cloned from an in-tree driver, major kernel updates may
cause driver not to load anymore. Source qed driver needs to be updated in
this repository from the new kernel version.
