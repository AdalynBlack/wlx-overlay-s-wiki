WlxOverlay-S comes with a skybox for OpenXR. 

# Changing the Skybox

We are only allowed to include pieces with specific licenses in the git repo, but feel free to procure your own skybox materiel for personal use!

A custom texture may be set via `~/.config/wlxoverlay/conf.d`
```yaml
skybox_texture = starry-sky.dds
```

Criteria:
- Path can be absolute, or relative to `~/.config/wlxoverlay/`.
- File must be DDS (See: [Custom Textures](https://github.com/galister/wlx-overlay-s/wiki/Custom-Textures))
- Image must be an equirectangular (aka "HDRI" or "Spherical 360") image.

# Disable the skybox

```bash
use_skybox = false
```