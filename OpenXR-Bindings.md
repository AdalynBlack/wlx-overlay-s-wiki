OpenXR Bindings can be configured using a file.

By default, the file does not exist and internal defaults will be used.

Place [openxr_actions.json5](https://github.com/galister/wlx-overlay-s/blob/main/src/backend/openxr/openxr_actions.json5) in `~/.config/wlxoverlay/` and edit it to your liking.

```bash
wget -O ~/.config/wlxoverlay/openxr_actions.json5 https://github.com/galister/wlx-overlay-s/raw/main/src/backend/openxr/openxr_actions.json5
```

To see what bindings are available for each controller type, search for the profile in [the OpenXR specification](https://registry.khronos.org/OpenXR/specs/1.1/html/xrspec.html).