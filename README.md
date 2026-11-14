# Ghostty config

My personal [Ghostty](https://ghostty.org) terminal configuration — macOS.
Adapted from a clone of [Thorsten Rhau](https://github.com/ThorstenRhau)'s
config, then changed to suit me. See [Credits](#credits).

**Clone it:**

```sh
git clone https://github.com/sahilverma-dev/ghostty-config.git ~/.config/ghostty
```

Repo: https://github.com/sahilverma-dev/ghostty-config

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

**Thorsten Rhau** — https://github.com/ThorstenRhau — wrote the original config
this repo grew out of. Full credit to him for the starting point.

| | |
| --- | --- |
| Original repo | `https://github.com/ThorstenRhau/ghostty` (now returns 404) |
| Copyright | (c) 2024, Thorsten Rhau |
| License | BSD 3-Clause — see [LICENSE](LICENSE) |
| Still his work | `LICENSE`, plus 9 of the 10 files in `themes/`: `kanagawa-dragon`, `kanagawa-lotus`, `kanagawa-wave`, `melange_dark`, `melange_light`, `tokyonight_day`, `tokyonight_moon`, `tokyonight_night`, `tokyonight_storm` |

BSD 3-Clause requires the copyright notice to be retained when those files are
redistributed, so `LICENSE` stays even though `config` no longer resembles his.

### What I changed

The `config` here is mine, not his. It differs in most of the things he had set:

- Theme: his Tokyo Night pair → Catppuccin Latte / Mocha, driven by the system
  appearance instead of being fixed
- Font: dropped his PragmataPro stack (paid font, not what I use) and his
  `font-feature` flags; font size 15 → 14
- Removed his split and tab keybindings, cursor and clipboard options
- Added `mouse-scroll-multiplier` and my own palette, `themes/My colours`

The theme files themselves are community ports. Tokyo Night, Kanagawa, Melange
and Catppuccin are other people's palettes, credited upstream.
