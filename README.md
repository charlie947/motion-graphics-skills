<p align="center">
  <a href="https://charliehills.substack.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/readme/hero-dark.png">
      <source media="(prefers-color-scheme: light)" srcset="assets/readme/hero-light.png">
      <img alt="Motion Graphics Skill Pack by Charlie Hills" src="assets/readme/hero-light.png" width="100%">
    </picture>
  </a>
</p>

<h1 align="center">Motion Graphics Skill Pack</h1>

<p align="center">
  <strong>13 skills that make launch-grade motion graphics with Claude Code. Every frame is code.</strong>
</p>

<p align="center">
  <a href="https://github.com/charlie947/motion-graphics-skills/stargazers"><img src="https://img.shields.io/github/stars/charlie947/motion-graphics-skills?style=flat-square&color=D97557&labelColor=00132F&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-13-D97557?style=flat-square&labelColor=00132F" alt="13 skills">
  <img src="https://img.shields.io/badge/runs_in-Claude_Code_%C2%B7_Codex-58B6FF?style=flat-square&labelColor=00132F" alt="Runs in Claude Code and Codex">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/charlie947/motion-graphics-skills?style=flat-square&color=FFFFFF&labelColor=00132F" alt="Licence"></a>
  <a href="https://charliehills.substack.com"><img src="https://img.shields.io/badge/newsletter-71k_readers-FFD11A?style=flat-square&labelColor=00132F" alt="MarTech AI newsletter"></a>
</p>

<p align="center">
  <a href="#install">Install</a> &nbsp;·&nbsp;
  <a href="#see-it-work">See it work</a> &nbsp;·&nbsp;
  <a href="#the-skills">The skills</a> &nbsp;·&nbsp;
  <a href="#how-they-fit-together">How they fit</a> &nbsp;·&nbsp;
  <a href="#prompts">Prompts</a> &nbsp;·&nbsp;
  <a href="https://charliehills.substack.com">Newsletter</a>
</p>

---

I make launch videos, animated charts and reels without After Effects or a video generator. Claude Code writes the animation as code, draws every frame and renders an MP4. These 13 skills are the workflows I use, with the rules that came out of real rejected drafts.

## Install

One line, about 30 seconds:

```bash
npx skills add charlie947/motion-graphics-skills
```

Then open Claude Code, pick Opus 5.5 with `/model`, and run `brand-intake` first.

<details>
<summary><strong>Manual copy into Claude Code</strong></summary>

Download this repo (green **Code** button, then **Download ZIP**) and unzip it, or clone it:

```bash
git clone https://github.com/charlie947/motion-graphics-skills.git
```

Copy the 13 folders inside `skills/` into `~/.claude/skills/` (every project) or your project's `.claude/skills/` (one project). This loop keeps any skill folder you already have:

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

</details>

<details>
<summary><strong>Claude Desktop (upload one skill)</strong></summary>

Zip one skill folder and upload it in Customise, then Skills. From `motion-graphics-skills/skills`:

```bash
zip -r brand-intake.skill brand-intake
```

Start with `brand-intake`, then add the skills you need.

</details>

<details>
<summary><strong>Codex</strong></summary>

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

</details>

<details>
<summary><strong>Export to MP4</strong></summary>

Add HyperFrames once (free, open source): `npx skills add heygen-com/hyperframes`.

</details>

## See it work

<table>
  <tr>
    <td width="64%" valign="top"><img src="assets/readme/demo-launch.gif" alt="A 20-second product launch film built entirely in code" width="100%"></td>
    <td width="36%" valign="top"><img src="assets/readme/demo-milestone.gif" alt="A 12-second milestone loop that resolves into 250,000 LinkedIn followers" width="100%"></td>
  </tr>
  <tr>
    <td valign="top"><sub>A 20-second launch film. Deep blue glass, one glow, every word from a fact list I approved. No screen recording.</sub></td>
    <td valign="top"><sub>A 12-second milestone loop. A night sky of points pulls into my real number.</sub></td>
  </tr>
</table>

### Start here: one line, 60 seconds

Before any skill, paste this into Claude Code on Opus 5.5:

```
Make a dynamic 15-second motion graphics video that shows what an incredible motion designer you are. Go all out.
```

Then change it by describing the edit:

- "Slow down the second scene."
- "Swap the text for mine: [your words]."
- "Use my brand colours: [hex codes]."
- "Make it 1080 x 1350 for LinkedIn."

When you want a specific job done properly, pick a skill below.

## The skills

Thirteen skills, in the order you use them. Type the line on the right into Claude Code and the right skill picks it up.

| Stage | Skill | What you get | Say this |
|---|---|---|---|
| Set up | [**brand-intake**](skills/brand-intake/) | Builds brand.md and MOTION.md. Every other skill reads them first. | "Set up my brand for motion. Here are five frames I like." |
| Plan | [**motion-brief-writer**](skills/motion-brief-writer/) | Turns a rough idea into a precise build brief in your brand. | "Write me a motion brief for my next milestone post." |
| Launch | [**launch-video**](skills/launch-video/) | A 30 to 45 second launch for a product, offer or cohort. | "Make a launch video for my new cohort." |
| Launch | [**apple-launch-film**](skills/apple-launch-film/) | A Mac-style launch film. Menu bar, notch and widgets, all code. | "Make it look like an Apple keynote launch." |
| Explain | [**vox-explainer**](skills/vox-explainer/) | A 30 to 60 second documentary explainer. | "Make a Vox-style video: why do we dream?" |
| Explain | [**animated-chart**](skills/animated-chart/) | A looping chart. Every value stays exactly as you give it. | "Animate my chart. Here are my numbers." |
| Explain | [**milestone-reveal**](skills/milestone-reveal/) | A night sky of points that pulls into your real number. | "Make a milestone video for my follower count." |
| Explain | [**motion-effects**](skills/motion-effects/) | 16 premium effects in your brand, as 8-second loops. | "Build the search-to-results effect in my brand." |
| Open | [**title-sequence-3d**](skills/title-sequence-3d/) | An 8 to 15 second 3D opener that stops the scroll. | "Make a cinematic 3D intro for my next video." |
| Compare | [**model-showdown**](skills/model-showdown/) | One brief, three AI models, stacked into one video. | "Same prompt, three AIs. Make a model showdown." |
| Promote | [**newsletter-promo**](skills/newsletter-promo/) | A 12 to 20 second promo that sends people to an edition. | "Make a promo for this week’s newsletter." |
| Promote | [**loop-cover**](skills/loop-cover/) | Your newsletter cover as a seamless looping GIF. | "Make my newsletter cover a looping GIF." |
| Promote | [**reel-export**](skills/reel-export/) | Any video as a clean 1080 x 1920 Reel or TikTok. | "Make this a reel for Instagram." |

See each skill's `SKILL.md` for its trigger phrases, the inputs it asks for and what it learned the hard way.

## How they fit together

Run `brand-intake` once. It writes `brand.md` (who you are, what you sell, your assets) and `MOTION.md` (your colours, type, timing and motion rules), and adds a rule to CLAUDE.md so Claude reads both before it animates anything. Every other skill reads those two files first. Without them, a skill asks for your hex codes, font and logo, and never calls its result on-brand.

```mermaid
flowchart TD
  B["brand-intake<br/>brand.md + MOTION.md"] --> P["Plan<br/>motion-brief-writer"]
  B --> L["Launch<br/>launch-video · apple-launch-film"]
  B --> E["Explain<br/>vox-explainer · animated-chart<br/>milestone-reveal · motion-effects"]
  B --> O["Open<br/>title-sequence-3d"]
  B --> C["Compare<br/>model-showdown"]
  B --> R["Promote<br/>newsletter-promo · loop-cover · reel-export"]
```

## Use it

Run `brand-intake` first, then say what you want. The right skill loads itself:

```
"Set up my brand" → brand-intake
"Brief this animation" → motion-brief-writer
"Make a launch video for my coaching programme" → launch-video
"Make an Apple-style launch for my app" → apple-launch-film
"Why does every logo look the same now?" → vox-explainer
"Animate my Q3 chart" → animated-chart
"Celebrate 10,000 subscribers" → milestone-reveal
"Build the chart morph with my numbers" → motion-effects
"Make a button that turns into a video player" → motion-effects
"Give me a cinematic opener" → title-sequence-3d
"Same prompt, three AIs" → model-showdown
"Promo for this edition" → newsletter-promo
"Make my cover move" → loop-cover
"Make this a reel" → reel-export
```

<details>
<summary><strong>The brief behind my "Why do we dream?" film</strong></summary>

One line gets you close. A proper brief gets you something people share. This is exactly what I typed (with `vox-explainer` installed):

```
Why do we dream? And then someone suddenly wakes up, zooms out of the eye, and goes into outer space. There are neural networks of interconnectivity to convey the brain.
```

It found a source for every fact before it drew anything, wrote the script, added a voice and rendered it. Then give it notes like you would a designer.

</details>

## Prompts

Every prompt from the edition, ready to paste, one file per job. Each one says when to use it.

| File | What is in it |
|---|---|
| [start-here.md](prompts/start-here.md) | The one-line starter, the edit-by-describing lines and what to do tonight |
| [brand-design-system.md](prompts/brand-design-system.md) | The MOTION.md prompt and the CLAUDE.md read-first block |
| [briefs.md](prompts/briefs.md) | The "Why do we dream?" brief and the real designer notes I gave |
| [polish.md](prompts/polish.md) | The Apple motion audit, the real-components rule and the fix-one-thing prompt |
| [effects.md](prompts/effects.md) | 16 prompts, one per effect, each built from scratch in your brand |

Want the 16 effects as one editable animated board, plus a PDF guide? Get it free at https://charliehills.substack.com/p/opus-55-motion-graphics

<details>
<summary><strong>What each skill needs to run</strong></summary>

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

</details>

<details>
<summary><strong>House rules every skill follows</strong></summary>

1. **Facts first.** Every name, date and number on screen comes from a list you approve. Nothing invented.
2. **Your brand, not the average.** Colours and fonts come from `brand-intake` or from you. With nothing given, it asks.
3. **Banned defaults:** typewriter text, glow, bounce, gradients on text, purple-to-blue backgrounds.
4. **Motion on twos** for anything hand-made in feel (hold each pose for 2 frames at 24fps).
5. **First 3 seconds carry the hook.** If the first frame is empty, it's cut.
6. **Check before export.** One frame from the middle of every shot, checked for cut-off text, overlaps and wrong facts.
7. **Real assets only.** Logos and screenshots come from your files, never redrawn from memory.

</details>

<details>
<summary><strong>Pairs well with: Apple's motion rules</strong></summary>

A free skill (not mine) that turns Apple's design guidelines into rules Claude follows:

```
npx skills add emilkowalski/skills --skill apple-design
```

Then ask: "Use the apple-design skill to audit this animation. Give me a ranked list of everything that feels off, worst first." Paste the fixes back as notes.

</details>

<details>
<summary><strong>Pairs well with: real UI components</strong></summary>

If your video shows a product, don't let Claude draw the buttons and cards from scratch. It guesses the spacing and the UI looks fake. [21st.dev](https://21st.dev) publishes real components with a prompt under each one. Paste this once, then paste any component prompt straight in:

```
Add this rule to CLAUDE.md: whenever I paste a component prompt or third-party component code, treat it as a structural donor only. Keep its engineering. Replace its demo copy with my real copy, and translate every colour, border, shadow, font and timing to MOTION.md.
```

</details>

> [!NOTE]
> **One honest limit:** a photoreal human face. Code draws motion, type and UI brilliantly, but a lifelike person still needs an image model (for now).

## Contributing

Found a way to improve a skill? [Open a PR](https://github.com/charlie947/motion-graphics-skills/pulls). Stuck? [Open an issue](https://github.com/charlie947/motion-graphics-skills/issues).

Run `bash validate-skills.sh` before you submit. It checks every skill's frontmatter, that the name matches the folder, the description length, and the house style (no em dashes or semicolons in prose, no local paths) across every skill, its reference files and the prompts folder.

## Built by

<table>
  <tr>
    <td width="96" valign="top"><img src="assets/readme/charlie.png" width="80" height="80" alt="Charlie Hills"></td>
    <td valign="top">
      <strong>Charlie Hills</strong><br>
      <sub>I write the MarTech AI newsletter for 71,000 readers and share what I build with Claude every week.</sub><br>
      <a href="https://charliehills.substack.com">MarTech AI newsletter</a> &nbsp;·&nbsp;
      <a href="https://www.linkedin.com/in/charlie-hills/">LinkedIn</a> &nbsp;·&nbsp;
      <a href="https://github.com/charlie947">More repos</a>
    </td>
  </tr>
</table>

## Licence

[MIT](LICENSE). Use these however you like. If they help you, a link back to the [newsletter](https://charliehills.substack.com) is appreciated.
