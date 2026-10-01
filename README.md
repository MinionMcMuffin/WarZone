# WarZone

A 3D tank game that runs in the browser. You command a main battle tank holding a valley road and a ruined village against waves of enemy armour.

## Play

Open `index.html` in a desktop browser, or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

Three.js loads from the jsDelivr CDN, so you need a network connection the first time.

| Control | Action |
| --- | --- |
| W A S D | Drive and steer the hull |
| Mouse | Traverse the turret and lay the gun |
| Left click | Fire the 120 mm main gun |
| Right click / Shift | Gunner's sight (zoom) |
| Space | Coaxial machine gun |
| Esc | Pause |

On phones and tablets you get a joystick, a drag-to-aim area, and fire, MG and zoom buttons.

## What's in it

- Procedural 2 km valley terrain, with a road, a ruined village, forests, rocks, wind-blown grass, telegraph lines and burning wrecks
- Physically based lighting from a golden-hour sky, image-based environment light, soft shadows and drifting clouds
- Detailed tank models with animated tracks and road wheels, a turret that traverses at a realistic rate, gun recoil and suspension pitch
- Ballistic shells, ricochets on oblique armour hits, front/side/rear damage zones, falling trees, track marks and scorch decals
- Particle explosions, muzzle blast, dust, fire and smoke columns, plus debris and a turret that blows off when a tank is destroyed
- Enemy AI that flanks, leads its shots and needs line of sight to fire
- Bloom, SMAA, colour grading, film grain and a damage vignette
- Synthesised audio for the engine, the cannon, explosions, the MG and ricochets
- Low, High and Ultra graphics presets
