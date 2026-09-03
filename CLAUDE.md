# FORGE

A single-file PWA. `index.html` is the entire app — markup, styles and logic. `sw.js` is the
offline cache. Deployed by GitHub Pages from `main`; live about 60 seconds after a commit.

## Read this first

**`docs/DESIGN.md` is not optional reading.** This app is a training program for a 13-year-old,
and several things in it look like arbitrary choices but are deliberate safety decisions taken
against the youth resistance-training literature. Read it before changing behaviour, and do not
"improve" anything it marks as a hard rule.

The short version, so it is impossible to miss:

- **No bodyweight tracking, no body-fat, no appearance language, no before-and-after framing.**
  Anywhere. Ever. If asked to make this "more like Dad's app", weigh-ins are the one thing to refuse.
- **Never to failure, no maximal lifts.** Nothing may reward grinding.
- **Reps are the progression variable, not load.** The bells jump 20–50% between sizes; you
  cannot progress load 5–10% with them.
- **Three sessions a week is the target.** Four pays more but is a bonus, never the goal.
- **No hardcoded YouTube video IDs.** Search links only, or a URL a parent has vetted.
- **Rewards are experiences and kit.** Never food, appearance or bodyweight.

## Working here

- Bump the cache key in `sw.js` on **every** `index.html` change, or the iPad serves a stale copy
  from its offline cache and the change is invisible.
- All training data lives in the browser's `localStorage` on his iPad. Never on GitHub. Any change
  to the stored shape needs a migration in `load()` — old sessions must keep working.
- Dates use local time, never `toISOString()`. That bug once stamped every morning session to the
  previous day.
- There is a browser test suite convention in this project: changes should be verified by driving
  the page, not by reading the diff. Ask before assuming a change works.

## Tone

Copy in this app is written for a 13-year-old and is deliberately dry — direct, unpatronising, no
exclamation marks, no hype. Match it.
