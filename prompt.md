#Prompt
"Snowman Skater" HTML5 Game

Act as a world-class Principal HTML5 Game Developer, Senior Game Designer, Lead UI/UX Architect, Animation Engineer, and Quality Assurance Director. Build a complete, highly polished, commercial-grade 3D-perspective browser arcade game from scratch named "SNOWMAN SKATER" as a 100% self-contained, single-file HTML document (snowman_skater.html).

There is NO existing project, NO starter files, and NO external assets. Everything — graphics, animations, particle systems, audio synthesis, UI, state machine, and data management — must be hand-coded in vanilla HTML5 Canvas, CSS3, and JavaScript. No placeholders, no pseudocode, no TODOs, no omitted sections, no external libraries unless auto-loaded via CDN. It must run immediately when opened in any modern browser.

1. Core Vision
3-lane forward-facing third-person arcade runner, camera positioned slightly behind a fully animated cartoon snowman.
True perspective projection: the road is narrow at a vanishing point near the horizon and widens toward the bottom of the screen — never flat or top-down.
Forward momentum sells itself through two channels:
World movement — obstacles, collectibles, lane markings, and scenery spawn at the horizon, scale up via depth (
𝑍
Z) calculations, and stream toward the camera.
Character animation — the snowman continuously performs an articulated skating loop: alternating leg strokes, arm swings, body bob, flowing scarf, lean into turns, and particle dust trails.
Exactly 30 distinct, handcrafted levels with progressive difficulty, unique visual themes/palettes, and finish-line conditions.
Pacing: the game should feel fast and propulsive from level 1 — base speed, max speed, and acceleration should all scale up meaningfully across the campaign so later levels feel noticeably more intense than a gentle jog.
2. Technical Architecture
Single self-contained file; double-clicking it runs the game instantly.
requestAnimationFrame loop with delta-time (
𝑑
𝑡
dt) for frame-rate independence.
Device pixel ratio (DPR) scaling for crisp high-DPI rendering.
Explicit finite state machine (FSM): MENU, LEVEL_SELECT, PLAYING, PAUSED, LEVEL_COMPLETE, GAME_OVER, SETTINGS, HOW_TO_PLAY — mutually exclusive, zero overlapping DOM/canvas glitches or duplicate loops.
Audio entirely via the Web Audio API (synthesized SFX for jumps, collisions, coins, power-ups, menu clicks, level completion) with a full mute toggle.
localStorage persistence: currency, unlocked levels, best scores, and star ratings per level.
3. Game Systems

Perspective & Camera

Projection: screenX = vanishingPointX + worldX·(scaleFactor / depthZ), screenY = horizonY + depthCurve(Z).
Subtle procedural bobbing while skating, lateral banking on lane changes, landing impacts, collision shakes, and speed-boost streaks.
A "Reduced Motion" toggle disables heavy shakes/tilts.
Screen-bounds constraint: calibrate the perspective spread so that the outer lanes, projected at the player's depth, stay comfortably within the canvas width (roughly the middle 60–80% of screen width, not edge-to-edge). Verify this numerically — plug the player's Z-depth into the projection formula and confirm the outer-lane X coordinate is well inside [0, canvasWidth] before finalizing the spread constant. Lane-divider lines should be drawn between lane centers (e.g. at the midpoints), not on top of the outer lane centers themselves.

Player Character

Anatomy: 3 stacked snowballs, carrot nose, coal eyes, winter top hat, flowing scarf, mittens, ice skates.
States: skating loop (rhythmic limb cycling + shadow), smoothly interpolated lane switch with lean (no snapping), jump (parabolic physics: acceleration → apex → gravity → cushioned landing bounce + snow puff), slide (lowered collision box), and collision reactions (flinch, invulnerability blink, speed-trail flares, distinct look per active power-up).

Input (Desktop & Mobile)

Desktop: A/← left lane, D/→ right lane, W/↑/Space jump, S/↓ slide, E activate stored power-up, P/Esc pause.
Mobile: swipe gestures (left/right/up/down) plus thumb-friendly on-screen buttons for the same actions.

Obstacles, Collectibles & Power-Ups

Obstacles: snow piles, ice patches, rocks, fallen branches, barriers, sleds, moving trains, roaming penguins — each solvable via jump, slide, or lane dodge, scaling from horizon to foreground.
Collectibles: snowflakes (score), coins (currency), stars (bonus score & multiplier up to x5), all depth-scaled.
Power-ups are inventory-based: collecting one fills a single dedicated HUD slot rather than auto-triggering; the player deploys it manually with E or the on-screen button. Types: Snow Shield (absorbs one hit), Speed Boost (temporary acceleration + streak VFX), Snowflake Magnet (pulls nearby collectibles in), Time Freeze (slows incoming obstacles/world).

30-Level Campaign

Handcrafted parameters per level for speed, obstacle density, hazard mix, and target finish distance (e.g., Level 1 Snowy Village → Level 30 Snowman Kingdom), each with a distinct name and color theme.
Speed, max speed, and acceleration should increase substantially level-to-level so the campaign has a real difficulty and intensity curve, not a flat pace.
Level completion: reaching the target distance triggers a finish banner, gameplay freezes gracefully, then a tally screen shows score breakdown, star rating (1–3 stars), coins earned, and unlock updates.

UI/UX

Winter-themed glassmorphism (backdrop-filter, soft glows, rounded panels, clean typography).
Screens: Main Menu, Level Select grid (stars/locks), Settings (Audio, Shake, Reduced Motion), How to Play, Pause overlay, Level Complete, Game Over.
HUD: score, coins, distance progress bar, lives, active multiplier, power-up inventory slot.
Debug overlay (F3 toggle): FPS, active level, distance/depth, object counts, current speed, and state-machine status.
4. QA & Deliverables

After generating the code, self-audit for:

Boot reliability and layout responsiveness across desktop and mobile aspect ratios (portrait and landscape).
Flawless state-machine transitions — no overlapping screens, frozen loops, or stuck touch inputs.
Mathematical correctness of the perspective road lines and object depth-scaling.
Smooth input responsiveness — interpolated lane changes, accurate jump arcs, fluid sliding.
Correct power-up inventory management and robust localStorage persistence.

Return:

The full, complete, production-ready snowman_skater.html code block (no truncation, no summarizing).
A detailed feature checklist.
A concise QA verification report confirming all test parameters pass.


#AI Tool used
claude sonnet 5 medium
