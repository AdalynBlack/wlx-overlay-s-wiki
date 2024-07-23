Custom textures are accepted in the form of DDS files.

## What is a DDS file?

DDS is a container format for GPU-native textures. The image data is ready to be uploaded to the GPU.

The image data of a DDS file can use various compression methods, with some methods focusing on specific use cases.

## Convert standard picture to DDS using Texpresso

[Texpresso](https://github.com/jansol/texpresso) is available via Cargo:
```bash
cargo install texpresso_cli
```

Usage example:
```bash
texpresso compress --format BC3 path/to/image.png
```

The resulting .dds file can then be used with WlxOverlay-S.

## Recommended Formats:
 - `BC1`: RGB with no transparency
 - `BC3`: Has transparency, but takes twice the memory as BC1
 - `BC7`: Same characteristics as BC3, but higher quality (Not supported by Texpresso)