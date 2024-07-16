# RISC-V Toolchain Installation

## Debian/Ubuntu

```sh
sudo apt-get install git build-essential gdb-multiarch qemu-system-misc gcc-riscv64-linux-gnu binutils-riscv64-linux-gnu 
```

## Arch Linux

```sh
sudo pacman -S riscv64-linux-gnu-binutils riscv64-linux-gnu-gcc riscv64-linux-gnu-gdb qemu-emulators-full
```

## MacOS

```sh
brew tap riscv/riscv
brew install riscv-tools
brew install qemu
```

## Windows

Fxxk windows, use virtual machine or WSL.

## Test Installation

```sh
qemu-system-riscv64 --version
```

At least one RISC-V version of GCC:

```sh
riscv64-linux-gnu-gcc --version
riscv64-unknown-elf-gcc --version
riscv64-unknown-linux-gnu-gcc --version
```
