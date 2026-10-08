# WarZone

A 3D combat game that runs in the browser. Pick an era, then fight as a tank commander or as an infantryman, holding a valley road and a ruined village against waves of enemy armour and infantry.

## Play

Open `index.html` in a desktop browser, or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

Three.js, N8AO and postprocessing load from the jsDelivr CDN, so you need a network connection.

## Eras and maps

Each era is self-contained and has its own map. Switching era rebuilds the world (the page reloads), and nothing crosses between eras.

| Era | Map | Your vehicles | Enemy vehicles | Your kit | Enemy infantry |
| --- | --- | --- | --- | --- | --- |
| WW2 Italy · 1944 | Apennine valley with a hill town of tiled roofs | M4A3E8 Sherman, Cromwell Mk IV, Churchill Mk VII | Panzer IV Ausf. H, Panther Ausf. G, Tiger I | M1 Garand, M1A1 Bazooka | Kar98k riflemen, Panzerschreck teams |
| D-Day · 1944 | Omaha Beach: swim ashore in a DD Sherman with its flotation screen up, or ride in on a Higgins boat until the ramp drops; land on the sand, cross the obstacle belt, take the bunkers on the bluffs and push up the draws to a Norman village; the fleet fires from offshore | M4A3E8 Sherman, Churchill Mk VII, Cromwell Mk IV | Panzer IV Ausf. H, Panther Ausf. G, Tiger I | M1 Garand, M1A1 Bazooka | MG42 bunker crews, Kar98k riflemen, Panzerschreck teams |
| Korea · 1951 | Steep snowy mountain valley and a small village | M26 Pershing, M46 Patton, M24 Chaffee | T-34-85 | M2 Carbine, M20 Super Bazooka | PVA riflemen with PPSh-41s, captured M20s |
| Vietnam · 1968 | Jungle hills, red earth and a village of thatched huts | M48A3 Patton, Centurion Mk 5/1, M551 Sheridan, M113 ACAV | PT-76B, T-54A, T-55 | M16A1, M72 LAW | AK-47 riflemen, RPG-7 teams |
| Cold War · 1985 | Rolling Fulda Gap farmland and a German town | M1 Abrams, Leopard 2A4, M60A3 Patton, M2 Bradley (+ Marder 1A3 allies) | T-72A, T-64B, T-80B, BMP-1, BMP-2 | M16A2, M47 Dragon (wire-guided) | AK-74 riflemen, RPG-7 teams |
| Modern | A city of apartment blocks and high-rises in a mountain valley | M1A2 Abrams, Leopard 2A6, Challenger 2, M2A3 Bradley (+ Warrior allies) | 2S25 Sprut-SD, T-72B3, T-80BVM, T-90M, T-14 Armata, BMP-2, BMP-3 | M4A1, FGM-148 Javelin | AK-74M riflemen, RPG-7 teams |

Armour is modelled in millimetres: every gun has a penetration value that falls off with range, and every vehicle has front, side and rear armour that grows with impact angle, so a Panther shrugs off a Sherman's 76 mm from the front but not from the side. Hits can throw a track, start an engine fire, jam the turret ring or wound a crewman; crews repair in the field. The radar only shows enemies your side has actually spotted. Tanks halt to fire (they are far less accurate on the move) and pop smoke and back off when badly hit. Every building can be destroyed: shell it until it collapses, or drive a tank straight through it. IFVs fire rapid autocannons, launch anti-tank missiles and drop off a rifle squad near the enemy.

## Controls

**Tank commander**

| Control | Action |
| --- | --- |
| W A S D | Drive and steer the hull |
| Mouse | Traverse the turret and lay the gun |
| Left click | Fire the main gun |
| Right click / Shift | Gunner's sight (zoom) |
| Space | Coaxial machine gun |
| F | IFV: fire a TOW missile (guided onto the crosshair) |
| X | Smoke grenades: a screen that blocks line of sight |
| E | IFV: dismount your rifle squad |

**Infantry**

| Control | Action |
| --- | --- |
| W A S D | Move (Shift sprint, C crouch, Z prone, Space jump) |
| Mouse | Look and aim |
| Left click | Fire |
| Right click | Aim down sights (red dot or iron sights); with the Javelin, hold near a tank to lock on; with the Dragon, keep the sight on the tank until impact |
| 1 / 2 or Q | Rifle or anti-tank launcher |
| R | Reload |
| G | Throw a grenade |

Esc pauses. Phones and tablets get a joystick, drag-to-aim and on-screen buttons.

## What's in it

- Procedural 2 km valley with a lake, road, ruined village, forests, dense wind-blown 3D grass, wildflowers and burning wrecks
- Raymarched volumetric clouds that cast drifting shadows, forested mountains with eroded rock, golden-hour sky, image-based lighting, soft shadows with a far cascade out to the horizon, ambient occlusion, light shafts, lens flare, bloom and per-era colour grading
- Eighteen procedurally modelled tanks with animated tracks, crews, period insignia and paint
- Ballistic gunnery, ricochets, armour zones, tank cook-offs, splash damage and tracers
- Battle sizes from Standard to Epic: up to 50 enemy tanks and 100 enemy infantry at once, 8 allied tanks and well over a hundred soldiers
- Infantry on both sides that take cover, bound forward in pairs, go prone under fire, reload, throw grenades and get thrown by blasts; incoming rounds crack past and pin you down
- Allied air strikes and artillery barrages on enemy positions, with smoke from burning towns on the horizon
- Infantry squads with riflemen and anti-tank gunners, an allied fireteam, and tanks that hunt infantry with their machine guns
- A Javelin that locks on and flies a top-attack profile, a wire-guided Dragon, and unguided LAW and Bazookas
- Tanks can't enter the lake; infantry can wade the shallows
- Low, High and Ultra graphics presets, stepped down automatically if your computer can't keep a smooth frame rate
