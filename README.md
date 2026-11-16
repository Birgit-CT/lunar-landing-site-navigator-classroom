# Lunar Landing Site Navigator – v2

**Continued development after NASA Space Apps 2026.** The version submitted to the challenge is kept unchanged at https://birgit-ct.github.io/lunar-landing-site-navigator/ (source: https://github.com/birgit-ct/lunar-landing-site-navigator).

**Live app (v2):** https://birgit-ct.github.io/lunar-landing-site-navigator-v2/
**30-second demo (from the hackathon):** https://birgit-ct.github.io/lunar-landing-site-navigator/demo.mp4

Created by Birgit Cecilie Tarlebø at NASA Space Apps Challenge 2026 – Oslo.

> **Experimental prototype.** Built in one weekend for NASA Space Apps 2026. The sunlight and Earth-visibility calculations use NASA terrain data and were checked against NASA illumination maps, but the mission profiles, targets, scores and verdicts are illustrative examples that have not been validated by mission engineers. Use it to explore and understand trade-offs, not as a landing-site recommendation or safety assessment. Not an official NASA product.

Choosing where and when to land near the lunar south pole is a trade-off between sunlight for power, a direct line of sight to Earth for communication, and how long a mission must survive in darkness. Lunar Landing Site Navigator turns NASA terrain data into a guided, game-like experience. You choose a mission type, pick a site, scrub through time, see why a landing window works or fails, and pin the options to compare them side by side.

## How it works – five steps
1. **Explore** – choose a mission type. Each type sets its own targets for sunlight, Earth contact and longest darkness:
   - Solar rover: Sun ≥ 70 %, Earth ≥ 40 %, longest darkness ≤ 48 h
   - Science lander: 50 %, 50 %, 72 h
   - Comms outpost: 40 %, 80 %, 120 h
2. **Target** – pick a known site or click anywhere on the Moon.
3. **Timing** – each day in the calendar is scored as a 14-day mission. Scrub the time strip to watch the Sun and Earth rise and set over the real horizon.
4. **Evaluate** – see the mission score, the three target rings, a lander's-eye skyline view, and countdowns to sunset and Earthset.
5. **Pin & compare** – save missions as pins and compare them side by side.

Score = 35 % sunlight + 35 % Earth visibility + 30 % survival (longest darkness). The targets are example values, not NASA requirements.

## Method
- For each site, a 360° skyline is traced through the LOLA elevation data out to 300 km, including lunar curvature, with the eye 2 m above the ground.
- The Sun or Earth counts as visible when the centre of its disc is above that skyline. Positions are sampled hourly with Astronomy Engine and the IAU lunar orientation model.
- The surface south of 60°S is shaded in real time from the same elevation data: surface normals plus cast shadows toward the Sun at the time shown.
- The rest of the globe uses NASA's LRO colour map, lit in real time with slopes from NASA's global LOLA elevation map, so craters catch the light as the Sun moves.
- **Validation:** results were checked against NASA GSFC PGDA average-visibility maps (Mazarico et al. 2011) at 80 random points between 85° and 90°S.
  - Sunlight: r = 0.988, mean difference 1.7 percentage points.
  - Earth visibility: r = 0.981, mean difference 4.1 points.
- **Limitations:** terrain features smaller than the grid are smoothed out. Sites north of 60°S use a flat horizon. This is a planning-level view, not a landing-safety assessment.

## Data sources
- **Terrain 84–90°S:** NASA GSFC PGDA, LOLA `LDEM_80S_80MPP_ADJ` (Barker et al. 2023, *Planet. Sci. J.* 4:183), averaged to 240 m/px. https://pgda.gsfc.nasa.gov/products/90
- **Terrain 60–84°S and global relief:** NASA SVS CGI Moon Kit, LOLA `ldem_16` (16 px/degree). https://svs.gsfc.nasa.gov/4720
- **Moon surface colour:** NASA SVS CGI Moon Kit, LRO Wide Angle Camera colour map (`lroc_color_16bit_srgb_4k.tif`, 2025 edition), reduced to 2048 × 1024. https://svs.gsfc.nasa.gov/4720
- **Validation:** NASA GSFC PGDA `AVGVISIB_85S_060M_201608` (Mazarico et al. 2011, *Icarus* 211:1066). https://pgda.gsfc.nasa.gov/products/69
- **Sun, Earth and planet positions:** Astronomy Engine 2.1.19 (MIT licence).
- **Stars and Milky Way:** about 41,000 stars to magnitude 8 from the ESA Hipparcos catalogue, plus Milky Way outlines, via d3-celestial by Olaf Frohn (BSD-3-Clause). https://github.com/ofrohn/d3-celestial
- **Site coordinates:** approximate published landing coordinates and rounded reference points.

## Use of AI
- **Code:** the application's code was written with AI assistance (Claude by Anthropic), directed, tested and reviewed by the author.
- **Music:** the background music is generated live in the browser by code (Web Audio API). No audio files are used.
- **Demo video:** the screen footage is a real capture of the app, recorded and edited with AI-assisted scripts. The voice-over is recorded by the author (Birgit Cecilie Tarlebø) and cleaned up with standard audio processing. The video carries a visible "AI-assisted production" watermark and the same disclosure in its file metadata.

## Files
- `index.html` – the whole app, with terrain, star data and NASA Moon maps embedded.
- `vendor/` – three.js r128 and Astronomy Engine 2.1.19, with their licence files and the d3-celestial licence.
- `demo.mp4` – the 30-second demo, also playable from the Demo button in the app.
- `demo.srt` – English subtitles for the demo.

## Run locally
Run `python3 -m http.server` in this folder, then open http://localhost:8000. Pins are saved in your browser.

## Licences
- three.js and Astronomy Engine: MIT. d3-celestial data: BSD-3-Clause. The licence files are in `vendor/`.
- NASA data are public domain; please cite the references above.

## Changes since Space Apps 2026
| Date | Change |
|---|---|
| 2026-11-16 | v2 created as a copy of the submitted version, for further development. |
