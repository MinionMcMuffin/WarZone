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

Armour is modelled in millimetres: every gun has a penetration value that falls off with range, and every vehicle has front, side and rear armour that grows with impact angle, so a Panther shrugs off a Sherman's 76 mm from the front but not from the side. Hits can throw a track, start an engine fire, jam the turret ring or wound a crewman; crews repair in the field. The radar only shows enemies your side has actually spotted. AP rounds punch through armour; HE (or HEAT-MP in later eras) bursts wide against infantry and buildings but bounces off thick plate. Tanks are fastest on roads and paved streets and bog down in beach sand. On foot, sprinting runs you out of breath and your sights sway, less when crouched or prone and almost not at all while you hold your breath. Badly mauled enemy squads break and fall back, and the wider battle rumbles in the distance. Tanks halt to fire (they are far less accurate on the move) and pop smoke and back off when badly hit. Every building can be destroyed: shell it until it collapses, or drive a tank straight through it. IFVs fire rapid autocannons, launch anti-tank missiles and drop off a rifle squad near the enemy.

**Battle flow**

- **Objectives.** Every wave comes with a task: destroy an enemy ace (a tougher, faster-loading, more accurate tank with its own name, ringed in gold on the radar), take the village (get in, clear out their armour and hold it while green smoke marks the spot), or knock out every anti-tank position. The objective panel and a gold diamond on the compass point the way. Completing it scores a bonus and an extra promotion.
- **Field promotions.** Each cleared wave you choose one of three upgrades (press 1, 2 or 3, or tap). Tank crews can take a faster loader, better ammunition, extra armour, a field workshop, a bigger ready rack, gunnery school, a tuned engine or crew drill. On foot you get extra magazines, body armour, more launcher rounds, a steadier aim or a medic. Either way you can take priority fire support, a reinforced platoon or close air support. Most stack up to three ranks.
- **Hit feedback.** Your rounds tag what they did where they struck: PEN and the zone, NO PEN, WEAK SPOT, RICOCHET or REACTIVE ARMOUR. Kills get a big DESTROYED or KNOCKED OUT and a beat of slow motion.
- **After-action report.** When your battle ends you see the rank you earned, time in action, armour destroyed by type, infantry, positions and aircraft, your gunnery accuracy and penetration rate, objectives, damage taken and the promotions you chose.
- Dug-in anti-tank crews don't hold up the end of a wave; whatever survives stays in position into the next one. The last two tanks of an attack stop hanging back and press home.

**Tank warfare**

- **Ways to die.** A penetrating hit can find the ammunition and blow the turret off at once (carousel autoloaders in the T-64/72/80 are the worst for it; the Abrams' blow-out panels and the T-14's crew capsule make it rare). Otherwise a tank is knocked out and left burning, its surviving crew bail out, and the fire may still reach the ammunition a few seconds later. Enemy crews run for their own lines; friendly crews fight on as riflemen.
- **Bail out.** If your own tank is knocked out rather than blown up, you climb out and carry on fighting on foot.
- **More to break.** As well as tracks, turret ring, crew and engine fires, hits can now damage the engine (you limp along at under half speed) or jam the breech (no firing until it is cleared).
- **Gun stabilisation.** WW2 and Korean War guns are only accurate at the halt with the turret still; the aiming ring opens up as you drive or traverse. Vietnam-era stabilisers help, and Cold War and modern tanks shoot accurately on the move. AI crews follow the same rule: old tanks halt to fire, modern ones fight at speed.
- **Reactive armour.** T-64B, T-80B, T-72B3, T-80BVM and T-90M carry explosive bricks that break up the first HEAT rounds, rockets and missiles to hit each face. Kinetic AP ignores them, and so does a hit on the rear or roof.
- **Active protection.** The M1A2's Trophy and the T-14's Afghanit shoot down incoming rockets and missiles until their charges run out. Afghanit cannot reach a diving Javelin.
- **Enemy platoons.** Enemy armour arrives in platoons of two to four with a job: assault head-on, work round a flank (scouts warn you which way), or sit back on overwatch at long range. Tanks turn their frontal armour to the threat when they halt, pick targets they can actually hurt, hold fire when a friend is in the way, and infantry squads move up behind them.
- **You command the platoon.** `T` cycles your tanks between follow me, hold position and attack. `V` marks the enemy tank in your sights so the whole platoon engages it. `B` calls an artillery fire mission onto the ground you are aiming at (50 second reload, refused if it is danger close).
- **Anti-tank positions.** Each wave the enemy digs in anti-tank weapons overlooking your line of advance: Pak 40s (WW2, D-Day), ZiS-3 guns (Korea), SPG-9 recoilless rifles (Vietnam), Fagot (Cold War) and Kornet (Modern) missile teams. They stay hidden until they fire, when the launch dust gives them away. Knock them out with a direct hit, artillery or air, kill the crew, or drive straight over them.
- **Wire-guided missiles can be beaten.** Missiles from ATGM teams and helicopters fly onto you while the gunner can see you. Pop smoke between you and the launcher, or kill the gunner, and the missile loses guidance. You get a warning with a clock bearing when one is fired at you.
- **Attack helicopters.** Hueys (Vietnam), Cobras (Cold War) and Apaches (Modern) come on station to hunt enemy armour with missiles, rockets and guns. From wave 2 the enemy can send a Mi-24 Hind (Cold War) or Ka-52 (Modern) at you. Helicopters hover off at stand-off range, climb and reposition when they can't see, and leave when they're out of ammunition or badly hit. Shoot them down with the coax, an IFV's autocannon, a main gun round or a Javelin (it locks on to helicopters); allied IFVs engage them too.
- **FPV drones (Modern).** From wave 2, cheap one-way attack quadcopters buzz in and dive onto the thin roof armour. Listen for the whine, then shoot them down; allied IFVs help.
- **Thermal sight** (`N`, Cold War and modern tanks). White-hot imaging: engines, crews and fires glow, the sky goes dark, and smoke and dust no longer hide anything.
- **Enemy artillery.** From wave 2, sitting in one spot for too long brings enemy guns down on you. You get a warning and a few seconds to move.

## Controls

**Tank commander**

| Control | Action |
| --- | --- |
| W A S D | Drive and steer the hull |
| Mouse | Traverse the turret and lay the gun |
| Left click | Fire the main gun |
| Right click / Shift | Gunner's sight (zoom) |
| Space | Coaxial machine gun |
| 1 / 2 | Load armour-piercing or high-explosive (switching unloads the round in the breech) |
| F | IFV: fire a TOW missile (guided onto the crosshair) |
| X | Smoke grenades: a screen that blocks line of sight |
| N | Thermal sight (Cold War and modern tanks) |
| T | Platoon orders: follow me, hold position, attack |
| V | Mark the enemy tank in your sights for the platoon |
| B | Artillery fire mission on your aim point |
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
| Shift while aiming | Hold your breath to steady the sights |
| G | Throw a grenade |
| T / V / B | Order the tanks, mark a target, call artillery |

Esc pauses. Phones and tablets get a joystick, drag-to-aim and on-screen buttons, including ammunition, smoke, orders, target marking, artillery and thermal.

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
