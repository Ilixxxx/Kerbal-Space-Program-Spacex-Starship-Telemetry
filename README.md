## Disclaimer

I do not have a single coding experience into Kerbal Space Program.
This is "my" first ever mod 100% coded with the free plan of [claude.ai](https://claude.ai/)
Contact @Jxst_aviation on discord for more information.
 
## Code

The full source code is in the 'Source/' folder of this repository and is released under the
[MIT license](LICENSE): anyone can read, modify and redistribute it. Contributions and pull requests are welcome.

## Features

This mod is a re-creation of the SpaceX telemetry during classical starship launches on Kerbal Space Program.

## Requirements

- Kerbal Space Program **1.12.x**
- Starship Expansion Project, latest version (V3 vehicules)

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

## Recommanded mods

- Physical Range Extender: Without it, you'll lost the telemetry of the ship/booster few seconds after separation due to range limits of KSP.
- kOS: With it, you can automatize the whole flight / the booster while your managing your ship.
<img width="1920" height="1080" alt="Kerbal Space Program Screenshot 2026 10 24 - 00 19 18 51" src="https://github.com/user-attachments/assets/dcbefd0d-5ff7-45eb-b63b-8b3f1f7f4a1d" />
<img width="1920" height="1080" alt="Kerbal Space Program Screenshot 2026 10 23 - 15 28 45 99" src="https://github.com/user-attachments/assets/204fe0ae-fb42-4f66-b6e3-e19f19e6acaf" />
<img width="1920" height="1080" alt="Kerbal Space Program Screenshot 2026 10 23 - 00 02 15 60" src="https://github.com/user-attachments/assets/93de6595-f5ad-4260-a239-36b9ec46d1c4" />
<img width="1920" height="1080" alt="Kerbal Space Program Screenshot 2026 10 22 - 14 36 39 56" src="https://github.com/user-attachments/assets/af9869ca-ecd5-4e87-9c08-d51e500e33f7" />

