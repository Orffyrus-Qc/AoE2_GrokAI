# GrokAI — Age of Empires II DE Adaptive AI

**GrokAI** is a competitive AoE2 DE AI personality built on Promisory Extreme with an adaptive layer that reads enemy openings and counters them. It uses dedicated builder villagers to erect walled compounds, gates, and towers before committing to offense.

## Features

| Module | Role |
|--------|------|
| **Detection** | Identifies drush, scout rush, archer rush, MAA flush, fast castle, boom, siege, smush, water |
| **Counters** | Civ-aware unit counter steering on top of opening detection |
| **Defense** | Full square TC wall ring with one gate on the longest side |
| **Stronghold** | Every TC and castle gets a closed stone compound with one gate |
| **Builders** | Dedicated build corps (group 19) for walls, gates, towers, TCs, castles |
| **Towers** | Defensive towers on TC flanks and resource sites |
| **Fortify** | Progressive stone walls, extended chokes, castle-age guard towers |
| **Military** | Unified attack blobs, population-scaled waves, siege escorts |
| **Age** | Fast feudal → castle → imperial with food-heavy eco while aging |

Adaptation is silent — no in-game chat spam.

## Requirements

- Age of Empires II: Definitive Edition (Steam)
- Windows
- Promisory Extreme AI (included with game install)

## Install

### Option A — Automatic (recommended)

1. Clone this repo.
2. Open the `GrokAI` folder (project root).
3. Right-click `install-on-friend-pc.ps1` → **Run with PowerShell**.
4. Launch AoE2 DE → **Mod Manager** → **Local** → enable **GrokAI**.

### Option B — Developer deploy

From the project root, run:

```powershell
.\deploy.ps1
```

This copies AI files to the Steam install, local mod mirror, and generates a test scenario.

## Test in-game

1. Enable the **GrokAI** local mod.
2. **Single Player** → **Load Scenario** → **GrokAI 1v1 Test**.
3. Pick **GrokAI** as the opponent AI (or play vs Standard AI on any map).

Watch for:

- Closed square wall ring around TC with one gate
- Builder villagers erecting compounds and towers at each TC
- Counter units (spears vs scouts, skirms vs archers, etc.)
- Adaptive response to your opening

## Steam install path

```
C:\Program Files (x86)\Steam\steamapps\common\AoE2DE
```

## Project layout

```
AoE2_GrokAI/
├── README.md
├── info.json
├── deploy.ps1
├── install-on-friend-pc.ps1
├── create_test_scenario.py
└── resources/_common/ai/
    ├── GrokAI.ai
    ├── GrokAI.per
    └── GrokAI/*.per
```

## Architecture

```
Promisory Extreme (economy, units, buildings, researches)
  → constants → memory → intel → detection → superiority → counters → response
  → economy → builders → gatealign → defense → isolate → towers → fortify
  → stronghold → military → preattack → explore → raid → coordination → age
```

## License / credits

- **Author:** Orffyrus
- **Base AI:** Promisory Extreme (game install)
- **Adaptive layer:** GrokAI modules
- Use and modify freely; no warranty.