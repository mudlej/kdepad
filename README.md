# kdepad

Hide running windows off every virtual desktop on KDE Plasma 6, and call them
back when you want them.

A hidden window keeps running. It is gone from all desktops, the taskbar,
Alt+Tab, the pager and the Overview until you call it back.

## Screenshots

| Picker | Tray menu |
| :---: | :---: |
| <img width="380" alt="The picker: a filter box above a list of three hidden windows" src="https://github.com/user-attachments/assets/e4587dc1-f184-4228-bbbd-608fd122e5b3" /> | <img width="380" alt="The tray menu: the hidden windows, then Bring everything back, Reload config, Edit config and Quit" src="https://github.com/user-attachments/assets/f27c5b64-5dd3-4ed7-83a2-702fd353acb0" /> |

## Install

kdepad is one file. It needs Plasma 6 and PyQt6, and offers to install PyQt6
if it is missing.

```sh
curl -LO https://github.com/mudlej/kdepad/releases/latest/download/kdepad
chmod +x kdepad
./kdepad
```

Put the file where you want to keep it before the first run. That run adds
kdepad to login autostart and the app launcher and puts `kdepad` on your PATH.
`kdepad uninstall` undoes all of that.

## Use

| Key            | What it does                                   |
| -------------- | ---------------------------------------------- |
| `Meta+H`       | Hide the focused window                        |
| `Meta+Shift+H` | List the hidden windows; type to filter, Enter |
| `Meta+Ctrl+H`  | Bring back the most recently hidden window     |

The tray icon does the same with the mouse. A window you bring back lands on
the desktop you are on. Quitting kdepad brings every hidden window back.

## Config

`~/.config/kdepad/config.toml`, applied with `kdepad reload`:

```toml
[shortcuts]
stash  = "Meta+H"
picker = "Meta+Shift+H"
last   = "Meta+Ctrl+H"

[[app]]
name      = "Music"
match     = "spotify"   # window class, from `kdepad windows`
shortcut  = "Meta+S"    # hide when focused, otherwise bring it to you
autostash = true        # hide its window as soon as it opens
command   = "spotify"   # started by the shortcut when it is not running
```

## Commands

```
kdepad            run the tray daemon
kdepad windows    list open windows with their class and hidden state
kdepad pick       open the list of hidden windows
kdepad reload     re-read the config
kdepad restore    bring every hidden window back
kdepad quit       restore, then stop
kdepad uninstall  remove autostart, launcher entry and PATH link
```

## Limits

Plasma 6 only; it drives KWin directly, so it does not work on other desktops
or on Plasma 5. Developed on Wayland.

## License

GPL-3.0. See [LICENSE](LICENSE).
