# Motion Graphics Skill Pack

Five skills that make launch-grade motion graphics with Claude Code. Every frame is code. No After Effects, no video generator.

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

## Pick by what you want

| You want to... | Use |
|---|---|
| Launch a product, offer or cohort | `launch-video` |
| Explain a "why" question people half understand | `vox-explainer` |
| Stop the scroll in the first 3 seconds | `title-sequence-3d` |
| Show a result, a stat or a trend | `animated-chart` |
| Get people to read your newsletter | `newsletter-promo` |

## Three ways I use it

1. **Promote a newsletter edition:** `newsletter-promo` turns the edition into a 15-second clip for LinkedIn and Instagram.
2. **Drive people to Substack:** every clip ends on the newsletter name and "Read it free at…". `title-sequence-3d` and `vox-explainer` make the scroll-stoppers that carry it.
3. **Start your own launch video:** `launch-video` is the one to run first if you're launching an offer, a cohort or a product.

## Install

1. Download this repo (green **Code** button, then **Download ZIP**) and unzip it.
2. Copy the five folders inside `skills/` into `~/.claude/skills/` (or your project's `.claude/skills/`).
3. Open Claude Code, pick Opus 5.5 with `/model`.
4. For MP4 export, add HyperFrames once (free, open source): `npx skills add heygen-com/hyperframes`.
5. Say what you want: "make a launch video for my coaching programme". The right skill loads itself.

## House rules every skill follows

1. **Facts first.** Every name, date and number on screen comes from a list you approve. Nothing invented.
2. **Your brand, not the average.** Colours and fonts come from you. With nothing given, it asks.
3. **Banned defaults:** typewriter text, glow, bounce, gradients on text, purple-to-blue backgrounds.
4. **Motion on twos** for anything hand-made in feel (hold each pose for 2 frames at 24fps).
5. **First 3 seconds carry the hook.** If the first frame is empty, it's cut.
6. **Check before export.** One frame from the middle of every shot, checked for cut-off text, overlaps and wrong facts.
7. **Real assets only.** Logos and screenshots come from your files, never redrawn from memory.

Made by Charlie Hills · charliehills.substack.com
