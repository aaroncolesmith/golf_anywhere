# Visual improvement log — Portland: Golf Anywhere

## Pass 1 — 2026-07-03
Baseline = initial build (score 100). Verdict: **KEPT** — obvious improvement across all 7 test angles.

**Life & motion**
- 56 animated cars (9 body colors, dark cabins, wheels) driving all downtown/eastside streets **and over all three bridges**, following the deck elevation profile
- 42 pedestrians walking sidewalks, the waterfront path, the Esplanade, and Pioneer Courthouse Square, with walk-bob
- 9 seagulls circling and flapping over the Willamette

**Architecture**
- Facade generator expanded: 4 variants per style, glass in 5 hue families (blue/teal/green/bronze/steel) with optional spandrel bands, concrete in 5 tones with paired-window rhythm, brick in 5 tones with vertical coursing, sills, lintels, and glass glints
- Lit ground-floor storefront bands (awnings in 6 colors, doors, warm shop windows) on all downtown buildings — glow in gloom mode
- Parapet caps on every generated building; 5 roof tones instead of 1
- Landmark identity pinned: Big Pink = pale rose glass, Wells Fargo = white-blue

**Ground & lighting**
- Zebra crosswalks at every downtown intersection + curb lines around all blocks
- Sun lowered (0.66 → 0.52 elevation) for long late-afternoon shadows

**Vegetation**
- Leafy trees switched to flat-shaded icosahedron clumps; firs flat-shaded — sculpted low-poly look

**Verified after pass**: 0 console errors · 33/33 walking legs OK · 13/13 named areas reachable on foot · hole generation + swing physics intact.

## Pass 2 — 2026-07-03
Baseline = pass 1. Verdict: **KEPT** — Hood/waterfront/gloom angles all clearly better.

**Backdrop**
- Mt. Hood & St. Helens rebuilt: noise-displaced 26-segment cones with per-vertex rock/snow/forest coloring and ragged snowlines, flat-shaded — replaces the smooth "glass pyramid" cones
- Rescaled and pushed back after comparison (Hood was dwarfing the skyline); now peeks from behind the towers in the Rose Garden view like the real thing

**Atmosphere & light**
- Sky shader: warm haze band near the sun's azimuth at low altitude
- Gloom mode: warm lamplight pools on the ground under all ~100 lampposts (additive, fade in with weather)

**Water**
- Animated foam streak lines hugging both river banks

**Landmarks**
- Pioneer Courthouse got a real classical facade: two rows of arched windows, string courses, cornice band

**Golf presentation**
- Fairway overlay now has alternating mow stripes (vertex-colored bands)
- Green gained a darker fringe ring

**Verified after pass**: 0 console errors · 33/33 walking legs · 13/13 areas reachable · swing test clean.

## Pass 3 — 2026-07-03
Baseline = pass 2. Verdict: **KEPT**, with one experiment rejected after comparison.

**Gloom atmosphere**
- Cars got head- and taillights (warm white / red) that switch on in the gloom
- Pedestrians raise colored umbrellas when the rain starts
- Low mist banks drift over the Willamette in gloom
- **Rejected**: wet-ground env-map sheen — the side-by-side showed it washed the park out to frosted mint instead of reading "wet"; reverted

**Materials & detail**
- Bridge decks: procedural worn-asphalt texture with yellow center dashes and white edge lines (tiles per 10 m segment); speckle regraded to grayscale after the first version looked like confetti up close
- Full-terrain multiply grain overlay — the ground finally has tooth at close range instead of mipmap blur
- Pioneer Square brick arcs softened (moiré fix)

**Verified after pass**: 0 console errors · 33/33 walking legs · 13/13 areas reachable · swing test clean.

## Pass 4 — 2026-07-03
Baseline = pass 3. Verdict: **KEPT**.

**Showpiece & horizon**
- Rose bushes rebuilt as two layers: flat-shaded green clump + colored bloom cluster (was: single pink gumball)
- Horizon sprawl: ~150 hazy low-rise blocks north and south of the playable area over ground-skirt planes — the city no longer ends at a grass cliff
- Sun glints: 420 additive sparkle points drifting downstream on the river, sunny weather only

**Golf readability**
- Shot tracer: white arc line records each ball flight and stays visible while you walk to your ball; resets per shot

**Testing infrastructure** (found while verifying)
- Headless Chromium throttles requestAnimationFrame, so live-time flight barely advances in the rig — added `__GA.step(n)` for deterministic simulation stepping; the game itself was healthy
- Walking route updated to follow Burnside → 6th-ave streets after the facade rand-stream shift re-rolled building layouts (the old diagonal shortcut dead-ended in a courtyard)

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing test clean · mid-flight tracer capture confirmed ball at 32 m altitude, 100 m downrange.

## Pass 5 — 2026-07-03
Baseline = pass 4. Verdict: **KEPT**.

**Street level**
- 52 parked cars along downtown curbs (solid — the ball caroms off them), sharing the traffic fleet's instanced geometry

**Washington Park**
- ~330 sword-fern clumps scattered across the forest floor, densest along the trail corridor
- 6 picnic tables (waterfront, esplanade, and trail) with collision
- Trail marker posts with white blazes at every bend of the switchback path
- Added a dedicated park-trail camera angle to the screenshot suite — the trail now reads like a real Hoyt Arboretum walk

**Gloom**
- Distant lightning: every ~15–40 s the sky and ambient flicker for a few frames, with a low thunder rumble 1–3 s later

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 6 — 2026-07-03
Baseline = pass 5. Verdict: **KEPT**.

**Game feel**
- First-person golf club (shaft, grip, chromed head) parented to the camera: idle sway at address, backswing tracks the power meter, and it releases through the ball on the third press with a follow-through

**People**
- Pedestrians got separate heads with six skin tones (instanced second mesh) — no more walking thumbs
- Three standing conversation clusters in Pioneer Courthouse Square facing each other

**Transit**
- Portland Streetcar: three-segment white-and-blue tram gliding the length of 5th Ave with door pauses at four stops, on freshly painted track lines

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 7 — 2026-07-03
Baseline = pass 6. Verdict: **KEPT** (smallest delta so far — diminishing returns noted).

**Street-level depth**
- Storefront awnings are now real protruding canopy slabs (one merged mesh across ~110 buildings) that catch light and cast shadows, instead of paint on the wall texture
- 18 bronze Benson Bubbler drinking fountains on downtown corners (Portland's four-bowl icon)

**Silhouette**
- Rooftop water towers (tank + conical cap + legs) on ~20 tall buildings, with collision so a rooftop lie can carom off them
- Steel Bridge lower deck gained handrails and K-brace struts

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 8 — 2026-07-03
Baseline = pass 7. Verdict: **KEPT** — biggest single-feature win since pass 2.

**Golden hour (third atmosphere)**
- Weather system refactored from a binary sunny↔gloom blend into a preset blender; T now cycles sunny → golden hour → gloom, and the start screen offers all three
- Dusk preset: sun low over the West Hills (elevation 0.14 — shadows stretch across whole blocks), burnt-orange horizon fading to indigo, warm fog, windows and lamps aglow, car headlights on, water gone dark with glints — and Mt. Hood catches pink alpenglow
- Weather hooks now receive semantic (rain, glow) parameters instead of a single blend factor, so every existing effect (umbrellas, mist, lightning, lamp pools, headlights, sparkles) keys off the right physical cause in all three modes

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean · all three atmospheres screenshot-verified.

## Pass 9 — 2026-07-03
Baseline = pass 8. Verdict: **KEPT** — completes the atmosphere set.

**Night (fourth atmosphere)**
- T now cycles sunny → golden hour → gloom → night; fourth card on the start screen
- Hash-based twinkling starfield in the sky shader (starK per preset — a few stars already peek through at dusk)
- Cool moonlight from the east, near-black sky with a faint city-glow horizon, every window lit, lamp pools on, headlights on, dark water with moon glints, subtle night vignette
- Cloud billboards now dim with sun intensity so they don't glow white after dark; sky-shader time uniform finally hooked up (clouds drift, stars twinkle)

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean · all four atmospheres screenshot-verified.

## Pass 10 — 2026-07-03
Baseline = pass 9. Verdict: **KEPT** (night-polish pass; solid but incremental).

**After-dark water**
- City-light reflections: additive streak overlays hugging both banks, brightness driven by the glow parameter (dusk/night/gloom), gently wobbling; mipmaps disabled so they survive grazing angles. Took three iterations to get right: plane orientation, then transparent render order vs. the depth-writing water, then brightness
- Sailboats and the barge got red/green nav lights and masthead lights after dark

**Sky**
- The sun disc/halo is now tinted per preset — silver moon at night, orange sun at dusk (was always warm white)

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 11 — 2026-07-03
Baseline = pass 10. Verdict: **KEPT** — the missing "game studio" ingredient.

**Post-processing bloom**
- EffectComposer + UnrealBloomPass + OutputPass (same CDN as three.js — still one file, no build step), on a 4×-multisampled half-float render target so MSAA survives
- Bloom strength is a weather parameter: 0.06 sunny → 0.45 golden hour → 0.3 gloom → 0.65 night. Every lit window, lamp orb, storefront, headlight, and the White Stag sign now halos after dark; night reads like a long-exposure photograph
- Artifact hunting from the comparisons: gulls switched from unlit white (they bloomed into glowing sky-dashes) to lit material; shader clouds now dim by starK so they read as moonlit instead of glowing; bloom threshold raised so the sunny sky doesn't haze the whole frame

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean · all four atmospheres re-verified.

## Pass 12 — 2026-07-03 (new direction: "feel like walking around Portland")
Baseline = pass 11. Verdict: **KEPT**.

**Street-level authenticity**
- Street-name blades on every downtown corner — 17 real names (SW Broadway, SW 5th Ave, W Burnside St, SW Salmon St, …), green-and-white, stacked and crossed like real sign poles, readable from both sides (two front-facing planes after the first version mirrored and the second version interleaved)
- Working traffic signals at 15 intersections: pole, mast arm, three-lamp head with emissive red/yellow/green cycling on a 12 s timer — synchronized citywide like actual downtown Portland, glowing at night via bloom
- Fire hydrants and park-green trash cans scattered on corners (with ball collision)
- Sidewalks gained expansion-joint scoring so pavement reads as poured panels underfoot

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 13 — 2026-07-03
Baseline = pass 12. Verdict: **KEPT**.

**Transit & bikes (walking-around-Portland pass 2)**
- Two TriMet-liveried buses (white/blue with orange stripe, window band, six wheels) driving W Burnside and SW Madison end-to-end — including over the bridges — with 4-second door pauses at five stops each
- Glass bus shelters (frame, roof, bench, transparent back panel) at all ten stops, with collision
- Bike racks (inverted-U staple racks) scattered on downtown sidewalks, ~70% holding a parked bike — full frame geometry with two wheels, fork, top/down tubes, seat and handlebars, in six frame colors, leaning slightly like real locked bikes

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 14 — 2026-07-03
Baseline = pass 13. Verdict: **KEPT**.

**Food-cart pod (SW 9th & Oak)**
- Requisitioned a downtown block as an asphalt lot with nine food carts in a U — each with its own color, striped awning, and a service window that glows after dark
- Four picnic tables in the middle, a wooden "Food Cart Pod" sign, and string lights strung pole-to-pole across the lot: catenary wires with ~80 individually glowing bulbs that come on at dusk (magical with bloom at golden hour)

**Old Town murals**
- Up to five painted murals on brick walls above the storefronts: a ROSE CITY rose on teal, Mt. Hood at sunset over a fir line, and a PDX-in-the-rain piece — placed on street-facing faces of taller Old Town buildings

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 15 — 2026-07-03
Baseline = pass 14. Verdict: **KEPT** — the icons pass.

**Portland landmarks**
- Powell's City of Books claims the block at W Burnside & 11th: full-block building with the red "POWELL'S CITY OF BOOKS" wall signs on both street faces (they glow after dark)
- Chinatown Gate spanning 3rd Ave at Burnside: red columns, three tiered green roofs with gold finials, CHINATOWN plaque — with collision, so yes, you can ricochet a drive off it
- "Keep Portland Weird" wall sign on the block across from the White Stag building

**Street color**
- Storefront canopies now carry per-building awning colors (burgundy, navy, forest, rust, charcoal) via vertex colors in the merged mesh, instead of one uniform green

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 16 — 2026-07-03
Baseline = pass 15. Verdict: **KEPT**.

**Walk cycle**
- Pedestrians no longer glide: bodies split into torso + two instanced legs with hip-pivot scissor animation synced to each walker's gait phase and speed, in five pants colors. The last big "video-game glide" tell at eye level is gone

**Micro-landmarks**
- Mill Ends Park: the world's smallest park, faithfully rendered as a 1-meter planter with lawn, shrub, and plaque in the middle of Naito Parkway
- The elk statue on its stone plinth holding a traffic lane on SW Salmon (bronze, antlers and all, with collision)

**Infrastructure note**: the OS cleaned the temp scratchpad between passes — rebuilt the playwright rig (verify.js, npm deps, HTTP server) from scratch; all 34 walking legs + swing test green on the rebuilt rig.

## Pass 17 — 2026-07-03
Baseline = pass 16. Verdict: **KEPT**.

**Trees (they're in every frame)**
- Deciduous canopies rebuilt from 2 to 4 offset flat-shaded lobes with a much wider hue range (yellow-greens through cedar-dark) and larger street-tree scale — kills the uniform-gumball look citywide
- Painted mulch tree pits under every deciduous tree, including the waterfront rows

**Streets**
- Parking stall stripes ticked along the curb lanes of every N-S street (except the streetcar street, which correctly has none)

**River corridor**
- Distant Fremont Bridge (white tied double-arch, north) and Marquam Bridge (gray double-deck box truss, south) silhouettes — the Willamette no longer just ends; every up- or down-river view now terminates in a real Portland bridge

**Sky**
- Sunny cumulus coverage bumped (cloudK 0.18 → 0.30) for a proper Oregon summer sky

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 18 — 2026-07-03
Baseline = pass 17. Verdict: **KEPT**.

**Streets (the Portland tell)**
- Green bike lanes with white dash markings painted on the Broadway/3rd couplet (full length, block by block) and the Oak St east-west crossing — the single most recognizable piece of Portland street paint
- Newspaper-box clusters (2–4 boxes in Oregonian orange, Willamette Week blue, Mercury red, and friends) at ~1 in 5 street corners, with collision

**Street life**
- Static "waiting riders" at TriMet shelters (55% of stops) facing the street, plus five regulars milling around the food-cart pod — bus stops no longer look abandoned
- Hanging flower baskets on every lamppost arm: dark planter pot + flat-shaded bloom ball in five flower colors (pink/red/fuchsia/orange/yellow), the downtown-Portland summer signature

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.

## Pass 19 — 2026-07-04
Baseline = pass 18. Verdict: **KEPT**.

**Grounding the world (eye-level realism)**
- Contact-shadow AO fringe painted under every building footprint (three nested translucent rects) — buildings no longer look pasted onto the sidewalk
- Dark gutter bands along both edges of every street — the sidewalk-to-asphalt transition now has a real curb seam instead of a hard flat line

**Overhead wires (the missing urban layer)**
- Creosote utility poles with crossarms and three sagging catenary-sampled wires down every east-side street — the industrial district finally has its signature clutter
- Streetcar catenary on 5th Ave: masts on both sidewalks, sagging cross-spans every 40 m, and a contact wire running above the tracks

**Verified after pass**: 0 console errors · 34/34 walking legs · 13/13 areas reachable · swing + tracer clean.
