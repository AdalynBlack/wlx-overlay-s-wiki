Mirrors are overlays that show a view-only PipeWire cast of any kind; screen, region, window.

The view-only part means that mouse input will not work on these. This is due to a PipeWire protocol limitation.

Each mirror has a unique identifier (M1, M2, M3, ...) and can be initialized at runtime via the Show/Hide button on the settings page. The mirrored screen/region/window can be changed by destroying the mirror via the [X] button, then re-creating it with the Show/Hide button.

Mirrors are only supported on Wayland.

Note that not all Wayland compositors implement region / window casting.