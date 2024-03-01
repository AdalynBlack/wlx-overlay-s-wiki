WlxOverlay-S can be built thicker or thinner, depending on your needs. The use of Rust features allows you to tailor the build to your system. By default, everything is included.

Help extend this wiki by providing packages for additional distros!

## Base dependencies
Using [Rustup](https://rustup.rs/) is recommended.

These are required in all cases:
- Arch: `base-devel cmake libxkbcommon fontconfig dbus alsa-lib`
- Ubuntu: `build-essential pkg-config cmake libxkbcommon-dev fontconfig libfontconfig-dev libdbus-1-dev libasound2-dev`

## Available features
### Feature `openvr`
Enable this if you plan on using SteamVR

Dependencies:
- Arch: `openvr`
- Ubuntu: `libopenvr-dev libopenvr-api1`

### Feature `openxr`
Enable this if you plan on using Monado

Dependencies:
- Arch: `openxr`
- Ubuntu: `libopenxr-dev`

### Feature `wayland`
Enable this if you're on a Wayland desktop

Dependencies:
- Arch: `libpipewire clang`
- Ubuntu: `libpipewire-0.3-0 libpipewire-0.3-dev libspa-0.2-dev clang`

### Feature `x11`
Enable this if you're on X11

Dependencies:
- Arch: `libx11 libxext libxrandr`
- Ubuntu: `libx11-6 libxext6 libxrandr2 libx11-dev libxext-dev libxrandr-dev`

### Feature `osc`
Enable this if you want XSO-compatible OSC parameters in VRChat

The following parameters will be sent:
```
isOverlayOpen (bool)
isKeyboardOpen (bool)
isWristVisible (bool)
openOverlayCount (int)
```

Dependencies: None

# Execute the build

Here are some examples you can do:
```bash
# Build with all features
cargo build --release

# Build for X11+SteamVR
cargo build --release --no-default-features --features=x11,openvr

# Build for Wayland+Monado
cargo build --release --no-default-features --features=wayland,openxr
```

A single executable will be placed at `target/release/wlx-overlay-s`.