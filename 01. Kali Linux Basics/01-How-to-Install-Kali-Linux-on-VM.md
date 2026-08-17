# How to Install Kali Linux on a Virtual Machine

## Introduction

Running Kali Linux inside a virtual machine (VM) is the safest and most
practical way to learn offensive security. A VM is an isolated computer
that runs inside your normal computer. If something goes wrong inside the
VM (a misconfiguration, a malware sample, a broken package), it does not
affect your real (host) operating system. It can simply be reset or
reinstalled.

This guide covers installing Kali Linux using both major virtualization
platforms:

- **VirtualBox** (free, cross-platform, made by Oracle)
- **VMware** (VMware Workstation Pro on Windows/Linux, VMware Fusion on
  macOS; free for personal use)

## 1. System Requirements

Before starting, make sure the host machine (your real computer) meets
these minimum requirements. These are for a comfortable experience running
Kali Linux with a graphical desktop inside a VM.

| Resource | Minimum | Recommended |
|---|---|---|
| RAM (Host) | 8 GB total | 16 GB or more total |
| RAM (allocated to VM) | 2 GB | 4 GB or more |
| CPU | 2 Cores, virtualization support (Intel VT-x / AMD-V) | 4 Cores or more |
| Disk Space | 20 GB free | 40-80 GB free (SSD recommended) |
| Host OS | Windows 10/11, macOS, or Linux | Same, fully updated |

Important notes:

- Virtualization (Intel VT-x or AMD-V) must be enabled in the host
  computer's BIOS/UEFI settings. Most modern computers have this enabled
  by default, but some do not.
- On laptops, check that "Hyper-V" (Windows) is not conflicting with
  VirtualBox. If VirtualBox VMs fail to start on Windows, disabling
  Hyper-V and related features (Windows Hypervisor Platform, Virtual
  Machine Platform, Windows Subsystem for Linux) in "Turn Windows
  features on or off" often fixes it. VMware Workstation on Windows can
  usually run alongside Hyper-V using its own compatibility mode.

## 2. Downloading Kali Linux

Always download Kali Linux from the official source to avoid tampered or
malicious images.

1. Go to the official Kali Linux downloads page: `https://www.kali.org/get-kali/`
2. Choose **Virtual Machines** (not "Installer" and not "Live") if you
   want a pre-built VM image for VirtualBox or VMware. This is the
   fastest option because the OS is already installed inside the image.
3. Alternatively, choose the **Installer** ISO if you want to perform a
   full manual installation yourself (recommended if you want to learn
   the installation process in detail, which this guide covers below).

## 3. Verifying the Download with SHA256 Checksum

Verifying the checksum confirms that the file you downloaded is complete
and has not been corrupted or tampered with. Kali Linux publishes SHA256
checksums on the download page next to each image.

### On Linux or macOS (Terminal)

```bash
sha256sum kali-linux-2024.x-installer-amd64.iso
```

On macOS, if `sha256sum` is not available, use:

```bash
shasum -a 256 kali-linux-2024.x-installer-amd64.iso
```

### On Windows (PowerShell)

```powershell
Get-FileHash .\kali-linux-2024.x-installer-amd64.iso -Algorithm SHA256
```

Compare the resulting long string of letters and numbers against the value
published on the official Kali download page. They must match exactly. If
they do not match, delete the file and download it again from the official
site.

## 4. Installing Kali Linux on VirtualBox

### 4.1 Install VirtualBox

1. Download VirtualBox from `https://www.virtualbox.org/`.
2. Install it using the default options for your operating system.
3. Also download and install the matching **VirtualBox Extension Pack**
   from the same site, which adds USB support and other features.

### 4.2 Create a New Virtual Machine

1. Open VirtualBox and click **New**.
2. Set a name, for example `Kali-Linux`. VirtualBox usually
   auto-detects the Type as "Linux" and Version as "Debian (64-bit)".
3. Set **Memory size (RAM)** to at least 2048 MB (2 GB), 4096 MB (4 GB)
   is better if the host has enough RAM.
4. Choose **Create a virtual hard disk now**, click **Create**.
5. Select **VDI (VirtualBox Disk Image)**.
6. Choose **Dynamically allocated** (disk grows as needed, saves space).
7. Set the disk size to at least 20 GB, 40 GB is recommended.
8. Click **Create** to finish creating the VM shell.

### 4.3 Attach the Kali ISO and Configure Settings

1. Select the new VM, click **Settings**.
2. Go to **System > Processor**, set at least 2 CPU cores.
3. Go to **Display**, set Video Memory to at least 128 MB, and enable
   3D Acceleration if available.
4. Go to **Storage**, click the empty optical drive icon, click the disk
   icon next to it, choose **Choose a disk file**, and select the Kali
   Linux ISO you downloaded.
5. Go to **Network**, confirm Adapter 1 is set to **NAT** (default,
   gives internet access without extra configuration). Later this can be
   changed to **Bridged Adapter** if the VM needs to appear as a separate
   device on your local network (useful for attacking other lab machines).
6. Click **OK** to save settings.

### 4.4 Boot and Install

1. Select the VM and click **Start**.
2. The Kali boot menu appears. Choose **Graphical Install**.
3. Follow the installation wizard:
   - Select language, location, and keyboard layout.
   - Set a hostname (for example `kali`).
   - Set a domain name (can be left blank).
   - Create a full user account: full name, username, and a strong
     password. This is very important, do not use a weak password.
   - Select the timezone.
   - Disk partitioning: choose **Guided - use entire disk** for
     simplicity (this only affects the virtual disk, not the real host
     computer).
   - Confirm partitioning changes by writing them to disk.
   - Choose which software collections to install (Desktop environment,
     top10 tools, standard system utilities). The default Kali
     recommended selection is fine for beginners.
   - Install the GRUB bootloader to the virtual disk when prompted.
4. When installation finishes, click **Continue** to reboot. VirtualBox
   will typically ask you to remove the installation media, or you can
   manually detach the ISO from Settings > Storage afterward.
5. Log in with the username and password you created.

## 5. Installing Kali Linux on VMware

### 5.1 Install VMware Workstation Player/Pro (or Fusion on macOS)

1. Download VMware Workstation Pro/Player from `https://www.vmware.com/products/workstation-pro.html`
   (Windows/Linux) or VMware Fusion for macOS.
2. Install using the default options.

### 5.2 Option A: Use the Pre-Built Kali VMware Image (Fastest)

1. Download the **VMware 64-bit** image from the official Kali downloads
   page. It comes as a compressed archive (`.7z`).
2. Extract the archive using 7-Zip (Windows) or `7z`/Archive Utility
   (Linux/macOS).
3. In VMware, choose **File > Open**, and select the extracted `.vmx`
   file.
4. Click **Play virtual machine**. Kali boots directly, already fully
   installed.
5. Default login credentials for the pre-built image are usually
   `kali` / `kali`. Always change this password immediately (see section
   6.3 below).

### 5.3 Option B: Manual Installation from ISO

1. Open VMware, click **Create a New Virtual Machine**.
2. Choose **Typical (recommended)** configuration.
3. Choose **Installer disc image file (iso)** and browse to the Kali
   ISO file.
4. VMware may detect it as Linux/Debian automatically. If it offers
   "Easy Install", it is safer for beginners to disable that and install
   manually so the graphical installer runs normally.
5. Name the VM, choose a location to store its files.
6. Set the maximum disk size to at least 20 GB, 40 GB recommended.
   Choose **Store virtual disk as a single file** for simplicity, or
   split into multiple files if the host filesystem has size limits.
7. Click **Customize Hardware** to increase RAM (2-4 GB) and CPU cores
   (2 or more) before finishing.
8. Click **Finish**, then **Power on this virtual machine**.
9. Follow the same **Graphical Install** steps described in section 4.4
   above (language, user account, partitioning, software selection,
   GRUB installation).

## 6. Post-Installation Tasks

These steps should be done immediately after any fresh Kali Linux install,
whether on VirtualBox or VMware.

### 6.1 Install Guest Additions / VMware Tools

These tools improve integration between the host and the VM: shared
clipboard, drag-and-drop, automatic screen resizing, and better mouse
performance.

**VirtualBox Guest Additions:**

```bash
sudo apt update
sudo apt install -y virtualbox-guest-utils
```

Then, in the VirtualBox window menu, go to **Devices > Insert Guest
Additions CD image**, and if prompted, run the installer from the mounted
CD, or simply reboot after installing the package above, since Kali's
repository package is usually enough on modern versions.

```bash
sudo reboot
```

**VMware Tools (usually called open-vm-tools on Debian-based systems):**

```bash
sudo apt update
sudo apt install -y open-vm-tools open-vm-tools-desktop
sudo reboot
```

After rebooting, try resizing the VM window. The Kali desktop resolution
should automatically adjust to fit the window.

### 6.2 Update the System

Always update Kali Linux immediately after installation, and regularly
afterward, since penetration testing tools change frequently.

```bash
sudo apt update && sudo apt upgrade -y
```

- `apt update` refreshes the local list of available packages and their
  versions from Kali's repositories.
- `apt upgrade -y` installs the newer versions of any packages that are
  outdated, automatically answering "yes" to prompts.

For a full distribution upgrade (which can also remove or install new
packages as needed to resolve dependencies), use:

```bash
sudo apt full-upgrade -y
```

Reboot after a large upgrade:

```bash
sudo reboot
```

### 6.3 Change Default Passwords

If you used the pre-built VM image with default credentials (commonly
`kali` / `kali`), change the password immediately:

```bash
passwd
```

This prompts for the current password, then asks for a new password
twice. Choose a strong, unique password, this machine will often be
exposed to untrusted networks and lab environments during practice.

If root login is enabled and you plan to use it, also set a strong root
password:

```bash
sudo passwd root
```

### 6.4 Take a Snapshot

Both VirtualBox and VMware support **snapshots**, which save the exact
state of the VM at a point in time. After completing setup and updates,
take a snapshot so you can always roll back to a clean, working state if
something breaks during practice.

- **VirtualBox:** Machine menu > Take Snapshot.
- **VMware:** VM menu > Snapshot > Take Snapshot.

This is one of the most useful habits in a lab environment, snapshot
before trying anything risky or destructive.

## Summary Checklist

- [ ] Verified host meets RAM/CPU/Disk requirements and virtualization is enabled in BIOS.
- [ ] Downloaded Kali Linux from the official website.
- [ ] Verified the SHA256 checksum of the downloaded image.
- [ ] Created the VM with at least 2 CPU cores, 2-4 GB RAM, 20-40 GB disk.
- [ ] Completed the graphical installation (or imported the pre-built image).
- [ ] Installed Guest Additions (VirtualBox) or VMware Tools.
- [ ] Ran `sudo apt update && sudo apt upgrade -y`.
- [ ] Changed all default passwords.
- [ ] Took a clean snapshot of the working system.
