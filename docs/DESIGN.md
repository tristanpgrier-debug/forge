# FORGE — design constraints

Orlando's kettlebell app. He is 13, 175 cm, plays sport, had never lifted when this was built.
Read this before changing anything. Several decisions here look arbitrary and are not.

## Hard rules — do not undo these

**No bodyweight tracking. Ever.** No body-fat, no appearance language, no before-and-after
framing, anywhere in the app. At 13 that combination is the documented risk factor for muscle
dysmorphia, and none of it is needed to give him what he asked for. Progress is shown as bells
lifted, reps added, levels earned. If a future request is "make it more like Dad's app", weigh-ins
are the one feature to refuse.

**Never to failure. No maximal lifts.** This is the clearest instruction in the youth training
literature and it is written into the app's copy. Any feature that rewards grinding contradicts it.

**Rewards are experiences and kit only.** Never food, appearance or bodyweight.

**No generic motivational quote feed or API.** The built-in lines were written for this app.
Stock gym quotes are grindset ("no pain no gain") and argue directly with the rule above; a large
share of the famous ones are also misattributed.

**No hardcoded YouTube video IDs.** The default is a search for the movement. A guessed or stale
ID either dead-links or drops a 13-year-old on whatever now sits at that URL. Specific videos are
pasted by his dad in the Coach tab after he has watched them.

## Why load is not the progression variable

The bells are 4, 6, 8, 10, 12, 16 kg — one of each. The jumps are +50%, +33%, +25%, +20%, +33%.
Youth guidance is to progress load 5–10% at a time, which is arithmetically impossible with this
set. So **reps are the progression variable.** Reps climb inside the range; the bell only moves
once the top of the range is hit on *every* set. "Too hard" walks the reps back, never the load —
a load step down here is a 20–33% cliff. At the 16 kg with the range maxed, the app names a
harder variation instead of asking for more weight.

## Frequency

Three sessions a week on non-consecutive days (NSCA). Tristan originally asked for four; the app
was built as three, with optional finishers absorbing the extra appetite. The reward ladder pays
more for four but frames three as the target, and the app tells him to rest if he trained
yesterday. Do not quietly turn four into the goal.

## Rating scale: three faces, not a number

Each set is rated Easy / Just right / Too hard. There is a 1–10 toggle in the Coach tab, off by
default. The faces are the safer input: this is a novice who cannot reliably tell a 7 from an 8,
and the rep progression runs off whatever this input says. A number here is noise driving load
decisions. The 1–10 mode maps onto the same three buckets underneath.

## Reward points

4 sessions = 3 points, 3 = 2, 2 = 1, 0–1 = 0. Points bank and never reset. The original brief was
"nothing for two" — that was deliberately not built. The weeks he hits two are sick weeks, exam
weeks, school camps. A zero there teaches "the week is already ruined, why bother Thursday."

## Technique unlocks

Swing, Clean and Half Get-up start locked, each with a safe substitute training the same pattern.
His dad unlocks them in the Coach tab against a written checklist. This is what makes
"supervised at first, then solo" safe. Do not unlock them by default.

## Growth spurt

At 175 cm he is likely mid-spurt. Coordination often regresses temporarily while limbs lengthen —
a technique wobble is usually growth, not laziness. Knee or heel pain during a spurt is common and
worth easing off jumping and deep squatting for. Resistance training itself is not the risk.

## Mechanics

Single-file PWA. `index.html` is the whole app. Data lives in the iPad's browser storage, never on
GitHub. **Bump the cache key in `sw.js` on every `index.html` change** or the iPad serves a stale
copy from its offline cache and the update is invisible.

Dates use local time, not `toISOString()` — that bug stamped every morning session to the previous
day in Sydney.

## Open question

As of 3 Sep 2026 the app has a week calendar, a reward bank, a quote of the day, per-set logging
and exercise history — and nobody has completed a session in it. Everything since 4 August is a
guess about what keeps a 13-year-old engaged. The next useful move is not another feature.
