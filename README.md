# Duck Pond — v1.2-dev.9

## v1.0.3 – Smart TV stability

- Uses classic transform-based pond positioning on detected TV browsers to reduce jitter.
- Keeps swimming prestige stars aligned to the 512×512 duck canvas on legacy TV engines.
- Disables Gangnam and duck fights on TV browsers because older Web Animations implementations can abort those sequences mid-event.
- Modern phone/desktop browsers retain all existing interactions and performance paths.


Duck Pond is the Taipans Cricket Club weekly duck animation. Player and duck data are loaded from CSV files and rendered as an interactive pond for desktop and mobile browsers.

## Production files

- `index.html` — application shell and cache-busted references
- `src/app.js` — pond behaviour, player/week logic and events
- `src/styles.css` — layout, animation and responsive styling
- `data/players.csv` — player presentation data
- `data/ducks.csv` — weekly duck events
- `assets/` — production artwork and sound
- `docs/` — design decisions, backlog, roadmap and release/security notes

## Data format

`data/players.csv`

```text
playerId,name,nickname,presentation,featherTone,build,president,captain,coach,hair,headwear,swimAccessory
```

`data/ducks.csv`

```text
date,playerId,team,duckType
```

Supported `duckType` values are `standard`, `golden` and `diamond`. Dates may be supplied as `D/M/YYYY`, `DD/MM/YYYY` or `YYYY-MM-DD`.

## Club-week behaviour

The season is anchored to **28 Sep–4 Oct 2026**. Empty/washout weeks remain selectable. When duck data exists, the latest populated club week is selected by default.

## Hosting

The production build is suitable for static hosting on GitHub Pages. Treat everything committed to a public production repository, including CSV data and assets, as publicly accessible.

## v1.0.0 release

v1.0.0 is the production launch build promoted directly from the tested v0.183 release candidate. It includes the completed pre-release cleanup plus mobile portrait pond-scroll hints and the Facebook/Instagram in-app-browser landscape notice. No functional pond changes were made during the v1.0.0 promotion.


## v1.0.1 compatibility release

- Transpiles modern JavaScript syntax for older smart-TV browser engines.
- Adds small DOM/JavaScript compatibility fallbacks required by older browsers.
- Detects common smart-TV browsers and automatically enters a TV display mode after the selected week loads.
- TV mode hides normal page chrome and leaves a remote-friendly **Change week** control to return to the selector.
- The default remains the latest populated club week.
- No duck, animation, asset, CSV or scoring behaviour changed from v1.0.0.

## Release notes

v1.0.4 improves TV startup/display behaviour. Detected TV browsers enter full-pond display mode immediately, show the loading pond overlay while production data/assets are prepared, then begin the newest-week entry sequence without waiting for all ducks to finish entering. The non-working TV Change Week control has been removed. Modern phone/desktop behaviour is unchanged.


## v1.0.6

- Rebuilt directly from known-good v1.0.4.
- Added Hisense / VIDAA / Odin detection only for TV display mode.
- Hisense enters full-pond TV display mode immediately at startup.
- Existing v1.0.4 rendering and legacy-TV compatibility logic is unchanged.
- No CSS, assets or CSV data changed.


## v1.0.7

- Added deterministic TV display mode via `?tv=1`.
- A forced TV display choice is remembered in local storage for future visits on that browser.
- `?tv=0` clears the remembered TV display choice and disables TV display mode for that load.
- Existing v1.0.6 rendering and legacy-TV compatibility logic is unchanged.
- No CSS, assets, or CSV data changed.


## v1.2-dev.1 — Lincoln bowling game prototype

DEV ONLY. Adds the first playable Lincoln bowling Easter egg: “Bowler’s name?” trigger, in-pond bowler selection, field-setting choreography, flick-to-bowl ball control, Lincoln sixes/scoreboard taunts, scoreboard sandpaper rubbing mechanic, scuffed inswing dismissal, Lincoln walk-off and normal pier re-entry. Cricket graphics are intentionally temporary CSS artwork for gameplay testing. Production is unchanged.


## v1.2-dev.2

- Fixes the cricket trigger being nested inside a mobile-only toolbar and therefore hidden on desktop.
- Moves “Bowler’s name?” into the main production toolbar so it is visible on desktop and mobile, but remains hidden in TV display mode.
- Corrects CSS and JS cache-buster references to the current dev build.

## v1.2-dev.3

- Reoriented cricket pitch to run away from the viewer.
- Bowling is now an upward flick-to-release gesture; the delivery path runs automatically.
- Disabled normal click-scoot and collision reactions while cricket is active.
- Kept the cricket ball visible through delivery and six animations and hardened reset behaviour.
- Increased ball size.
- Added random six trajectories around the ground.
- Pushed fielders toward the pond edges and made them face Lincoln once set.
- Moved “Bowler’s name?” above the scoreboard and only reveals it after all weekly entrants have finished.
- Enlarged scoreboard taunts; only some taunts mention sandpaper.
- Improved temporary bat proportions for the prototype.

## v1.2-dev.4

- Corrected Lincoln's dismissal exit.
- Lincoln now swims toward the pavilion bank, gets visually smaller as he moves away,
  transitions to walking near the steps, walks up toward the pavilion door, and disappears through it.
- Removed the reverse-pier/moonwalk exit from the cricket game.

## v1.2-dev.5

- Fixed the cricket trigger disappearing after devices had previously opened `?tv=1`.
- Forced TV mode is now tied to the current URL/device only and is no longer persisted in localStorage.
- The normal dev URL therefore returns to normal interactive mode automatically.
- Added a defensive post-load reveal for the “Bowler’s name?” trigger after the pond entry sequence completes.

## v1.2-dev.6

- Corrects the live DEV mismatch where `index.html` and `app.js` were on dev.5 but `styles.css` was still the dev.2 cricket layout.
- Includes `src/styles.css` in the changed-files package.
- Removes runtime hidden/unhidden logic from “Bowler’s name?”.
- The trigger is visible in the pond by default, hidden only while cricket is running, and remains hidden in TV display mode.

## v1.2-dev.7

- Enlarges the cricket ball's invisible mobile touch target while keeping the visible ball close to its current size.
- Stops ball pointer gestures from bubbling into pond scrolling/selection.
- Slightly enlarges the cricket ball interaction target again in mobile landscape.
- Moves Lincoln forward of the stumps and forces Lincoln/bowler above pitch/stump layers.
- Smooths six trajectories with more path points and curved interpolation.
- Slows the post-hit flight slightly for a cleaner read.
- Removes Lincoln's water-to-land size jump by matching the first walk scale to the final swim scale.
- Changes Lincoln's exit path so he settles onto the stairs first, then walks upward toward the pavilion doors while getting smaller.

## v1.2-dev.8

- Replaces flick-to-bowl with pull-back-and-release.
- The ball now follows the pointer/finger whenever held, making the same drag interaction usable for the sandpaper clue.
- A pull toward the viewer of sufficient distance releases a fixed delivery; the pull distance does not yet change pace.
- Moves the ready ball farther up-pitch so it no longer sits underneath the bowler.
- Forces Lincoln into a consistent right-handed batting orientation rather than inheriting his previous pond-facing direction.
- Updates the scoreboard instruction to “PULL BACK & RELEASE”.

## v1.2-dev.9

- Moves the ready ball farther up-pitch so it sits clearly in front of the bowler.
- Makes the bowler's front wing track the dragged ball.
- Corrects Lincoln's exit target to the top waterline at the foot of the pavilion steps.
- Starts Lincoln's walking asset at ~0.45 scale to match the pond perspective at that waterline and remove the size jump.
- Keeps Lincoln on the lower steps first, then walks him upward while shrinking toward the pavilion.
- Uses the actual Gangnam stage/door cavity so the pavilion door visibly opens as Lincoln approaches.
- Fades the pitch once Lincoln is roughly halfway between the wicket and the water's edge.
- Rebuilds the temporary cricket bat as a separate visible handle and blade so the handle remains present while batting and walking.
