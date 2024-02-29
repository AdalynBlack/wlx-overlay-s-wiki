UI definitions are stored in yaml files under `~/.config/wlxoverlay`.

First, let's grab some files that we can edit.

### Customize Watch

```bash
cd ~/.config/wlxoverlay
wget https://github.com/galister/wlx-overlay-s/raw/main/src/res/watch.yaml
```

### Customize Settings Panel

```bash
cd ~/.config/wlxoverlay
wget https://github.com/galister/wlx-overlay-s/raw/main/src/res/settings.yaml
```

### Add a custom UI window of your own

Simply create any Yaml file in `~/.config/wlxoverlay` with the correct format. You will be able to spawn it using the `Window` type `Button` placed on an existing UI panel, such as the watch or settings.

# Before you begin - Performance considerations

UI panels can be expensive.
- Pick the smallest render resolution (`size`) that still looks OK. Increasing resolution will severely increase VRAM usage.
- Pick 2-3 font sizes and use those same sizes across your panels. Loading additional font sizes will increase VRAM usage.
- Compositing is not a simple task. It often makes sense to create one larger panel instead of many smaller ones (sacrifice VRAM in exchange for lighter CPU load).

# Basic UI Settings

- `size` - render resolution of the panel. after changing this, you would need to to re-adjust the placement and sizes of elements. 
- `width` - size of the panel in 3D space, in meters. height will be calculated from the aspect ratio.

- `elements` - the UI elements that will be drawn and may be interacted with

# Element Types

## Panel

A colored rectangle.

Example:
```yaml
  - type: Panel
    rect: [0, 0, 400, 200]
    bg_color: "#353535"
```

## Label

Displays some kind of text.

#### Static Label
Displays static text.
```yaml
  - type: Label
    rect: [15, 35, 600, 70]
    font_size: 12
    fg_color: "#ffffff"
    source: Static
    text: Settings
```

#### Clock label
The clock label displays date, time or both with the provided format. See available formats [here](https://docs.rs/chrono/0.4.34/chrono/format/strftime/index.html).
```yaml
    source: Clock
    format: "%x"
```
#### Exec Label

Executes a command every `interval` seconds

```yaml
    source: Exec
    command: ["echo", "hello world" ]
    interval: 0.5
```

#### Internal Use

There are some types that are meant to be used internally, but feel free to use them, too. See: [LabelContent](https://github.com/galister/wlx-overlay-s/blob/main/src/gui/modular/label.rs)

## Button

Rectangular push-button with a background rectangle, a highlight layer and foreground text.

Buttons provide these events:
- `click_down`
- `click_up`
- `long_click_up`
- `right_down`
- `right_up`
- `long_right_up`
- `middle_down`
- `middle_up`
- `long_middle_up`
- `scroll_down`
- `scroll_up`

Any number of actions can be attached to events. Actions are enumerated in order of appearance.

Example:
```yaml
  - type: Button
    rect: [327, 52, 46, 32]
    font_size: 14
    fg_color: "#FFFFFF"
    bg_color: "#505050"
    text: "+"
    click_down:
      - type: Exec
        command: [ "pactl", "set-sink-volume", "@DEFAULT_SINK@", "+5%" ]
      - type: Toast
        message: Volume was raised!
```

### Button actions

#### Exec
Executes a command.
```yaml
      - type: Exec
        command: [ "pactl", "set-sink-volume", "@DEFAULT_SINK@", "+5%" ]
```

#### Toast
```yaml
      - type: Toast
        message: Hello world!
```

#### Window

**Create a window from `mypanel.yaml`:**
```yaml
      - type: Window
        target: mypanel
        action: ShowUi
```

**Create a mirror (PipeWire window/region/screen):**
```yaml
      - type: Window
        target: M1
        action: ShowMirror
```

**Destroy a window**:
Closes the window, stopping all captures and releasing resources such as swapchains.
This can be used with windows spawned by ShowUi and ShowWindow.

```yaml
      - type: Window
        target: M1
        action: Destroy
```
#### Overlay
These work on windows created with ShowUi / ShowMirror, as well as built-in overlays.

A showcase of this can be found on the `kbd` button in [watch.yaml](https://github.com/galister/wlx-overlay-s/blob/f4b10f825e010ef48c2e9573343385328a32ea6c/src/res/watch.yaml#L26).

#### Internal Use

There are some types that are meant to be used internally, but feel free to use them, too. See: [ButtonData, ButtonAction](https://github.com/galister/wlx-overlay-s/blob/main/src/gui/modular/button.rs)