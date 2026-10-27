# The Northern Front — IRONFRONT

**A single-file, browser-based 3D combined-arms battlefield game.**

Take to the battlefield as infantry, command an armoured vehicle, fly an attack helicopter, or pilot a bomber. Fight alongside your squad, push across capture sectors, and adapt your loadout to three distinct environments.

The game is branded **IRONFRONT — Operation Cold Horizon** in its interface. The playable experience is implemented in `index.html`, with the project licensed under the Apache License 2.0.

## Features

- **Five deployment types:** MBT-90 main battle tank, IFV-80 infantry fighting vehicle, rifleman, AH-6 Talon attack helicopter, and B-24 Hammer bomber.
- **Three environments:** Karst Valley, Frost Reach, and Dune Sea, each with its own operation and sector names.
- **Combined-arms combat:** fight ground units and aircraft, use different vehicle weapons, and make use of vehicle armour and splash damage.
- **Capture-sector objectives:** contest territory across the battlefield and use friendly sectors to repair vehicles and replenish supplies.
- **Squad commands:** direct your three squadmates to follow you, hold position, or attack a sector.
- **Vehicle interaction:** enter and exit vehicles, switch between exterior and crew-eye views, and take control of marked anti-aircraft missile emplacements.
- **Tactical overview:** track allied and hostile units and battlefield objectives on the minimap.
- **Responsive controls:** keyboard and mouse on desktop, with touch movement, aiming, and firing controls on touchscreens.
- **Configurable settings:** adjust graphics quality, resolution, shadows, field of view, performance options, audio volume, aim sensitivity, axis inversion, zoom behaviour, and key bindings.
- **No build step:** the game and its styling and gameplay code live in a single HTML file.

## Play

### Run locally

You need a modern browser with WebGL support and an internet connection. The game imports Three.js modules from jsDelivr; serving the file over HTTP also avoids browser restrictions that can affect ES modules when opening an HTML file directly.

1. Download or clone this repository.
2. Open a terminal in the project directory.
3. Start a local static web server:

   ```bash
   python3 -m http.server 8000
   ```

4. Open [http://localhost:8000](http://localhost:8000) in your browser.

Stop the server with `Ctrl+C`.

> **Internet requirement:** the game loads Three.js from the jsDelivr CDN. The interface also requests fonts from Google Fonts. You do not need to install Node.js, npm, or a separate game engine, but the CDN-hosted Three.js modules must be reachable for the game to initialise.

### Host it on a website

Because this is a static HTML project, it can be hosted by any static-file web host. To publish it with GitHub Pages, open the repository's **Settings → Pages**, choose the `main` branch and the root folder, and save. Once GitHub Pages has finished publishing, use the URL it provides. The first load still needs access to the external Three.js CDN.

## Controls

The defaults shown in the game are:

| Input | Action |
| --- | --- |
| `W` `A` `S` `D` | Move |
| Left mouse button | Fire |
| Right mouse button | Aim/zoom, depending on the selected zoom setting |
| `F` | Enter or exit a vehicle; take a nearby AA gunner seat |
| `R` | Resupply or reload when possible |
| `Q` | Open squad orders |
| `1`, `2`, `3` | Order the squad to sector A, B, or C |
| `M` | Toggle the tactical map |
| `P` | Switch between crew-eye and exterior view |
| `Shift` / `Space` | Aircraft-specific controls; also used for sprint/brake or jump where applicable |
| `Esc` | Pause or open settings; releases mouse capture |

Click the battlefield to capture the mouse for aiming. Press **Esc** to release it. Controls can be rebound in the settings menu.

### Aircraft controls

- **AH-6 Talon helicopter:** `Shift` climbs, `Space` descends, `W`/`S` moves forward/backward, and `A`/`D` swings the nose.
- **B-24 Hammer bomber:** `Shift`/`Space` control throttle, `W`/`S` controls the elevator, and `A`/`D` banks the aircraft. The bomber carries three bombs; bombs can be replenished inside a friendly sector.

On a touchscreen, use the left on-screen stick to move, drag on the right side to aim, and use the on-screen buttons to fire or interact.

## Technology

- **HTML, CSS, and JavaScript** in a single `index.html` file
- **Three.js 0.160.1** for 3D rendering, imported as browser ES modules from jsDelivr
- **Web Audio API** for in-game audio
- **Local storage** for saved settings and custom key bindings

There is no package manifest or build pipeline in this repository. For development, edit `index.html`, refresh the browser, and check the browser's developer console if the scene fails to initialise.

## Project structure

```text
The-Northern-Front/
├── index.html   # Game interface, styling, rendering, and gameplay
└── LICENSE      # Apache License 2.0
```

## Known considerations

- A working internet connection is required to retrieve the Three.js modules from the CDN.
- Performance depends on the device, browser, GPU, and selected graphics settings. Lowering quality, resolution, or shadows may help on slower hardware.
- The gameplay and controls are evolving; not every device/browser combination has been independently tested.

## License

This project is distributed under the **Apache License 2.0**. See [LICENSE](LICENSE) for the full text.
