# Motion Graphics Skill Pack

12 skills that make launch-grade motion graphics with Claude Code. Every frame is code. No After Effects, no video generator.

Built by [Charlie Hills](https://charliehills.substack.com). Subscribe to the [MarTech AI newsletter](https://charliehills.substack.com) for weekly breakdowns of how I use these in practice.

**Contributions welcome.** Found a way to improve a skill? [Open a PR](https://github.com/charlie947/motion-graphics-skills/pulls). Run into a problem? [Open an issue](https://github.com/charlie947/motion-graphics-skills/issues).

## Start here: one line, 60 seconds

Before any skill, paste this into Claude Code on Opus 5.5:

```
Make a dynamic 15-second motion graphics video that shows what an incredible motion designer you are. Go all out.
```

It writes the animation as code, draws every frame and renders an MP4. Then change it by describing the edit:

- "Slow down the second scene."
- "Swap the text for mine: [your words]."
- "Use my brand colours: [hex codes]."
- "Make it 1080 x 1350 for LinkedIn."

When you want a specific job done properly, pick a skill below.

## What are Skills?

Skills are markdown files that give Claude a tested workflow for one job. Install them and Claude recognises when you're making a launch video, a chart or a reel, then asks for the right inputs, follows the rules that came out of real rejected drafts and checks its own frames before it shows you anything.

## How Skills Work Together

Run `brand-intake` once. It writes `brand.md` (who you are, what you sell, your assets) and `MOTION.md` (your colours, type, timing and motion rules), and adds a rule to CLAUDE.md so Claude reads both before it animates anything. Every other skill reads those two files first. Without them, a skill asks for your hex codes, font and logo, and never calls its result on-brand.

```
                         ┌──────────────────────────────────────────┐
                         │               brand-intake               │
                         │           brand.md + MOTION.md           │
                         │       (read by every skill below)        │
                         └─────────────────────┬────────────────────┘
                                               │
       ┌───────────────┬───────────────┬───────┴───────┬───────────────┬───────────────┐
       ▼               ▼               ▼               ▼               ▼               ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ Plan        │ │ Launch      │ │ Explain     │ │ Open        │ │ Compare     │ │ Promote     │
├─────────────┤ ├─────────────┤ ├─────────────┤ ├─────────────┤ ├─────────────┤ ├─────────────┤
│ motion-     │ │ launch-video│ │ vox-        │ │ title-      │ │ model-      │ │ newsletter- │
│ brief-writer│ │ apple-      │ │ explainer   │ │ sequence-3d │ │ showdown    │ │ promo       │
│             │ │ launch-film │ │ animated-   │ │             │ │             │ │ loop-cover  │
│             │ │             │ │ chart       │ │             │ │             │ │ reel-export │
│             │ │             │ │ milestone-  │ │             │ │             │ │             │
│             │ │             │ │ reveal      │ │             │ │             │ │             │
└─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘
```

See each skill's `SKILL.md` for its trigger phrases, the inputs it asks for and what it learned the hard way.

## Available Skills

| Skill | What it does |
|---|---|
| [brand-intake](skills/brand-intake/) | Interview plus 3 to 5 reference frames becomes `brand.md`, `MOTION.md` and the CLAUDE.md read-first rule. The foundation every other skill reads. |
| [motion-brief-writer](skills/motion-brief-writer/) | Turn a rough idea into a precise build brief in your brand. |
| [launch-video](skills/launch-video/) | Launch a product, offer or cohort in 30-45 seconds. |
| [apple-launch-film](skills/apple-launch-film/) | Rebuild an Apple-style Mac launch (menu bar, notch, widgets, wallpapers) entirely in code. |
| [vox-explainer](skills/vox-explainer/) | Explain a "why" question people half understand, documentary style. |
| [animated-chart](skills/animated-chart/) | Show a result, a stat or a trend as a looping chart. |
| [milestone-reveal](skills/milestone-reveal/) | A night sky of points that pulls into your real, sourced number. |
| [title-sequence-3d](skills/title-sequence-3d/) | Stop the scroll in the first 3 seconds with a cinematic 3D opener. |
| [model-showdown](skills/model-showdown/) | Same brief to three AI models, first try each, stacked into one comparison video. |
| [newsletter-promo](skills/newsletter-promo/) | Get people to read your newsletter with a 15-second promo. |
| [loop-cover](skills/loop-cover/) | Turn a cover into a seamless looping GIF where only one element moves. |
| [reel-export](skills/reel-export/) | Turn any video into a clean 1080 x 1920 Reel or TikTok with safe-zone text. |

## Installation

### Claude Code

Download this repo (green **Code** button, then **Download ZIP**) and unzip it, or clone it:

```bash
git clone https://github.com/charlie947/motion-graphics-skills.git
```

Copy the 12 folders inside `skills/` into `~/.claude/skills/` (every project) or your project's `.claude/skills/` (one project). This loop keeps any skill folder you already have:

```bash
mkdir -p ~/.claude/skills
for skill in motion-graphics-skills/skills/*; do
  [ -f "$skill/SKILL.md" ] || continue
  destination="$HOME/.claude/skills/$(basename "$skill")"
  if [ -e "$destination" ]; then
    printf 'Preserved existing skill: %s\n' "$destination"
  else
    cp -R "$skill" "$destination"
  fi
done
```

Open Claude Code and pick Opus 5.5 with `/model`.

### Claude Desktop

Zip one skill folder and upload it in Customise, then Skills. From `motion-graphics-skills/skills`:

```bash
zip -r brand-intake.skill brand-intake
```

Start with `brand-intake`, then add the skills you need.

### Codex

From your project's root, after cloning this repo into it:

```bash
test -d motion-graphics-skills/skills || { printf 'Missing source skills folder\n'; exit 1; }
mkdir -p .agents/skills || exit 1
for skill in motion-graphics-skills/skills/*; do
  [ -f "$skill/SKILL.md" ] || continue
  name="$(basename "$skill")"
  destination=".agents/skills/$name"
  if [ -e "$destination" ] || [ -L "$destination" ]; then
    printf 'Preserved existing skill: %s\n' "$destination"
  else
    cp -R "$skill" "$destination" || exit 1
  fi
done
```

Open a fresh Codex task and check the skills load from `.agents/skills/<name>/SKILL.md`.

### Export to MP4

Add HyperFrames once (free, open source): `npx skills add heygen-com/hyperframes`. No export tools at all? [My export kit (Mac and Windows)](https://drive.google.com/file/d/18ugNPOOHqLTbkekSYPzvC1wJStMjWg8y/view?usp=drivesdk) turns any of these HTML files into an MP4.

## Usage

Run `brand-intake` first, then say what you want. The right skill loads itself:

```
"Set up my brand" → brand-intake
"Brief this animation" → motion-brief-writer
"Make a launch video for my coaching programme" → launch-video
"Make an Apple-style launch for my app" → apple-launch-film
"Why does every logo look the same now?" → vox-explainer
"Animate my Q3 chart" → animated-chart
"Celebrate 10,000 subscribers" → milestone-reveal
"Give me a cinematic opener" → title-sequence-3d
"Same prompt, three AIs" → model-showdown
"Promo for this edition" → newsletter-promo
"Make my cover move" → loop-cover
"Make this a reel" → reel-export
```

### The brief behind my "Why do we dream?" film

One line gets you close. A proper brief gets you something people share. This is exactly what I typed (with `vox-explainer` installed):

```
Why do we dream? And then someone suddenly wakes up, zooms out of the eye, and goes into outer space. There are neural networks of interconnectivity to convey the brain.
```

It found a source for every fact before it drew anything, wrote the script, added a voice and rendered it. Then give it notes like you would a designer.

## Skill Categories

### Foundation
- `brand-intake`: interview plus reference frames, writes brand.md and MOTION.md

### Plan
- `motion-brief-writer`: rough idea to build brief

### Launch
- `launch-video`: product, offer or cohort launch
- `apple-launch-film`: Mac interface launch, all in code

### Explain
- `vox-explainer`: documentary "why" film
- `animated-chart`: looping chart for a result or trend
- `milestone-reveal`: particles that resolve into your number

### Open
- `title-sequence-3d`: cinematic 3D opener

### Compare
- `model-showdown`: three models, one brief, one video

### Promote
- `newsletter-promo`: 15-second edition promo
- `loop-cover`: looping cover GIF
- `reel-export`: vertical Reel and TikTok export

## Capabilities

Only install what the job needs. Nothing here needs an API key.

| Workflow | Needs | If it is missing |
|---|---|---|
| Any skill, on-brand | `brand.md` and `MOTION.md` from `brand-intake` | The skill asks for hex codes, font and logo, and does not call the result on-brand |
| Build any animation | Claude Code on Opus 5.5 | Nothing to build with |
| MP4 export | HyperFrames, or ffmpeg plus Chrome | You get the HTML with `window.seek()`, export pending |
| `loop-cover` measuring | ffmpeg and Python 3 | GIF made, seam and motion unmeasured, so not called done |
| `reel-export` and `model-showdown` stacking | ffmpeg and ffprobe | Stacked layout as HTML, final encode and checks pending |
| `model-showdown` | Access to each model through your own accounts | Compare the models you can reach, and say which were left out |
| `apple-launch-film` motion check | The free `apple-design` skill | Builds without it, motion unchecked against Apple's rules |
| Logos and screenshots | Your own files | The skill asks. It never redraws a logo from memory |

## House rules every skill follows

1. **Facts first.** Every name, date and number on screen comes from a list you approve. Nothing invented.
2. **Your brand, not the average.** Colours and fonts come from `brand-intake` or from you. With nothing given, it asks.
3. **Banned defaults:** typewriter text, glow, bounce, gradients on text, purple-to-blue backgrounds.
4. **Motion on twos** for anything hand-made in feel (hold each pose for 2 frames at 24fps).
5. **First 3 seconds carry the hook.** If the first frame is empty, it's cut.
6. **Check before export.** One frame from the middle of every shot, checked for cut-off text, overlaps and wrong facts.
7. **Real assets only.** Logos and screenshots come from your files, never redrawn from memory.

## Pairs well with: Apple's motion rules

A free skill (not mine) that turns Apple's design guidelines into rules Claude follows:

```
npx skills add emilkowalski/skills --skill apple-design
```

Then ask: "Use the apple-design skill to audit this animation. Give me a ranked list of everything that feels off, worst first." Paste the fixes back as notes.

## Pairs well with: real UI components

If your video shows a product, don't let Claude draw the buttons and cards from scratch. It guesses the spacing and the UI looks fake. [21st.dev](https://21st.dev) publishes real components with a prompt under each one. Paste this once, then paste any component prompt straight in:

```
Add this rule to CLAUDE.md: whenever I paste a component prompt or third-party component code, treat it as a structural donor only. Keep its engineering. Replace its demo copy with my real copy, and translate every colour, border, shadow, font and timing to MOTION.md.
```

**One honest limit:** a photoreal human face. Code draws motion, type and UI brilliantly, but a lifelike person still needs an image model (for now).

## Contributing

PRs and issues welcome. Run `bash validate-skills.sh` before you submit. It checks every skill's frontmatter, that the name matches the folder, the description length, and the house style (no em dashes or semicolons in prose, no local paths).

## License

[MIT](LICENSE). Use these however you like. If they help you, a link back to the [newsletter](https://charliehills.substack.com) is appreciated.

— Charlie
