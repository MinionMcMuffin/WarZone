# WarZone

A 3D combat game that runs in the browser. Pick an era, then fight as a tank commander or as an infantryman, holding a valley road and a ruined village against waves of enemy armour and infantry.

## Play

Open `index.html` in a desktop browser, or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

Three.js, N8AO and postprocessing load from the jsDelivr CDN, so you need a network connection.

## Eras

Each era is self-contained: tanks, infantry weapons, uniforms, insignia, wrecks and colour grade all match the period, and nothing crosses between eras.

| Era | Your tanks | Enemy tanks | Your kit | Enemy infantry |
| --- | --- | --- | --- | --- |
| WW2 · 1944 | M4A3E8 Sherman, Cromwell Mk IV, Churchill Mk VII | Panzer IV Ausf. H, Panther Ausf. G, Tiger I | M1 Garand, M1A1 Bazooka | Kar98k riflemen, Panzerschreck teams |
| Vietnam · 1968 | M48A3 Patton, Centurion Mk 5/1, M551 Sheridan | PT-76B, T-54A, T-55 | M16A1, M72 LAW | AK-47 riflemen, RPG-7 teams |
| Modern | M1A2 Abrams, Leopard 2A6, Challenger 2 | 2S25 Sprut-SD, T-72B3, T-80BVM, T-90M, T-14 Armata | M4A1, FGM-148 Javelin | AK-74M riflemen, RPG-7 teams |

## Controls

**Tank commander**

| Control | Action |
| --- | --- |
| W A S D | Drive and steer the hull |
| Mouse | Traverse the turret and lay the gun |
| Left click | Fire the main gun |
| Right click / Shift | Gunner's sight (zoom) |
| Space | Coaxial machine gun |

**Infantry**

| Control | Action |
| --- | --- |
| W A S D | Move (Shift sprint, C crouch, Space jump) |
| Mouse | Look and aim |
| Left click | Fire |
| Right click | Aim down sights; with the Javelin, hold on a tank to lock on |
| 1 / 2 or Q | Rifle or anti-tank launcher |
| R | Reload |

Esc pauses. Phones and tablets get a joystick, drag-to-aim and on-screen buttons.

## What's in it

- Procedural 2 km valley with a lake, road, ruined village, forests, dense wind-blown 3D grass, wildflowers and burning wrecks
- Golden-hour sky, image-based lighting, soft shadows, ambient occlusion, light shafts, lens flare, bloom and per-era colour grading
- Eighteen procedurally modelled tanks with animated tracks, crews, period insignia and paint
- Ballistic gunnery, ricochets, armour zones, tank cook-offs, splash damage and tracers
- Infantry squads with riflemen and anti-tank gunners, an allied fireteam, and tanks that hunt infantry with their machine guns
- A Javelin that locks on and flies a top-attack profile; unguided LAW and Bazooka
- Low, High and Ultra graphics presets
