# Dotfiles
These are my configuration files for my Arch Linux Rice. Here you can install in your system with a simple .sh file!! <br>**WARNING!** These dotfiles are not complete! For example ``swaylock`` is not customised.<br>![rice](https://github.com/Arkinux-Code/Dotfiles/assets/72414293/4e6990cd-4560-4236-b705-be6f1f15db52)

# Installation

**WARNING!**: For people with NVIDIA Cards, NVIDIA drivers will not work for everybody because of Wayland! Go to the Hyprland wiki for further information: https://wiki.hyprland.org/Nvidia/. <br>
**WARNING 2!**: Make sure to modify settings that will work on the computer! But installing with the default settings *should* not cause problems.

## Automatic Installation

## Non NVIDIA users
Clone the repository (or fork it if you want to edit settings before installing the dotfiles) inside the home folder. The install and update .sh files will be included in the repository.
```bash
git clone https://github.com/Arkinux-Code/Dotfiles.git && cd Dotfiles
```
Change the .sh ownership from root to the user.
```bash
chmod +x install.sh
```
Then execute the ``install.sh``.
```bash
./install.sh
```
The installer will copy the config files in the needed locations and you need to do anything. It is recommended to install drivers for your Intel/AMD card.

## NVIDIA users
For NVIDIA users, the steps are basically the same, but, some steps are required to make NVIDIA drivers work. Older cards require the Nouveau driver.
When installing any Linux Distro it is recommended to make the EFI partition ``1GB``, because it is strongly advised to install the ``linux-zen`` package, which is the Linux Zen kernel.
### Arch-based systems
```bash
pacman -S linux-zen linux-zen-headers
```
### Other systems
You need to compile it manually. Follow these steps: <br>
First, install the dev tools:
### Debian-based systems
```bash
apt install build-essential git fakeroot
```
### Using DNF
```bash
dnf group install "Development Tools"
```
Then, clone the zen kernel repository from github using this command:
```bash
git clone https://github.com/zen-kernel/zen-kernel.git && cd zen-kernel
```
Afterwards, execute the ``build.sh`` file:
```bash
./build.sh
```
The build process will take a while. Then, update GRUB or any other bootloader with this command:
```bash
grub-mkconfig -o /boot/grub/grub.cfg
```
or
```bash
update-grub
```
Reboot. <br>
After installing the Zen Kernel, check if it is running with ``uname -a``.

After installing the kernel, you need to install the ``nvidia-dkms`` package. <br>
**Arch Linux:** ``pacman -S nvidia-dkms`` <br>
**Debian:** ``apt install nvidia-dkms`` <br>
**DNF:** `dnf install akmod-nvidia` <br>

Reboot. The NVIDIA drivers should work. <br>

After rebooting, clone the repository (or fork it if you want to edit settings before installing the dotfiles) inside the home folder. The install and update .sh files will be included in the repository.
```bash
git clone https://github.com/Arkinux-Code/Dotfiles.git && cd Dotfiles
```
Change the .sh ownership from root to the user.
```bash
chmod +x install.sh
```
Then execute the ``install.sh``.
```bash
./install.sh
```
The installer will copy the config files in the needed locations and you need to do anything. It is recommended to install drivers for your Intel/AMD card.
