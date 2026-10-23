# Starship Telemetry (KSP)

A "Starship Flight" style telemetry overlay for **Kerbal Space Program 1.12.x**: Super Heavy engine cluster and
speed on the left, Starship engines and speed on the right, a live T+ clock with a scrolling milestone timeline
in the middle, and an attitude icon for the stack / booster / ship.

> Fan project, not affiliated with SpaceX. The look of the overlay and the attitude icons are inspired by
> SpaceX's webcast telemetry.

## Open source

The full source code is in the [`Source/`](Source) folder of this repository and is released under the
[MIT license](LICENSE): anyone can read, modify and redistribute it. Contributions and pull requests are welcome.
(Every release on GitHub also comes with an automatic "Source code" archive.)

## Features

- Super Heavy: 33 Raptor dots (3 / 5 / 13 / 33 engine modes), fuel ring, speed gauge
- Starship: 3 sea-level + 3 vacuum Raptors (each real engine lights its own dot), fuel ring, speed / altitude gauges
- Attitude icon (stack, booster or ship) that follows the pitch of the vehicle
- T+ clock: auto (starts at liftoff), game MET, or manual countdown
- Timeline that starts as a straight line and gradually curves, with milestones (Liftoff, Max Q, Stage Sep,
  Super Heavy Landing, SECO, Entry, Landing...) that are detected in game, editable in game
- Customisable mission name under the clock (e.g. `STARSHIP FLIGHT 15`)
- Layout presets (Classic / Flight / Custom) with 4 configurable data slots
- Keeps tracking the booster and the ship after separation, even when they are far apart

## Requirements

- Kerbal Space Program **1.12.x**
- A Starship / Super Heavy rocket whose engine parts can be recognised by name (see *Part names* below)

## Installation

1. Go to the **[Releases](../../releases)** page and download `StarshipTelemetry-<version>.zip`
   (use this file, **not** the automatic "Source code" zip).
2. Unzip it. You get a single folder named `StarshipTelemetry`.
3. Move that folder into `Kerbal Space Program/GameData/`.

That's it: no compiling, no command line.
To update, delete the old `GameData/StarshipTelemetry` folder and copy the new one
(your settings live in `PluginData/settings.cfg` inside it, so keep that file if you want to keep them).

## Usage

- The telemetry is **hidden when KSP starts**. In flight, click the rocket icon in the application launcher
  (icon bar on the right) to show / hide it.
- **Control panel:** press `F10`, or click the small `≡` button at the bottom right of the overlay.
  - **Clock** - mission name, clock mode (Auto / Game MET / Manual with T- countdown)
  - **Display** - Classic / Flight / Custom layout, choice of the 4 data slots, size, opacity
  - **Milestones** - enable / disable milestones, set their times, add custom ones
  - **Tools** - engine diagnostics (writes what the mod detects into `KSP.log`), ship engine dot mapping
- `F2` does not hide the telemetry unless `hideWithF2 = true` in the cfg.

## Configuration

Edit `GameData/StarshipTelemetry/StarshipTelemetry.cfg` (every option is commented). Values changed in the
in-game panel (mission name, size, opacity) are saved to `GameData/StarshipTelemetry/PluginData/settings.cfg`.

### Part names

The mod finds the engines by words contained in the part name / title (all configurable in the cfg):

| What | Default keyword | Example part |
|---|---|---|
| Super Heavy engine cluster | `andrada` | Behemoth BL-3 "Andrada" Engine Cluster (modules `OuterTwenty`, `MiddleEight`, `MiddleTwo`, `CenterThree`) |
| Ship sea-level engines | `nagata` | Nagata 3 SL-C Engine |
| Ship vacuum engines | `draper` | Draper 3 VAC Engine |
| Ship reference part | `ship.core`, `donnager` | Donnager BL-3 Main Body |

If something is not detected or the wrong dot lights up: open the control panel > **Tools** >
*Write detected engines to KSP.log* and look for the `ENGINE DUMP` block in `KSP.log`. The *Rotate / Mirror*
options in the same tab fix the ship engine dot mapping.

## Building from source (developers only)

Players do **not** need this.

- **Automatically on GitHub:** push a tag like `v1.0.0` (`git tag v1.0.0 && git push --tags`). The workflow in
  `.github/workflows/release.yml` builds `StarshipTelemetry.dll` against the KSP 1.12.5 reference assemblies and
  publishes the release zip. It can also be started by hand from the *Actions* tab.
- **Locally:**
  ```
  cd Source
  dotnet build -c Release "-p:KSPDir=C:/path/to/Kerbal Space Program"
  ```
  The DLL is written to `GameData/StarshipTelemetry/Plugins/`.
- **Textures:** `Tools/bake_atlas.py` regenerates `GameData/StarshipTelemetry/Textures/atlas.png` and
  `atlas.txt` (needs Python with Pillow and numpy). The attitude icons come from `Tools/icons/*.png`
  (nose up, dark interior); replace a PNG and run the script again to change an icon. If a PNG is missing, the mod
  draws a vector fallback shape.

## Credits

- Code: MIT license - see `LICENSE`.
- Font: **D-DIN Bold** (Datto), SIL Open Font License 1.1 - see `D-DIN-OFL-1.1.txt`.
