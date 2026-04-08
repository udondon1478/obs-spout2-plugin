# Spout2 Plugin for OBS Studio (64bit) - OBS 32.0.4 対応フォーク

> **This is a fork of [Off-World-Live/obs-spout2-plugin](https://github.com/Off-World-Live/obs-spout2-plugin) updated for OBS Studio 32.0.4.**
>
> The upstream plugin targets OBS 31.0.x. This fork rebuilds the plugin against OBS 32.0.4 so it can be loaded by the latest version of OBS Studio.

This plugin enables the import and export of shared textures at high resolution to and from [SPOUT2](https://github.com/leadedge/Spout2) compatible
programs.

## Why

Previously the only way to import shared textures from SPOUT was via the DirectShow `SpoutCam` interface or by screen-capturing
the full-screen output of the `SpoutReceiver` program.

The `SpoutCam` is limited to standard webcam resolutions and capped at `1920x1080` and capturing the SpoutReceiver is both
inefficient and limited by your current screen resolution.

Previously, there was no way of outputting Spout video textures from OBS. 

This plugin implements the SPOUT2 SDK, creates an OBS Source from the SPOUT shared texture and a Spout output which sends the content of the OBS canvas to Spout.

## Installation

- Go to the [Releases Page](https://github.com/udondon1478/obs-spout2-plugin/releases)
- Download the windows installer: `OBS_Spout2_Plugin_Install_v1.11.1.exe`
- Run the installer (accepting installation from untrusted source)
- Select the `OBS` directory if not the default install location

> **Requires OBS Studio 32.0.4 or later.** This build is NOT compatible with OBS 31.x or earlier.

> **Upgrading from an older version:** If you previously installed the Spout plugin for OBS 31.x or earlier, you must remove the old files from `C:\Program Files\obs-studio\obs-plugins\64bit\` (specifically `win-spout.dll`, `Spout.dll`, `SpoutDX.dll`, `SpoutLibrary.dll`). The .exe installer does this automatically, but if you installed via .zip, delete them manually before installing the new version.

## Changes from Upstream

- Updated build configuration to target OBS Studio 32.0.4
- Updated obs-deps and Qt6 to 2025-08-23 release
- Added es-ES locale to NSIS installer
- Fixed submodule URL for CI compatibility (SSH -> HTTPS)

## Contributing / Building

- Clone this repo recursively
```
git clone --recursive https://github.com/udondon1478/obs-spout2-plugin
```
- Install [CMAKE min version 3.28](https://cmake.org/download/)
- Either configure and generate through the CMAKE Gui or through the command line for the `windows-x64` architecture
- Run `Configure`, `Generate` and then `Open Project` in the `CMake Gui`

### Building a release locally

```
cmake --preset windows-x64
cmake --build build_x64 --config RelWithDebInfo
```

## Acknowledgements

Thanks to the original authors at [Off World Live](https://offworld.live) for creating this plugin.

Thanks to the developer of [OBS-OpenVR-Input-Plugin](https://github.com/baffler/OBS-OpenVR-Input-Plugin) whose source
helped greatly in getting started with the OBS API.

Thanks to the OBS team and their discord channel.

Thanks to the authors of [SPOUT](https://github.com/leadedge/Spout2) for the library and clear documentation.

## License

This plugin originally authored by Campbell Morgan is Copyright Off World Live Ltd, 2019-2021 and [licenced under the GPL V.2](./LICENSE).
