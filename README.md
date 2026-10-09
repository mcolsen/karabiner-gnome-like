# GNOME-like keyboard shortcuts for macOS

A [Karabiner-Elements](https://karabiner-elements.pqrs.org/) config that makes a Mac feel like GNOME.

## Common shortcuts

- **Ctrl acts as Cmd** for letters, numbers, zoom, and common punctuation shortcuts in GUI apps. Standalone terminals are excluded, so Ctrl+C still interrupts.
- **Ctrl+Left/Right** moves by word, **Ctrl+Backspace/Delete** deletes a word, and **Ctrl+Home/End** moves to document boundaries in GUI apps. Shift extends selections where the app supports it.
- **Ctrl+Shift+C/V/T/W/N/F in terminals** maps to copy, paste, new tab, close tab, new window, and find.
- **Alt+Tab** switches apps, and **Alt+`** cycles windows of the same app. Shift reverses the direction.
- **Ctrl+Click** becomes Cmd+Click, including opening links in iTerm2. The mouse must be enabled in Karabiner's Devices settings.
- **Ctrl+H** opens History in Chrome/Firefox and Replace in VS Code. VS Code's **Ctrl+G/M** opens Go to Line and toggles Tab Moves Focus.

Standalone terminal matching covers Terminal, iTerm2, Alacritty, kitty, WezTerm, Warp, Hyper, Ghostty, and Tabby. Explicit shortcuts allow Caps Lock to remain on.

## Super and desktop shortcuts

The **left Command/Win key** acts as Super for these shortcuts. A solo tap within 300 ms opens Mission Control. Command is sent immediately while held, so native modifier and mouse behavior does not wait for another key. Right Command retains native Mac shortcuts.

| Shortcut | Action |
| --- | --- |
| Super+Left/Right | Tile window to the left/right half |
| Super+Up | Maximize using macOS Fill |
| Super+Down | Restore the window's size before tiling |
| Super+PageUp/PageDown | Switch to the previous/next Space |
| Super+H | Minimize the current window |
| Super+L | Lock the screen |
| PrtSc | Open the screenshot interface |
| Shift+PrtSc | Capture the entire screen |
| Alt+PrtSc | Select a window to capture |

Window tiling uses macOS's Fn+Ctrl shortcuts and requires macOS Sequoia or later. Space switching requires the system Ctrl+Left/Right shortcuts to be enabled. Alt+PrtSc requires a click to select the window on macOS.

## Additional iTerm2 shortcuts

These mappings are scoped to iTerm2 because other terminals can use different native shortcuts.

| Shortcut | Action |
| --- | --- |
| Ctrl+PageUp/PageDown | Previous/next tab |
| Ctrl+Shift+PageUp/PageDown | Move tab left/right |
| Alt+1 through Alt+8 | Select numbered tab |
| Ctrl+Shift+W | Close the current tab, including all its panes |
| Ctrl+Shift+Q or Alt+F4 | Close the terminal window |
| Ctrl+Shift+G/H | Find next/previous |
| Ctrl+Shift+J | Clear Find |
| Ctrl++ / Ctrl+- / Ctrl+0 | Increase/decrease/reset text size |
| F11 | Toggle fullscreen |

Plain Ctrl+C/D/Z/L/R/S/Q remains available to the shell. Alt+9/0 is not translated: GNOME selects the ninth/tenth tab, while iTerm2's Cmd+9 selects the last tab and Cmd+0 resets text size.

## Setup

1. Install Karabiner-Elements (see the [docs](https://karabiner-elements.pqrs.org/docs/)).
2. Back up any existing `~/.config/karabiner/karabiner.json`, then copy this repository's `karabiner.json` there. Karabiner reloads it automatically.
3. In **Karabiner Settings > Devices**, enable **Modify events** for the external mouse you actually use. Mice are ignored by default, so the Ctrl-click rule alone is insufficient.
4. For Linux-style Alt+B/F/D in iTerm2, set **Settings > Profiles > Keys > General > Left Option Key** to **+Esc**. Right Option can remain Normal for special characters. This repository does not change iTerm2 preferences.

The `devices` section includes personal device entries, including a Logitech receiver's pointing interface (vendor 1133, product 50475). They apply only to matching hardware. Enable your own external mouse if it differs. The built-in trackpad is not enabled; capturing Apple pointing devices can interfere with touch features.

## Limits

- Mission Control approximates the GNOME overview but lacks its integrated typing-to-search. Unmapped Super combinations still act as native Command shortcuts. Launcher, notifications, input-source switching, moving windows between Spaces/monitors, and universal Alt+F4 behavior are not fully emulated.
- Karabiner sees the frontmost application, not whether an editor's embedded terminal has focus. VS Code's integrated terminal needs native bindings using `terminalFocus`; the GUI Ctrl translations otherwise apply there too.
- Ctrl-to-Cmd translation is an approximation across apps. Plain Home/End and app-specific commands can differ from Linux. Native app switching also differs from GNOME in grouping and handling minimized windows.
- Ctrl-click translation applies when clicking with an enabled mouse. It does not translate Ctrl-hover or automatically cover other mice and trackpads.

The configuration was audited against [GNOME desktop shortcuts](https://help.gnome.org/gnome-help/shell-keyboard-shortcuts.html), [GNOME Terminal shortcuts](https://help.gnome.org/gnome-terminal/adv-keyboard-shortcuts.html), [iTerm2 3.6.11 menu bindings](https://github.com/gnachman/iTerm2/blob/v3.6.11/Interfaces/MainMenu.xib), and [macOS window tiling shortcuts](https://support.apple.com/guide/mac-help/mac-window-tiling-icons-keyboard-shortcuts-mchl9674d0b0/mac). Karabiner 16.2.0 accepted the rules on macOS 26.7.1 and confirmed configuration reload and mouse capture. Physical shortcut behavior still needs interactive confirmation.
