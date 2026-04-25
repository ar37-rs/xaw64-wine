# XaW64-Wine

![Wine Version](https://img.shields.io/badge/Wine-10.7-%23800000?style=for-the-badge&logo=wine&logoColor=%23800000) ![Box64 Version](https://img.shields.io/badge/Box64-0.3.5-blue?style=for-the-badge)

Wine-WoW64 Android + Box64 Android presetuped for termux native (aarch64)
with minimal dependencies as possible and install only what needed.

---

# Installation:

> [!NOTE]
> For termux-glibc users try [XoW64](https://github.com/ar37-rs/xow64-wine)

### 1. Install desktop for native termux

[(Read for more info on how to setup xfce4)](https://github.com/ar37-rs/xfce4-termux)
or
[(Using termux-desktop from here)](https://github.com/sabamdarif/termux-desktop/tree/main)

### 2. Make sure if wget is installed

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

# Usage

## Setting Usage

### Inside termux terminal

#### Enable sdcard for wine D: drive (optional)

```bash
~/xaw64 sdcard=true
```

#### Start wine in desktop mode on termux terminal

```bash
~/xaw64 sd
```

#### Quit wine desktop or terminate all wine related process

```bash
~/xaw64 qsd
```

### Inside desktop environment native termux

#### Run wine config

```bash
~/xaw64 r winecfg
```

#### Run registry editor (regedit)

```bash
~/xaw64 r regedit
```

#### Run any specific \*.exe

```bash
~/xaw64 r app_name.exe
```

#### Run any \*.exe with any specific path

```bash
cd ~/'.to/Prog Files/app/path' && ~/xaw64 r app_name.exe
```

#### Launch GPU Caps (test OpenGL and Vulkan)

```bash
~/xaw64 gpucaps
```

#### Launch TestD3D (D3D9)

```bash
~/xaw64 testd3d
```

#### Launch CubeMap (test EnvMapping D3D9)

```bash
~/xaw64 cubemap
```

#### Launch SphereMap (test EnvMapping D3D9)

```bash
~/xaw64 spheremap
```

#### Launch wine in windows desktop mode

##### configure desktop size like so (or any standard windows screen size)

```
~/xaw64 desk-size=1024x768
```

##### and then simply start using

```
~/xaw64 s
```

#### Quit wine or terminate all wine related process

```bash
~/xaw64 q
```

---

## Driver Usage:

### OpenGL/ES drivers

#### Using newer build of virgl (virpipe) driver

> [!NOTE]
> Universal android 9+ with vulkan 1.1+ GPU supported only
> [(Read more for virgl-angle additional usage from here)](https://github.com/ar37-rs/virgl-angle)

```bash
~/xaw64 driver=virpipe
```

#### Using virpipe angle driver

```bash
~/xaw64 vgl-use=angle
```

#### Using virpipe native android driver

> [!NOTE]
> Less stable might using older version of virgl

```bash
~/xaw64 vgl-use=android
```

#### Using virgl 4.3COMPAT profile (default is OpenGL 4.1COMPAT)

> [!NOTE]
> Supports OpenGL 2.1, 3.2, 3.3, 4.1 and 4.3 with COMPAT

```bash
~/xaw64 vgl-compat=4.3
```

#### Switch back virgl to default COMPAT profile.

```bash
~/xaw64 vgl-compat=4.1
```

#### Fix virgl color/visual problems on d3d9+ (Direct X) apps/games

```bash
~/xaw64 vgl-cfg=d3d
```

#### Reconfigure virgl for OpenGL/ES apps/games

```bash
~/xaw64 vgl-cfg=gl
```

#### Switch back OpenGL driver to default (if any)

```bash
~/xaw64 driver=default
```

### Direct 3D support for OpenGL drivers

#### Using WineD3D version 3.21

```bash
~/xaw64 wined3d=3.21
```

- > [!WARNING]
  > for wined3d 3.21 only: changing `deviceId` back to default is required if previously changed to something else)
  >
  > ```bash
  > ~xow64 device=default
  > ```

#### Using WineD3D version 4.21

```bash
~/xaw64 wined3d=4.21
```

#### Using WineD3D version 9.2 (fix graphical glitches for some devices on wine 10.7+, highly recommended for virgl stability and performance)

```bash
~/xaw64 wined3d=9.2
```

#### Using WineD3D version 10.3 (fix graphical glitches for some devices on wine 10.7+, recommeded for newer games compatibility)

```bash
~/xaw64 wined3d=10.3
```

#### Switch back using default builtin WineD3D version

```bash
~/xaw64 wined3d=default
```

### Direct 3D support for vulkan drivers

#### Using dxvk-proton (supported on vulkan llvmpipe and any supported GPU driver)

```bash
~/xaw64 vkd3d=true
```

#### Using dxvk-glasync-proton for more pleasant experience (supported on vulkan the same as dxvk-proton)

```bash
~/xaw64 vkd3d-async=true
```

#### Using dxvk-v1-proton (support for some legacy devices with vulkan 1.1)

```bash
~/xaw64 vkd3d-v1=true
```

#### Disable dxvk-proton, dxvk-glasync and dxvk-v1-proton

```bash
~/xaw64 vkd3d=false
```

> [!NOTE]
> If experiencing error on some specific vulkan drivers use the older supported version [from here](https://github.com/doitsujin/dxvk) or use modified dxvk version [from here](https://github.com/pythonlover02/DXVK-Sarek)

---

## Additional usage

#### Adding any custom environment variable (e.g: disabling `MMAP32`)

```bash
~/xaw64 env-add BOX64_MMAP32=0
```

#### Check list of the added custom environment variables

```bash
~/xaw64 env-info
```

#### Remove the added custom environemnt variable

```bash
~/xaw64 env-remove BOX64_MMAP32=0
```

#### Reset custom environment variables to default

```bash
~/xaw64 env-default
```

#### Using custom graphic card deviceId and vendorId, some games require the `deviceId` to be available on the system

##### use custom GPU code name (GeForce GTX 950M)

```bash
~/xaw64 device=gtx950m
```

##### or (GeForce GTX 980)

```bash
~/xaw64 device=gtx980
```

##### or (UHD Graphics 630)

```bash
~/xaw64 device=uhd630
```

##### Swich back to default `deviceId`

```bash
~/xaw64 device=default
```

#### Enable winedlloverride for cnc-ddraw

```bash
~/xaw64 cnc-ddraw=true
```

#### Disable winedlloverride for cnc-ddraw

```bash
~/xaw64 cnc-ddraw=false
```

#### Disable wine debugger (for stability)

```bash
~/xaw64 debug=false
```

#### Re-enable wine debugger

```bash
~/xaw64 debug=true
```

#### Update box64 to newer version

```bash
~/xaw64 update-box64
```

#### Update wine

```bash
~/xaw64 update-wine
```

#### Update angle-android (android 9+ only)

```bash
~/xaw64 update-angle
```

#### Update virglrenderer (android 10+ only)

```bash
~/xaw64 update-virgl
```

#### Update patch

```bash
~/xaw64 update-patch
```

#### Uninstall (remove) xaw64-wine completely

```bash
~/xaw64 remove-all
```

> [!NOTE]
>
> - Bionic currently a little buggy on some devices, working games tested CMR2, NFS MW 2005 with good performance.
> - Use `~/xaw64 r winecfg` to add /sdcard (or specific path) for more custom drive
> - Some commands (usage) and drivers might not available yet on xaw64, currently essentials commands are added and available
> - Use virpipe for some low-end (Mali/PowerVR/etc) GPUs with vulkan 1.1 or use vulkan wrapper for high-end Mali with vulkan 1.3+ GPUs or default native termux drivers such freedreno/KGSL for Adreno 6XX+.
> - Using virtual controller, install InputBrige
>
>   [From here](https://github.com/ar37-rs/xow64-wine/releases/download/latest/InputBridge_v0.1.9.9.apk)
>
>   and start command in desktop termux terminal
>
>   ```
>   ~/xaw64 s
>   ```
>
>   and then `StartIB.cmd` from wine start menu (desktop mode) before launching any game, then open InputBridge app on android device and then start configuring control buttons as need.
>
> - If experiencing any emulation issue for specific app/game
>
>   try using different version of configurations (especially box64 environment variables) and drivers available above accordingly.
>
> - If there's problem when installing xaw64, make sure the latest correct termux app version is installed.

(tested using [termux-app-v0.119.x](https://github.com/termux/termux-app/releases))

## Addtional guide:

- Using cnc-ddraw:

  [read more from here](https://github.com/FunkyFr3sh/cnc-ddraw)

## Additional troubleshoot:

- Fix virgl-angle vulkan support for some devices

  [such encountered on this issue](https://github.com/ar37-rs/virgl-angle/issues/1)

  ```
  pkg remove *icd-swrast && pkg install vulkan-loader-generic wget && cd && rm -rf ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && wget https://github.com/ar37-rs/virgl-angle/releases/download/latest/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && dpkg -i ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb
  ```

- Fix for some android 12+ devices with [Process completed (signal 9) - ...] issue using adb:
  ```
  adb shell "settings put global settings_enable_monitor_phantom_procs false"
  ```
  and set max_phantom_processes as well
  ```
  adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
  adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
  ```
  and then restart/reboot device.
  [read more for more info from here](https://ivonblog.com/en-us/posts/fix-termux-signal9-error/) or [here](https://github.com/termux/termux-app/issues/2366)

# Other links for credits (3rd parties):

- [InputBridge Wiki](https://search.brave.com/search?q=InputBrige%20exagear%20wiki&source=web)

- [XinputBridge Wiki](https://github.com/Ilan12346-maya/XinputBridge)

- [https://www.mesa3d.org](https://www.mesa3d.org)

- [https://github.com/termux](https://github.com/termux)

- [https://github.com/termux/termux-x11](https://github.com/termux/termux-x11)

- [https://github.com/ptitSeb/box64](https://github.com/ptitSeb/box64)

- [https://github.com/brunodev85/winlator](https://github.com/brunodev85/winlator)

- [https://github.com/doitsujin/dxvk](https://github.com/doitsujin/dxvk)

- [https://gitlab.com/Ph42oN/dxvk-gplasync](https://gitlab.com/Ph42oN/dxvk-gplasync)

- [https://github.com/HansKristian-Work/vkd3d-proton](https://github.com/HansKristian-Work/vkd3d-proton)

- [https://github.com/erfan2255/EnvMapping](https://github.com/erfan2255/EnvMapping)
