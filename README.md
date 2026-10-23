## Disclaimer

I do not have a single coding experience into Kerbal Space Program.
This is "my" first ever mod 100% coded with the free plan of [claude.ai](https://claude.ai/)
Contact @Jxst_aviation on discord for more information.
 
## Code

The full source code is in the [`Source/`](Source) folder of this repository and is released under the
[MIT license](LICENSE): anyone can read, modify and redistribute it. Contributions and pull requests are welcome.
(Every release on GitHub also comes with an automatic "Source code" archive.)

## Features

This mod is a re-creation of the SpaceX telemetry during classical starship launches on Kerbal Space Program.

## Requirements

- Kerbal Space Program **1.12.x**
- Starship Expansion Project, latest version (V3 vehicules)

## Installation

1. Go to the **[Releases](../../releases)** page and download `StarshipTelemetry-<version>.zip`
   (use this file, **not** the automatic "Source code" zip).
2. Unzip it. You get a single folder named `StarshipTelemetry`.
3. Move that folder into `Kerbal Space Program/GameData/`.

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
