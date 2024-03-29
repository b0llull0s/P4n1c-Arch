## Synopsis:

Simple installation script for Arch Linux with `wayland`, `hyperland` and `waybar` riced with `py-wal`.
It also unlocks the Black Arch library and downloads some basic security utils.
Have in mind that `hyperland` wont work on virtual machines, so this will only work on bare metal. 

- Planning to add the next features soon:
  - `Ranger` and `kitty` integration
  - `Waybar` batteries module
  - Thinkpad experience 
  - Find the right music player
    
![Screenshot](screenshot1.png)

## Details:

| Category               | Software               
|------------------------|------------------------|
| Window Manager         | Hyprland               |
| Terminal Manager       | Alacritty, kitty       |
| File Manager           | Ranger, Nemo           |
| Status Bar             | Waybar                 |
| Launcher               | Rofi                   |
| Shell                  | Zsh                    |
| Browser                | Librewolf              |
| Text Editor            | neovim, Visual Code    |

### Waybar:

- Custom module to see how many updates are available.
- Custom module to check and show your public ip.
- Fully customized style with `pywal` integration and nerdfont icons.
- Audio module changes the key in base to the situation.
- Network module opens the `Network.Manager GUI`.
  
### Additional Packages included:

`pacman-contrib`  `yay`  `exa`  `bat`  `ufw`  `wireshark`  `bleachbit`  `virtualbox`  `burp`  `obsidian`  `nordvpn`  `signal`  `btop`  `wget`  `curl`  `locate`  `qflipper`  `neofetch`  `python`  `rust`  `pamixer`  `cmus`  `scrub`

### Zsh Plugings, Aliases and Functions:

- `Ohmyzsh` and `pywal` integration.
- Some handy aliases to use `systemctl` and your system in general.
- `Git` pluging and most useful aliases.
- `Cheat.sh` implemented on a function to use as `cheat <argument>`.
- Safe deletion of files using `scrup` and `schred` on a funtion to use as `rmk <argument>`.
- Some `zsh` plugins.

### Custom Scripts:

- Waybar reset for troubleshooting.
- Theme Change
- Screenshot and edition. 

### Cybersecurity features:

- Black Arch libraries
- Wireshark profiles

## Installation:

Make you sure you have a `USB` ready to use with a verified Arch `ISO`, you can find how to verified the integrity of your `ISO` inside the Arch documentation.
- You can use `rufus` or `dd` command in linux:
```bash
# Lookup for your USB drive
sudo fdisk -l
# Lookup for the path of your ISO file
realpath isofile
# Creates the bootable USB
sudo dd bs=4M if=/home/shutter/Documents/ISOs/archlinux-2023.10.14-x86_64.iso of=/dev/sdb
```
- Once you booted the `USB` and accessed the Arch `ISO` you may need to connect to your `wifi`:
```bash
# Start iwctl
iwctl
# list devices
device list
# Interface set to scan
station wlan0 scan
# Scan for networks
station wlan0 get-networks
# Connect to a network
station wlan0 connect networkname
```
- Just run the `archinstall` script. This are the only relevant steps that you need to follow for this build:
  - Use `ext4` file type for your system
  - `Systemd-bootloader` can give you problems with encryptation, in that case just use `GRUB`
  - Choose `Hyperland` as profile
  - Make sure dont choose any session manager as `Hyperland` recommends to login directly from the `TTY`.
  - Choose `NetworkManager`
  - I always add the extra libraries
  - Once is done reboot your system.
- Now you should need to connect to the internet, this time use `NetworkManager` from your system:
  
```bash
# Check if Networkmanager is running
sudo systemctl status NetworkManager.service
sudo systemctl start NetworkManager.service
# Connect to wifi
nmcli device wifi list
nmcli device wifi connect SSID_or_BSSID password password
# Different interface
nmcli device wifi connect SSID_or_BSSID password password ifname wlan1 profile_name
# Hidden network
nmcli device wifi connect SSID_or_BSSID password password hidden yes
```
- And download this repository:
```bash
https://github.com/b0llull0s/P4n1c-Arch.git
cd ~/P4nic-Arch
chmod +x *.sh
```
You may want to add your wallpapers to the `w4llp4p3rs` folder or just change the name and path on the script as you want.
If you experience problems with `py-wal`, make sure that all the paths inside the config files match with your system files.

![Screenshot](screenshot.png)

## Tips:

- In case you need to generate a new `py-wal` template just run:
```bash
wal -i Downloads/w4llp4p3rs/1.jpg
```
- In case you need to make zsh your default shell:
```bash
usermod --shell /usr/bin/zsh username
```
- Refresh your system data base
```bash
sudo updatedb
``` 
- To implement plugings use locate to find the path of the plugin file and add it to your source file:
```bash
# use this command:
locate zsh-autosuggestions
# Copy the .zsh entry and add it as source in the config file:
source /usr/share/zsh/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
```

## Keybindings:

| Key Combination                      | Action                  |
|--------------------------------------|-------------------------|
| `Super + Enter`                      | Alacritty               |
| `Super + F`                          | Librewolf               |
| `Super + K`                          | Kill Window             |
| `Super + D`                          | Rofi                    |
| `Super + E`                          | Nemo                    |
| `Super + [1-9]`                      | Switch Workspace        |
| `Super + [SHIFT] + [1-9]`            | Move Window to Workspace|
| `Super + [SHIFT] + [ARROW]`          | Resize Window           |
| `Super + [ARROW]`                    | Move within Windows     |
| `Super + P`                          | Toggle Split            |
| `Super + O`                          | Toggle Float            |
| `Super + I`                          | Swap Horizontal/Verical |
| `Super + U`                          | Full screen             |
| `Super + [PRINTSCRN]`                | Screenshot              |
| `Super + C`                          | VSCode                  |
| `Super + T`                          | Obsidian                |
| `Super + X`                          | code .config            |
| `Super + Z`                          | code .zshsrc            |
| `Super + S`                          | Signal                  |
| `Super + W`                          | Wireshark               |
| `Super + B`                          | Reset waybar            |
| `Super + N`                          | Changes theme           |
| `Super + Q`                          | Volume Up               |
| `Super + A`                          | Volume Down             |

## Credits and appreciations 

- Credit to **_Stephan Raabe_** for the base idea behind the custom scripts and all the `pywal` integration without his youtube channel would have been way harder.
- Credit to **_s4vitar_** for the `rmk` function.
- Credit to the **_annonymous_** user who posted the `waybar` custom module to see your public ip.
- Credit to **_@PenAce_** for the `wireshark` profiles taken from his awesome video.
- Credit to **_Alan Moore_** and **_Dave Gibbons_** for `image1` and The band **_Sleep_** for `image2`.
- Wallpaper by **_Wenqing Yan_**. ;) 

![Screenshot](image3.png)
