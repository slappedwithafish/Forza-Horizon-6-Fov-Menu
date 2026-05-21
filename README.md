# Forza Horizon 6 FOV Menu — Tokyo Edition

A camera FOV adjustment tool for Forza Horizon 6, with a fresh FH6-themed UI.

## What it does

Lets you customize the field-of-view for all five in-game camera modes — **Chase**, **Far Chase**, **Driver/Dashboard**, **Hood**, and **Bumper** — with independent Min/Max values for each. Changes apply live while the game is running.

## Origin / credits

This is a **vibecoded** rebuild based on the open-source [Forza Mods FOV Menu](https://github.com/ForzaMods/Fov-Menu) (huge thanks to the Forza Mods team — all the actual memory-scanning brain power is theirs). The original tool was built for Forza Horizon 5, and while it works perfectly on FH6's engine internals (signatures didn't change), it had one annoying limitation that this build fixes.

Special shout-out to **Ichi Gaming** ([@ichi_Gaming00](https://www.youtube.com/@ichi_Gaming00)) — his [video tutorial](https://www.youtube.com/watch?v=hqHdzYfWnTs) was the first to figure out that the FH5 menu actually works on FH6 if you rename the executable. That discovery is what made this build possible — without his original workaround, nobody would have known the FH5 tool was even compatible.

## The "rename your exe" problem (and how we fixed it)

The original FH5 menu hardcodes the process name it attaches to — it only scans for `ForzaHorizon5` or `ForzaHorizon4`. So if you tried using it with FH6 directly, it'd just sit there waiting forever — because your process is named `forzahorizon6.exe`, not [forzahorizon5.exe](cci:7://file:///c:/Program%20Files%20%28x86%29/Steam/steamapps/common/ForzaHorizon6/forzahorizon5.exe:0:0-0:0). Ichi Gaming's workaround was to **rename `forzahorizon6.exe` to [forzahorizon5.exe](cci:7://file:///c:/Program%20Files%20%28x86%29/Steam/steamapps/common/ForzaHorizon6/forzahorizon5.exe:0:0-0:0)** before launching the game, which works perfectly but is gross and breaks other tools that expect the FH6 name.

### The fix

Updated the process detection logic in [Addresses.cs](cci:7://file:///c:/Users/matth/Downloads/Fov-Menu-2.0/Fov-Menu-2.0/Fov-Menu/Addresses.cs:0:0-0:0) to scan for [ForzaHorizon6](cci:9://file:///c:/Program%20Files%20%28x86%29/Steam/steamapps/common/ForzaHorizon6:0:0-0:0) first, then fall back to `ForzaHorizon5` and `ForzaHorizon4`. Backward-compatible — works with any of the three Horizon games, no exe renaming required.

## What's new in this build

- **Native Forza Horizon 6 process detection** — no more renaming
- **FH6 Tokyo Festival UI** — sakura-pink-to-cyan gradient wordmark, neon glow drop shadow, dark midnight background, card-based layout with colored category dots, modern title bar with min/close buttons
- **Live connection status bar** — shows green "CONNECTED · FORZAHORIZON6.EXE" when attached, red "WAITING FOR FORZAHORIZON6.EXE" otherwise, with a glowing status dot
- **Compact 5.9 MB build** — single exe, easy distribution
- **Signature scans untouched** — same Forza Mods scan patterns, same memory I/O, same reliability

## Requirements

- Windows 10 / 11 (x64)
- [.NET 7 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/7.0/runtime) — if you don't have it, Windows will prompt you with a direct download link the first time you run the menu

## How to use

1. Launch Forza Horizon 6
2. Run `Fov-Menu.exe`
3. Wait for the status bar to turn green (auto-attaches within 1 second)
4. Adjust the Min/Max values for each camera type — changes apply instantly in-game

## Disclaimer

Vibecoded build with AI assistance. Core memory scanning and signature logic is unchanged from the original Forza Mods tool — this is purely a process-name compatibility fix and a UI reskin. Use at your own risk; works in offline play, untested for online/multiplayer (the original tool's authors recommend offline-only out of an abundance of caution).

## Sources & credits

- **Original tool:** [github.com/ForzaMods/Fov-Menu](https://github.com/ForzaMods/Fov-Menu) — Forza Mods team
- **Compatibility discovery:** [Ichi Gaming on YouTube](https://www.youtube.com/watch?v=hqHdzYfWnTs) ([@ichi_Gaming00](https://www.youtube.com/@ichi_Gaming00))
- **This FH6 build:** vibecoded patch + Tokyo Edition theme
