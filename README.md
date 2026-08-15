  # Termux-Debian-installer
 
 Description:
 An automatic installer for Devices supporting Termux. Allowing installation of Debian packages via PRoot way easier
 ---
## How to Install and Set Up

## Requirements:

A device that has android support (Samsung, Google pixel, ChromeOS, etc)

Termux and Termux API

PRoot (Debian)

Nano (Optional. But install it if you will edit the script)
___
### step 1. installation of requirements: (Before installing, make sure all repositories are up to date with 'apt update && apt upgrade')

**Termux:** Download the APK on Github or F-Droid (DO NOT INSTALL IT FROM THE PLAY STORE)

**Termux:API:** Run `pkg install termux-api` inside of Termux and install the Termux:API app (found in Github or F-Droid. Download the APK from the same website as you got termux).

**PRoot (Debian):** Run `pkg install proot proot-distro` then after installation run `proot-distro install debian` inside of Termux NOTE: If you want to use a different distro. Then edit the ling with `proot-distro login` and replace `debian` with your desired distro in nano. 

**Nano:** Run 'pkg install nano' in Termux.
___
Termux and Termux API may ask for permissions. enable the following:

**Termux:** `display over other apps` and `install unknown apps`. Also run `termux-setup-storage` to enable termux to access system storage permissions

**Termux API:** `display over other apps`.

If these permissons do not appear automatically, they should be in: `settings/apps/Termux/Advanced` and `settings/apps/Termux:API/Advanced`

If you have everything installed and configured. Then proceed to step 2 
___
### step 2. Download or Save the Script
Make sure the script is stored in your `~/Scripts/`directory and is executable:

```bash
mkdir -p ~/Scripts

curl -sL https://raw.githubusercontent.com/kubilydaniel/Termux-Debian-installer/main/debian-installer.sh -o ~/Scripts/debian-installer.sh

chmod +x ~/Scripts/debian-installer.sh
```

### step 3. Link the script to termux-file-editor so Termux automatically routes opened .deb files to it
```bash
mkdir -p ~/bin

ln -sf ~/Scripts/debian-installer.sh ~/bin/termux-file-editor

chmod +x ~/bin/termux-file-editor
```
___
## How to use (File manager) 

Step 1. Locate the .deb file you want to install in the files app

step 2. press and hold (or press the three vertical dots) and press 'Open With' and click 'Termux'.

Step 3. a Termux pop up should appear with your file name and have three options, being: 'Open Directory', 'Cancel', and 'Edit'. press 'Edit' and the script should start.
___
## How to use (terminal)

run the command:
```bash
~/Scripts/debian-installer.sh /path/to/your/package.deb
```
___
to open the program, run: `proot-distro login debian` then enter the command to start the desired program
___
## Editing and customization

### Editing the script

**General:** To edit the script, run `nano ~/Scripts/debian-installer.sh`

**distro change** To change the distro the installer uses, run `nano ~/Scripts/debian-installer.sh` find `proot-distro login` and change  `debian` to the desired distro.
___

# Known issues

**No display output by default:** PRoot Debian operates strictly in terminal (CLI) mode out of the box. To Run Desktop (GUI) apps, you must set up a X11 server Or VNC client.
