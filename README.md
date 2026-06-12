# GNOME-like keyboard shortcuts for macOS

A [Karabiner-Elements](https://karabiner-elements.pqrs.org/) config that makes a Mac feel like GNOME.

What it does:

- **Ctrl acts as Cmd** in GUI apps — Ctrl+C/V/T/W/etc. just work. Terminals are excluded, so Ctrl+C still interrupts.
- **Ctrl+Shift+C/V/T/W/N/F in terminals** map to their Cmd equivalents, matching GNOME Terminal conventions.
- **Alt+Tab** switches apps, **Alt+`** cycles windows of the same app.
- **Tapping the Win/Super key** opens Mission Control, like the GNOME Activities overview.
- **PrtSc** takes a screenshot, **Shift+PrtSc** captures a region.
- **Ctrl+Click** becomes Cmd+Click (e.g. open link in new tab).

## Setup

Install Karabiner-Elements (see the [docs](https://karabiner-elements.pqrs.org/docs/)), then copy `karabiner.json` to `~/.config/karabiner/karabiner.json`.

The config includes a `devices` section tuned for my keyboard. Karabiner will simply ignore it if your hardware doesn't match, but feel free to delete it.
