# heuristic-eval

A Claude skill that runs an expert heuristic evaluation on any UI screen, wireframe, or prototype, checked against Nielsen's 10 usability heuristics. Findings are logged per issue with a severity rating, so you get a structured, portfolio-ready report instead of a loose list of comments.

This is an AI-assisted heuristic review, one evaluator's pass. It's meant to sit alongside your own review, not replace it. Nielsen's own research shows a single evaluator (human or AI) catches roughly 35% of usability issues, versus 75-85% with 3-5 independent evaluators.

## What it does

Given a screenshot or description of a screen, the skill:

1. Identifies the task the user is meant to accomplish on that screen
2. Walks all 10 of Nielsen's heuristics against it
3. Logs every issue found individually, with:
   - **Issue** – one-line description
   - **Heuristic violated**
   - **Severity** – Low / Medium / High
   - **Why it matters** – the real consequence for the user
   - **Suggested fix**
4. Outputs a markdown report per screen, with a short summary at the end

If you give it specific tasks or user scenarios up front, it'll fold those into "why it matters." If you don't, it evaluates the screen on its own merits.

## Install

**Claude.ai**

1. Download this repo as a ZIP (or just the `heuristic-eval` folder)
2. Go to **Settings → Customize → Skills**
3. Click **"+" → "+ Create skill"** and upload the ZIP
4. Toggle it on

**Claude Code / other CLI agents**

```bash
npx skills add IpshitaChatterjee/heuristic-eval
```

Or drop the folder manually into `~/.claude/skills/` (personal) or `.claude/skills/` (project-level).

## Usage

Share a screen and ask for a review:

> Run /heuristic-eval on this screen.

Or give it a specific task to check against:

> Run /heuristic-eval on this checkout flow, focused on completing a purchase without errors.

## Severity rubric

| Severity | Meaning |
|----------|---------|
| High | Would block task completion, or cause a costly/high-stakes mistake |
| Medium | Causes hesitation or an extra step, but the user recovers |
| Low | Minor friction or polish, unlikely to affect task success |

## Note

Label this output as an AI-assisted heuristic review wherever you use it, in a case study, a client deliverable, or internal documentation. Don't present it as user testing or real-user validation, it's expert inspection, a legitimate but different method.
