# XaW64-Wine

![Wine Version](https://img.shields.io/badge/Wine-10.7-%23800000?style=for-the-badge&logo=wine&logoColor=%23800000) ![Box64 Version](https://img.shields.io/badge/Box64-0.3.5-blue?style=for-the-badge)

Wine-WoW64 Android + Box64 Android pre-configured for Termux native (aarch64) with minimal dependencies, installing only what is needed.

---

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
  - [General Settings](#general-settings)
  - [Driver Usage](#driver-usage)
  - [Extra Configurations](#extra-configurations)
- [Additional Guides](#additional-guides)
- [Additional Troubleshooting](#additional-troubleshooting)
- [Credits and Links](#credits-and-links)

---

## Installation

> [!NOTE]
> For termux-glibc users, try [XoW64](https://github.com/ar37-rs/xow64-wine).

### 1. Install desktop for native termux

- [Read for more info on how to setup xfce4](https://github.com/ar37-rs/xfce4-termux)
- Or [use termux-desktop from here](https://github.com/sabamdarif/termux-desktop/tree/main)

### 2. Ensure wget is installed

```bash
pkg install wget
```

### 3. Download xaw64 (Bash script only)

```bash
cd $HOME && rm -rf ~/xaw64 && wget https://github.com/ar37-rs/xaw64-wine/raw/refs/heads/main/xaw64 && chmod +x ~/xaw64
```

### 4. Install xaw64

```bash
~/xaw64 install
```

---

## Usage

### General Settings

#### Inside Termux Terminal

##### Enable sdcard for wine D: drive (optional)

```bash
~/xaw64 sdcard=true
```

##### Start wine in desktop mode on termux terminal

```bash
~/xaw64 sd
```

##### Quit wine desktop or terminate all wine-related processes

```bash
~/xaw64 qsd
```

#### Inside Desktop Environment Native Termux

##### Run wine config

```bash
~/xaw64 r winecfg
```

##### Run registry editor (regedit)

```bash
~/xaw64 r regedit
```

##### Run any specific \*.exe

```bash
~/xaw64 r app_name.exe
```

##### Run any \*.exe with a specific path

```bash
cd ~/'.to/Prog Files/app/path' && ~/xaw64 r app_name.exe
```

##### Launch GPU Caps (test OpenGL and Vulkan)

```bash
~/xaw64 gpucaps
```

##### Launch TestD3D (D3D9)

```bash
~/xaw64 testd3d
```

##### Launch CubeMap (test EnvMapping D3D9)

```bash
~/xaw64 cubemap
```

##### Launch SphereMap (test EnvMapping D3D9)

```bash
~/xaw64 spheremap
```

##### Launch wine in Windows desktop mode

Configure desktop size (or use any standard Windows screen size):

```bash
~/xaw64 desk-size=1024x768
```

And then simply start using:

```bash
~/xaw64 s
```

##### Quit wine or terminate all wine-related processes

```bash
~/xaw64 q
```

---

### Driver Usage

#### OpenGL/ES drivers

##### Using newer build of virgl (virpipe) driver

> [!NOTE]
> Universal Android 9+ with Vulkan 1.1+ GPU supported only.
> [Read more for additional virgl-angle usage here](https://github.com/ar37-rs/virgl-angle).

```bash
~/xaw64 driver=virpipe
```

##### Using virpipe angle driver

```bash
~/xaw64 vgl-use=angle
```

##### Using virpipe native android driver

> [!NOTE]
> Less stable, may use an older version of virgl.

```bash
~/xaw64 vgl-use=android
```

##### Using virgl 4.3COMPAT profile (default is OpenGL 4.1COMPAT)

> [!NOTE]
> Supports OpenGL 2.1, 3.2, 3.3, 4.1 and 4.3 with COMPAT.

```bash
~/xaw64 vgl-compat=4.3
```

##### Switch virgl back to default COMPAT profile

```bash
~/xaw64 vgl-compat=4.1
```

##### Fix virgl color/visual problems on d3d9+ (DirectX) apps/games

```bash
~/xaw64 vgl-cfg=d3d
```

##### Reconfigure virgl for OpenGL/ES apps/games

```bash
~/xaw64 vgl-cfg=gl
```

##### Switch OpenGL driver back to default (if any)

```bash
~/xaw64 driver=default
```

#### Direct 3D support for OpenGL drivers

##### Using WineD3D version 3.21

```bash
~/xaw64 wined3d=3.21
```

> [!WARNING]
> For wined3d 3.21 only: changing `deviceId` back to default is required if previously changed to something else.
>
> ```bash
> ~/xaw64 device=default
> ```

##### Using WineD3D version 4.21

```bash
~/xaw64 wined3d=4.21
```

##### Using WineD3D version 9.2

Fixes graphical glitches for some devices on Wine 10.7+. Highly recommended for virgl stability and performance.

```bash
~/xaw64 wined3d=9.2
```

##### Using WineD3D version 10.3

Fixes graphical glitches for some devices on Wine 10.7+. Recommended for newer games compatibility.

```bash
~/xaw64 wined3d=10.3
```

##### Switch back to default built-in WineD3D version

```bash
~/xaw64 wined3d=default
```

#### Direct 3D support for Vulkan drivers

##### Using dxvk-proton (supported on vulkan llvmpipe and any supported GPU driver)

```bash
~/xaw64 vkd3d=true
```

##### Using dxvk-glasync-proton for a more pleasant experience (supported on vulkan, same as dxvk-proton)

```bash
~/xaw64 vkd3d-async=true
```

##### Using dxvk-v1-proton (support for some legacy devices with vulkan 1.1)

```bash
~/xaw64 vkd3d-v1=true
```

##### Disable dxvk-proton, dxvk-glasync and dxvk-v1-proton

```bash
~/xaw64 vkd3d=false
```

> [!NOTE]
> If experiencing errors on specific vulkan drivers, use the older supported version [from here](https://github.com/doitsujin/dxvk) or use the modified dxvk version [from here](https://github.com/pytho[...]).

---

### Extra Configurations

#### Add any custom environment variable (e.g., disabling `MMAP32`)

```bash
~/xaw64 env-add BOX64_MMAP32=0
```

#### Check the list of added custom environment variables

```bash
~/xaw64 env-info
```

#### Remove an added custom environment variable

```bash
~/xaw64 env-remove BOX64_MMAP32=0
```

#### Reset custom environment variables to default

```bash
~/xaw64 env-default
```

#### Use custom graphic card deviceId and vendorId

Some games require the `deviceId` to be available on the system.

- Use custom GPU code name (GeForce GTX 950M):
  ```bash
  ~/xaw64 device=gtx950m
  ```
- Or (GeForce GTX 980):
  ```bash
  ~/xaw64 device=gtx980
  ```
- Or (UHD Graphics 630):
  ```bash
  ~/xaw64 device=uhd630
  ```
- Switch back to default `deviceId`:
  ```bash
  ~/xaw64 device=default
  ```

#### Enable/Disable winedlloverride for cnc-ddraw

```bash
~/xaw64 cnc-ddraw=true  # Enable
~/xaw64 cnc-ddraw=false # Disable
```

#### Disable/Re-enable wine debugger (for stability)

```bash
~/xaw64 debug=false # Disable
~/xaw64 debug=true  # Re-enable
```

#### System Updates & Uninstallation

- Update box64: `~/xaw64 update-box64`
- Update wine: `~/xaw64 update-wine`
- Update angle-android (Android 9+ only): `~/xaw64 update-angle`
- Update virglrenderer (Android 10+ only): `~/xaw64 update-virgl`
- Update patch: `~/xaw64 update-patch`
- Uninstall (remove) xaw64-wine completely: `~/xaw64 remove-all`

> [!NOTE]
>
> - Bionic is currently a little buggy on some devices. Working games tested: CMR2, NFS MW 2005 with good performance.
> - Use `~/xaw64 r winecfg` to add `/sdcard` (or a specific path) for a more customized drive setup.
> - Some commands (usage) and drivers might not be available yet on xaw64. Currently, essential commands are added and available.
> - Use virpipe for some low-end GPUs (Mali/PowerVR/etc.) with Vulkan 1.1, or use the vulkan wrapper for high-end Mali with Vulkan 1.3+ GPUs, or default native termux drivers such as freedreno/KGSL for Adreno 6[...].
> - For using a virtual controller, install InputBridge
>
>   [From here](https://github.com/ar37-rs/xow64-wine/releases/download/latest/InputBridge_v0.1.9.9.apk)
>
>   Start the command in the desktop Termux terminal:
>
>   ```bash
>   ~/xaw64 s
>   ```
>
>   Then run `StartIB.cmd` from the wine start menu (desktop mode) before launching any game. Open the InputBridge app on the Android device and configure the control buttons as needed.
>
> - If experiencing any emulation issues for a specific app/game:
>   Try using different versions of configurations (especially box64 environment variables) and drivers available above accordingly.
>
> - If there are problems when installing xaw64, make sure the latest correct Termux app version is installed. (Tested using [termux-app-v0.119.x](https://github.com/termux/termux-app/releases))

---

## Additional Guides

- **Using cnc-ddraw:**
  [Read more here](https://github.com/FunkyFr3sh/cnc-ddraw)

---

## Additional Troubleshooting

- **Fix virgl-angle vulkan support for some devices:**
  [Such as encountered in this issue](https://github.com/ar37-rs/virgl-angle/issues/1)
  ```bash
  pkg remove *icd-swrast && pkg install vulkan-loader-generic wget && cd && rm -rf ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && wget https://github.com/ar37-rs/virgl-angle/releases/download/lates[...]
  ```

- **Fix for some Android 12+ devices with "Process completed (signal 9)" issue using adb:**
  ```bash
  adb shell "settings put global settings_enable_monitor_phantom_procs false"
  ```
  And set `max_phantom_processes` as well:
  ```bash
  adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
  adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
  ```
  Then restart/reboot the device.
  [Read more info here](https://ivonblog.com/en-us/posts/fix-termux-signal9-error/) or [here](https://github.com/termux/termux-app/issues/2366)

---

## Credits and Links

- [InputBridge Wiki](https://search.brave.com/search?q=InputBrige%20exagear%20wiki&source=web)
- [XinputBridge Wiki](https://github.com/Ilan12346-maya/XinputBridge)
- [Mesa3D](https://www.mesa3d.org)
- [Termux](https://github.com/termux)
- [Termux-X11](https://github.com/termux/termux-x11)
- [Box64](https://github.com/ptitSeb/box64)
- [Winlator](https://github.com/brunodev85/winlator)
- [DXVK](https://github.com/doitsujin/dxvk)
- [DXVK GPLAsync](https://gitlab.com/Ph42oN/dxvk-gplasync)
- [VKD3D Proton](https://github.com/HansKristian-Work/vkd3d-proton)
- [EnvMapping](https://github.com/erfan2255/EnvMapping)
