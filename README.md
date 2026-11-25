# ZMK config: Eyelash Corne, 5-column trainer (XIAO BLE dongle)

![keymap](keymap-drawer/eyeslash_corne.svg)

My [ZMK](https://github.com/zmkfirmware/zmk) configuration for an Eyelash Corne split keyboard, set up to practise a 36-key, 5-column layout before moving to a custom Chocofi-style board.

- **Keyboard:** Eyelash Corne (nice!nano v2 halves with nice!view screens)
- **Dongle:** Seeed XIAO BLE nRF52840, no screen, with ZMK Studio over USB
- **ZMK:** v0.3 (pinned)

Both halves are peripherals and the XIAO dongle is the central, which saves battery on the halves and lets the keyboard type before the OS boots.

## Build targets

Builds run from the **Actions** tab (Build ZMK firmware → Run workflow). Download the `firmware` artifact when it finishes.

| File | Flash to |
|---|---|
| `xiao_eyeslash_dongle.uf2` | XIAO dongle |
| `nano_eyeslash_left.uf2` | Left half |
| `nano_eyeslash_right.uf2` | Right half |
| `xiao_reset_settings.uf2` | Dongle, to clear pairings and saved settings |
| `nano_reset_settings.uf2` | Either half, to clear pairings and saved settings |

## Flashing

1. Plug in the board, double-press its reset button, and a USB drive appears.
2. (Optional, for a clean start) copy the matching `*_reset_settings.uf2`, wait for it to disconnect, then double-press reset again.
3. Copy the firmware file. The drive disconnects on its own when it's done.
4. Do the dongle and both halves, then plug the dongle in and turn the halves on. They pair with the dongle automatically.

After changing layers, use **Restore Stock Settings** in ZMK Studio so saved Studio edits don't override the new keymap.

## Layers

| # | Layer | How to reach it |
|---|---|---|
| 0 | Base5 | Default: 5-column QWERTY |
| 1 | Full | System + H toggles the original 6-column layout |
| 2 | ColemakDH | System + J toggles Colemak-DH |
| 3 | Mouse | Hold either Space; clicks on both thumb clusters (inner = right click, middle = left click); T = Snipping Tool (Win+Shift+S) |
| 4 | Fn | Hold right inner thumb (Return): WASD-style arrows, paging, media; browser and editor navigation on the left |
| 5 | Game | System + B; centre key returns to Base |
| 6 | Num | Hold left inner thumb (Enter) |
| 7 | Sym | Hold left outer thumb (Tab) |
| 8 | System | Hold Num + Fn together: Bluetooth, USB/BLE output, RGB, Studio unlock (V), reset |
| 9 | GameFn | Hold Game's left outer thumb: number row, F-keys |
| 10 | Precise | Mouse layer, either outer thumb: slow cursor |

Game and GameFn use plain keys and `&mo` only, because hold-taps misbehave in most games.

## Shortcuts (Windows)

**Fn layer, left hand** (hold right inner thumb). Home row stays Win / Alt / Shift / Ctrl.

| Q | W | E | R | T |
|---|---|---|---|---|
| Reopen tab (Ctrl+Shift+T) | Close tab (Ctrl+W) | Prev tab (Ctrl+Shift+Tab) | Next tab (Ctrl+Tab) | New tab (Ctrl+T) |

G: app switcher (Ctrl+Alt+Tab; pick with the Fn arrows, Enter to open)

| Z | X | C | V | B |
|---|---|---|---|---|
| Clipboard history (Win+V) | Address bar (Ctrl+L) | Command palette (Ctrl+Shift+P) | Quick open (Ctrl+P) | Terminal (Ctrl+`) |

**Mouse layer, left hand** (hold either Space):

| Q | W | E | R | T |
|---|---|---|---|---|
| Select all (Ctrl+A) | Save (Ctrl+S) | Find (Ctrl+F) | Toggle comment (Ctrl+/) | Snip (Win+Shift+S) |

G: next match / add cursor (Ctrl+D). Bottom row: Undo, Cut, Copy, Paste, Redo.

## Combos (Base5, Full and ColemakDH only)

- **Home-row mods (mirrored):** A+S Ctrl, S+D Shift (double-tap Caps Lock), D+F Alt, A+F GUI; L+; Ctrl, K+L Shift, J+K Alt, J+; GUI
- **Esc:** Q+W
- **Brackets:** F+G `(`, H+J `)`, R+T `[`, Y+U `]`, V+B `{`, N+M `}`
- **Others:** O+P `'` (hold for `"`), `.`+`/` `\`, `,`+`.` `|`

## Encoder

- **Base5, Full, ColemakDH:** Down / Up arrows
- **Mouse and Game:** scroll
- **Fn, Num, Sym, GameFn:** volume
- **System:** RGB brightness

## Dependencies

- ZMK v0.3
- nice-view-gem v0.3.0 (M165437)

## Credits

Based on the Eyeslash Corne dongle config shared by the community (shield files by Darryl deHaan and the ZMK contributors).
