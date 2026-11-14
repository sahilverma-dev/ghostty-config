# Ghostty config

My terminal configuration for [Ghostty](https://ghostty.org), on macOS.

## Theme follows the system appearance

```ini
theme = light:Catppuccin Latte,dark:Catppuccin Mocha
```

Ghostty picks the light or dark entry from the OS appearance, so flipping macOS
between Light and Dark re-themes open terminal windows immediately. No restart,
no launch agent, no `osascript` hook.

Tested on Ghostty 1.4.0 / macOS 27.2.1. `ghostty +validate-config` passes.

One upstream caveat worth knowing: on macOS, the titlebar tab bar keeps its old
colors when the theme switches. The terminal contents and background do update.
This is a known Ghostty bug, not something in this config.

To use a different pair, either pick a built-in one:

```ini
theme = light:Rose Pine Dawn,dark:Rose Pine
```

or point at files in `themes/`:

```ini
theme = light:tokyonight_day,dark:tokyonight_night
theme = light:melange_light,dark:melange_dark
theme = light:kanagawa-lotus,dark:kanagawa-wave
```

## Install

```sh
git clone https://github.com/sahilverma-dev/ghostty-config.git ~/.config/ghostty
```

Or drop `config` (and optionally `themes/`) into an existing `~/.config/ghostty/`.
Do not clone over a config directory that already has your own settings.

Ghostty reloads on change. To check syntax before you find out the hard way:

```sh
ghostty +validate-config
ghostty +list-themes    # shows built-in and local themes
```

## What's in the config

Deliberately small. Everything else is left commented out so it is easy to turn
on without digging through docs.

| Setting | Value | Why |
| --- | --- | --- |
| `theme` | Catppuccin Latte / Mocha | Follows system appearance |
| `font-size` | `14` | Plain default, no `font-family` set |
| `mouse-scroll-multiplier` | `0.95` | Slows down trackpad scrolling |

Two options in here are Linux-only and do nothing on macOS: `gtk-titlebar` and
`async-backend`. They are leftovers from a config that was copied across
platforms, left in place so the file stays identical on both machines.

## `themes/`

Files here are looked up before Ghostty's built-in themes and shadow a built-in
of the same name. `tokyonight_day`, `tokyonight_storm` and `My colours` have
local tweaks; the rest are as shipped.

## Credits

This repo started life as a clone of [Thorsten Rhau's Ghostty
config](https://github.com/ThorstenRhau/ghostty), which is no longer public. Nine
of the ten files in `themes/` come from there, and the `LICENSE` is his:

> BSD 3-Clause License, Copyright (c) 2024, Thorsten Rhau

The BSD 3-Clause license requires that notice to be retained when the files are
redistributed, so `LICENSE` stays even though `config` has since been rewritten
from scratch. The theme files themselves are community ports — Tokyo Night,
Kanagawa, Melange and Catppuccin are other people's palettes.
