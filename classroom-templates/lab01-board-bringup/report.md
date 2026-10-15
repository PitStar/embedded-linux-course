# Lab 01 report

- Student name:Danylo Sahno
- GitHub username:PitStar
- Image filename:
- SHA-256 (paste the checksum and state whether it matches the lab):

Replace each placeholder with your own command output. Label HOST and BBB
results. Do not include passwords or private keys.

## Running Linux on BBB

### BBB: `uname -r`

```text
6.1.99
```

### BBB: `cat /etc/os-release`

```text
NAME=Buildroot
VERSION=-ge6abe17d-dirty
ID=buildroot
VERSION_ID=2024.02
PRETTY_NAME="Buildroot 2024.02"
ID_LIKE="buildroot"
RK_BUILD_INFO="hxj@luckfox-System-Product-Name Mon Nov 24 19:33:32 CST 2025 - rockchip_rk3506_luckfox"
```

### BBB: `lsblk`

```text
after df -hT:
Filesystem           Type            Size      Used Available Use% Mounted on
ubi0:rootfs          ubifs         193.3M    106.0M     87.3M  55% /
devtmpfs             devtmpfs       42.8M         0     42.8M   0% /dev
tmpfs                tmpfs          42.9M     56.0K     42.8M   0% /var/log
tmpfs                tmpfs          42.9M    228.0K     42.6M   1% /tmp
tmpfs                tmpfs          42.9M     72.0K     42.8M   0% /run
tmpfs                tmpfs          42.9M         0     42.9M   0% /dev/shm
```

### BBB: `ip addr`

```text
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 16:de:37:26:a9:d1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.123.100/24 brd 192.168.123.255 scope global usb0
       valid_lft forever preferred_lft forever
```

## First user-space program

### HOST, in this lab directory: `file build/hello`

```text
build/hello: ELF 32-bit LSB pie executable, ARM, EABI5 version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux-armhf.so.3, BuildID[sha1]=3afdc3b47425b0926d3a251fef5199a827afb3e9, for GNU/Linux 3.2.0, not stripped
```

### BBB: `/home/debian/labs/lab01/hello`

```text
/root/labs/lab01/hello
Hello from Lab 01 on LuckFox Lyra!
```

## Shared kernel workspace

### HOST: `ls -lh ~/bbb-workspace/kernel/bb-kernel/deploy`

```text
-rw-r--r--   1 user user  496 Oct  1 20:03 COPYING
-rw-r--r--   1 user user 100K Oct  1 20:03 CREDITS
drwxr-xr-x  86 user user 4.0K Oct  1 20:03 Documentation
-rw-r--r--   1 user user 2.6K Oct  1 20:03 Kbuild
-rw-r--r--   1 user user  555 Oct  1 20:03 Kconfig
drwxr-xr-x   6 user user 4.0K Oct  1 20:03 LICENSES
-rw-r--r--   1 user user 673K Oct  1 20:03 MAINTAINERS
-rw-r--r--   1 user user  70K Oct  1 20:03 Makefile
-rw-r--r--   1 user user 594K Oct  1 20:26 Module.symvers
-rw-r--r--   1 user user  727 Oct  1 20:03 README
-rw-r--r--   1 user user 1.8M Oct  1 20:26 System.map
drwxr-xr-x  24 user user 4.0K Oct  1 20:03 arch
drwxr-xr-x   3 user user 4.0K Oct  1 20:20 block
-rw-r--r--   1 user user 8.1M Oct  1 20:26 boot.img
-rw-r--r--   1 user user 1.4K Oct  1 20:03 boot.its
-rw-r--r--   1 user user 136K Oct  1 20:26 built-in.a
drwxr-xr-x   2 user user 4.0K Oct  1 20:18 certs
drwxr-xr-x   4 user user  12K Oct  1 20:20 crypto
drwxr-xr-x 143 user user 4.0K Oct  1 20:26 drivers
drwxr-xr-x  81 user user  12K Oct  1 20:24 fs
drwxr-xr-x  33 user user 4.0K Oct  1 20:18 include
drwxr-xr-x   2 user user 4.0K Oct  1 20:26 init
drwxr-xr-x   2 user user 4.0K Oct  1 20:03 io_uring
drwxr-xr-x   2 user user 4.0K Oct  1 20:19 ipc
drwxr-xr-x  22 user user  12K Oct  1 20:22 kernel
drwxr-xr-x  22 user user  20K Oct  1 20:22 lib
-rw-r--r--   1 user user 690K Oct  1 20:03 logo.bmp
-rw-r--r--   1 user user 690K Oct  1 20:03 logo_kernel.bmp
drwxr-xr-x   6 user user  12K Oct  1 20:21 mm
-rw-r--r--   1 user user  11K Oct  1 20:26 modules.builtin
-rw-r--r--   1 user user  63K Oct  1 20:26 modules.builtin.modinfo
-rw-r--r--   1 user user 1.5K Oct  1 20:26 modules.order
drwxr-xr-x  72 user user 4.0K Oct  1 20:25 net
-rw-r--r--   1 user user 1.5M Oct  1 20:26 resource.img
drwxr-xr-x   6 user user 4.0K Oct  1 20:03 rust
drwxr-xr-x  39 user user 4.0K Oct  1 20:03 samples
drwxr-xr-x  17 user user  12K Oct  1 20:18 scripts
drwxr-xr-x  14 user user 4.0K Oct  1 20:19 security
drwxr-xr-x  27 user user 4.0K Oct  1 20:21 sound
drwxr-xr-x  41 user user 4.0K Oct  1 20:03 tools
drwxr-xr-x   4 user user 4.0K Oct  1 20:18 usr
drwxr-xr-x   4 user user 4.0K Oct  1 20:20 virt
-rwxr-xr-x   1 user user 140M Oct  1 20:26 vmlinux
-rw-r--r--   1 user user 584K Oct  1 20:26 vmlinux.a
-rw-r--r--   1 user user 271M Oct  1 20:26 vmlinux.o
-rw-r--r--   1 user user 6.1M Oct  1 20:26 zboot.img
```

### HOST: `cat ~/bbb-workspace/kernel/bb-kernel/KERNEL/include/config/kernel.release`

```text
6.1.99
```

Do the full HOST and BBB kernel-release strings match exactly?

<YES>

Why must Lab 02 use a matching kernel tree?

<modules in Lab02 will use built kernel without changes.The advantage of kernel-modules is in possibility of loading and unloading. In this case we do not need to rebuild a kernel and we can use it being unchanged. Developing kernel module we should ensure that kernel code in SDK is same in kernel which is deployed already.>

Submit this completed report with `src/hello.c` and `Makefile`. Do not commit
images, executables, toolchains, kernel sources, or build artifacts.
