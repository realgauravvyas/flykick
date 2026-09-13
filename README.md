# ⚽ FLYKICK — Connectome Football

**Live demo: https://realgauravvyas.github.io/flykick/** — no server, no setup, no dependencies.

**Two teams of neural-circuit flies play football. Possess any fly — either team, any time — and take over the match yourself.**

![Match in play](assets/demo-match.png)

Every player on the pitch is a fruit fly driven by a miniature connectome circuit — compound eyes → optic lobe → central complex → wing and leg motors — and you can click into any of their brains mid-match. Watch the AI flies play, then seize a forward on a counter-attack, or switch sides and defend against yourself.

> The fourth fly-connectome experiment in the series: **AFTERWING** wanders, **FlyGambit** thinks, **FLYMIND** feels — **FLYKICK competes.**

## 🎮 How to play

| Control | Action |
|---|---|
| **Click any fly** | Possess it — either team, any time |
| **WASD / Arrows** | Drive your fly |
| **Space (hold)** | Charge a kick — release to shoot (hold Space near the ball to trap/dribble) |
| **Q** | Release possession back to its brain |

The other nine flies keep playing by their own circuits: the closest chases the ball, the second supports, the rest hold formation lanes, and the goalkeepers dive on incoming shots.

![Possession](assets/demo-possess.png)

## 🧠 The brain inside each boot

The **Brain Cam** panel (side of the screen) streams the possessed fly's circuit live:

- **R1–R6 photoreceptors** fire when the fly sees the ball
- **T4/T5 + HS** (optic lobe) track motion
- **Central complex** commands steering — when you possess a fly, you literally hijack this node
- **Kenyon cells** flash as the fly "remembers" the play
- **Wing motor neurons** spike with every sprint; **leg motor (TTM)** with every kick

The circuit follows real Drosophila anatomy names from the published connectomes ([male CNS](https://male-cns.janelia.org/), [FlyWire](https://flywire.ai)) — distilled to 11 neurons per fly for playability (see the honest scale note below).

![Goal](assets/demo-goal.png)

## ⚔️ Match format

- 2 teams × 5 flies (GK / 2 DF / MF / FW), 2-minute matches
- Kickoffs, goal celebrations with light beams and screen shake, full-time + rematch
- Procedural audio: crowd murmur that swells with action, kick thumps, referee whistle, goal fanfare, wing buzz on possession — all synthesized, zero audio files
- Scoreboard, match log, and live brain telemetry

## 🚀 Run it

No build. No dependencies. Static files.

```bash
npm start        # → http://localhost:8123
# or: npx serve . / python -m http.server
```

## 🧪 Tested before shipping

```bash
node tools/test-engine.js      # 13/13: AI plays & scores, possession override, charge-kick, clock, goals both ends
node tools/play-audit.cjs      # 17/17 browser audit: boot, pixels, click-possess, WASD, kick, team-switch, brain cam, full-time, rematch — 0 console errors
```

Verified AI matches end competitive (13:17, 12:12, 14:11, 11:13 across test runs) — the teams are symmetric by construction and results are genuinely open.

## Visual identity — the fourth fly

| Project | The fly | The idea |
|---|---|---|
| [AFTERWING](https://github.com/realgauravvyas/afterwing) | jewel-toned wanderer | sever a connection, watch twins diverge |
| [FlyGambit](https://github.com/realgauravvyas/fly-gambit) | specimen under a fluorescence microscope | a fly brain learns chess, with lesions |
| [FLYMIND](https://github.com/realgauravvyas/flymind) | neon holo-wireframe under a lab scanner | poke senses, watch real circuits fire |
| **FLYKICK** (this) | **broadcast-neon athletes** | team play, possession, competition |

## 📁 Files

```
flykick/
├── index.html          app shell + overlays + brain cam panel
├── css/style.css       broadcast-neon theme
├── js/
│   ├── brain.js        per-fly 11-neuron circuit (anatomy-named)
│   ├── engine.js       match sim: roles, physics, possession, rules
│   ├── render.js       pitch, holo flies, ball, beams, shake
│   ├── input.js        WASD + click-to-possess
│   ├── audio.js        procedural crowd/whistle/kicks/fanfare
│   └── main.js         loop, HUD, brain cam, toasts
└── tools/              headless engine test + browser play audit
```

## Credits & inspired by

- Inspired by [*A connectomics milestone: mapping the complete male fruit fly brain*][blog] (Google Research × HHMI Janelia) and the [FlyWire female connectome][flywire].
- Companion labs: [FLYMIND](https://github.com/realgauravvyas/flymind) · [AFTERWING](https://github.com/realgauravvyas/afterwing) · [FlyGambit](https://github.com/realgauravvyas/fly-gambit)
- Everything is procedural — flies, pitch, and sound. Zero assets, zero dependencies, zero build.
- Honest scale: real connectomes have ~140,000 neurons per fly; FLYKICK models 11 per player. The anatomy names and signal flow are the homage, not the scale.

[blog]: https://research.google/blog/a-connectomics-milestone-mapping-the-complete-male-fruit-fly-brain/
[flywire]: https://flywire.ai

## License

MIT — see [LICENSE](LICENSE).
