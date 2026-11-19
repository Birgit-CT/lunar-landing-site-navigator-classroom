# Lunar Landing Site Navigator – Classroom Edition

**Live app:** https://birgit-ct.github.io/lunar-landing-site-navigator-classroom/

Created by Birgit Cecilie Tarlebø. First built at NASA Space Apps Challenge 2026 – Oslo, and developed further as a learning tool. The version submitted to the challenge is kept unchanged at https://birgit-ct.github.io/lunar-landing-site-navigator/.

> **A learning prototype.** The sunlight and Earth-visibility calculations use real NASA terrain data and were checked against NASA illumination maps. The mission profiles, targets and scores are simplified examples for learning, not validated engineering values or NASA requirements. Not an official NASA product.

## Why it matters
At the Moon's south pole, sunlight and contact with Earth come and go with every hill and every day. In March 2025 the Athena lander tipped over in a crater where sunlight could not reach its solar panels, and its mission ended after about 13 hours ([SpacePolicyOnline](https://spacepolicyonline.com/news/im-2-mission-ends-one-day-after-lunar-landing/)). In 2023, India's Chandrayaan-3 lander and rover did not wake up after their first lunar night ([Live Science](https://www.livescience.com/space/space-exploration/indias-chandrayaan-3-moon-lander-fails-to-answer-wake-up-call-may-be-dead-for-good)).

With the Artemis programme heading for the lunar south pole, many students will ask: why land there, and why is it so hard?

## Who it is for
Students aged about 13–19 and their teachers, in science, physics, geography and technology, plus science centres and anyone curious about the Moon.

## What changes for them
Understanding why a landing site works normally means reading illumination maps, horizon plots and astronomy tables. Here, students plan a mission in about two minutes:
- they pick a site,
- move through two weeks of time,
- and watch the Sun and Earth rise and set over the real terrain.

Every step has a **Learn** box with one short fact and one question to talk about. A **For teachers** button opens learning goals, a ready-made 40-minute lesson plan and 17 **background slides** (the Athena story, the landing sites, the three mission types, the lunar day and LOLA, each fact with its source). The slides are shown inside the app, with teacher notes and full-screen mode, and are not offered as a separate download, so they stay together with the app and its context.

## Why it can be trusted
- The terrain is NASA's Lunar Orbiter Laser Altimeter (LOLA) elevation data.
- For each site, a 360° skyline is traced out to 300 km, including the Moon's curvature.
- At 80 test points near the pole, the results match NASA's own average illumination maps:
  - Sunlight: r = 0.988, mean difference 1.7 percentage points.
  - Earth visibility: r = 0.981, mean difference 4.1 points.

## How it works – five steps
1. **Explore:** choose a mission type. Each type sets example targets for sunlight, contact with Earth and the longest stretch of darkness:
   - Solar rover: Sun ≥ 70 %, Earth ≥ 40 %, darkness ≤ 48 h
   - Science lander: 50 %, 50 %, 72 h
   - Comms outpost: 40 %, 80 %, 120 h
2. **Target:** pick a known site, or click anywhere on the Moon.
3. **Timing:** every day in the calendar is scored as a 14-day stay. Scrub through time to watch light and shadow move.
4. **Evaluate:** see the score, the three target rings, a lander's-eye view of the skyline, and how long until sunset and Earthset. Targets can be changed with − and +.
5. **Pin & compare:** save missions and compare them side by side.

Score = 35 % sunlight + 35 % Earth visibility + 30 % survival through darkness.

## Next steps
- Test it with classes and a science centre, and use the feedback to improve it.
- Translations, starting with Norwegian.
- A "bring your own requirements" mode, so students, or engineers, can enter a lander's real battery and power figures.
- A lighter mode for phones and older tablets.

Tried it in class? Share what worked and what did not under **Issues** in this repository.

## Data sources
- **Terrain 84–90°S:** NASA GSFC PGDA, LOLA `LDEM_80S_80MPP_ADJ` (Barker et al. 2023, *Planet. Sci. J.* 4:183), averaged to 240 m/px. https://pgda.gsfc.nasa.gov/products/90
- **Terrain 60–84°S, global relief and Moon colour:** NASA SVS CGI Moon Kit: LOLA `ldem_16` and the LRO Wide Angle Camera colour map (2025 edition). https://svs.gsfc.nasa.gov/4720
- **Validation:** NASA GSFC PGDA average-visibility maps `AVGVISIB_85S_060M_201608` (Mazarico et al. 2011, *Icarus* 211:1066). https://pgda.gsfc.nasa.gov/products/69
- **Site references:** NASA Artemis III candidate landing regions and approximate published landing coordinates.
- **Sun, Earth and planet positions:** Astronomy Engine 2.1.19 (MIT licence).
- **Stars and Milky Way:** ESA Hipparcos catalogue, via d3-celestial by Olaf Frohn (BSD-3-Clause).

## Use of AI
- **Code:** written with AI assistance (Claude by Anthropic), directed, tested and reviewed by the author.
- **Music:** the background music is generated live in the browser by code.
- **Demo video:** a real screen capture of the app, assembled with AI-assisted scripts. The voice-over is recorded by the author.

## Files
- `index.html`: the whole app, with terrain, star data and NASA Moon maps embedded.
- `vendor/`: three.js r128 and Astronomy Engine 2.1.19, with their licence files and the d3-celestial licence.
- `demo.mp4` and `demo.srt`: the 30-second demo from the hackathon, with English subtitles.

## Run locally
Run `python3 -m http.server` in this folder and open http://localhost:8000.

## Licences
- **This project:** Apache License 2.0.
- **Libraries and data:** three.js and Astronomy Engine are MIT, d3-celestial data is BSD-3-Clause, and fonts are from Google Fonts (SIL Open Font License). NASA data are public domain; please cite the references above.

## Changes since Space Apps 2026
| Date | Change |
|---|---|
| 2026-11-19 | Background slides with sources and teacher notes, shown inside the For teachers guide. |
| 2026-11-16 | Classroom Edition: "Why it matters" story, Learn boxes with a fact and a question on every step, a For teachers guide with a 40-minute lesson plan, and clearer learning-prototype notices. |
