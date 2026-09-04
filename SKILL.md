---
name: the-winning-scrape
description: Use this every week to decide the video. It hunts what is winning with your buyers right now, ranks it against each channel's own baseline, and forks on one question: no idea yet, and it picks ONE winner and digs it out completely (transcript, thumbnail text, what the comments complained about); idea already in hand, and it dresses your idea in the title shapes that are winning. First run also sets your lane: the niche and the search vocabulary it reuses every week after. Use it a second way when the founder says "Stock my demo shelf", "write my demo shelf", or hands over the transcript of a job they recorded: that mode reads their own recording and writes the real screens their work produced into squad/screens.md, so next week's script is written to footage that already exists.
---

# The Winning Scrape

You are the weekly picker. One winner, followed closely, freshly hunted every week; that
is what keeps it timely. You never invent an angle or a shape. Downstream: the Proven
Package packages the video and the Payoff Script writes it, both from the file you hand
over.

Read `.claude/squad-roots.md` first, the per-repo instance file every member-run skill
shares: founder name · brand words (the product word plus its banned synonyms) · accent
color · lane · week · episodes · credibility-bank · face · thumb-cages · voice
file · wpm (110 default) · data sources · screens (the `shelf` mode writes that row the
first time) · tools (the research mode this repo has).
Its values win over the `squad/` paths written below, which are worked examples. The
Winning Offer writes this file at the end of its run; fill any field you learn here
(the lane, above all) and never re-ask for one it already answers. A repo carrying the
legacy `.claude/spine-roots.md` keeps working: read that as the fallback when no
squad-roots.md exists.

## The two modes

| Mode | What the founder says | What runs |
|---|---|---|
| `pick` (default) | "Run the Winning Scrape." | beats 1 to 7: this week's video, picked off other people's numbers and dug out |
| `shelf` | "Stock my demo shelf.", or a job recording's transcript handed over | SHELF: the founder's OWN finished work read off one transcript into `squad/screens.md` |

Never both in one session. `shelf` hunts nothing, reads no channel and ranks
nothing; it is the supply line the Payoff Script asks for, and its own two-beat
map sits in its section below.

## The run map (where you run, where you STOP)

The `pick` mode.

| Beat | Mode |
|---|---|
| 1 SAY | HUMAN INPUT: the questions; the first answer picks the branch |
| 2 AGREE | **STOP · GATE: yes before the hunt** |
| 3 HUNT | AUTO |
| 4 RANK | AUTO |
| 5 SEAM | AUTO |
| 6 BRANCH | DIG: pick ONE winner, then **STOP · GATE: the founder fixes the pick** · DRESS: clone the shapes onto the founder's idea |
| 7 HANDOVER | Produce the files, then **STOP · GATE: approval + the voice pass on titles** |

Never pause the AUTO beats; batch small questions into the gates.

## 1 · SAY

Ask, in one message:

1. **Do you already have this week's video idea?** Yes: paste it (DRESS branch). No: the
   numbers will pick one (DIG branch).
2. What do you sell, in one sentence?
3. Who buys it?
4. Name 2-3 YouTube channels your buyers probably watch. (Skip if unknown.)

Skip 2-3 when `squad/business.md` exists (the Winning Offer writes its offer document there). For 4,
read the channels-mined section of `squad/offer-research.md` first when that file exists,
play those names back, and ask only whether to add or drop any; ask cold only when the file
is absent. Read the rest of that file too: its verbatim quotes and its `## BUYER LANGUAGE`
section (the one standing record of real replies, DMs, and objections, which the Pipeline
appends to) count as pasted buyer language, and its `## CHANNEL BASELINES` are the starting
numbers HUNT re-verifies. Read `squad/credibility-bank.md` too when it exists: its receipts
are the real figures DRESS can offer for the `[X]` slots. Weekly runs: read the last
published row and the latest `## Sundays` row of `squad/content-log.md` (the roots file's
`content log` row when it names one) and put both in front of the founder in this same
message, before question 1, so the answer picks the branch off last week's result; a proven
winner of your own outranks a fresh hunt, and a flop's repackage counts as an idea in hand
(DRESS). No log file or no published row yet: skip it silently. If the founder has real
buyer replies, comments, or DMs, ask for 3-5 pasted in; real buyer language outranks
everything you find.

**First run only** (no `squad/lane.md` yet): this run also sets THE LANE, the direction
the channel fights in: the niche named plainly, and the search vocabulary (the 6+ queries
that found winners). When `squad/business.md` and `squad/offer-research.md` exist, the
niche was already decided once, so read those judgments before naming a lane: the offer
document's SWITCHING ITCH and ANSWER lines, and the research file's direction call and
empty seat. State the lane against them at the AGREE gate ("your offer document says X;
this lane fights there" or "departs there, and here is why"). The answer's week-one
attack weights the DIG pick and rides into the winner file. Save the lane; every later
run reuses it, and it refreshes at season boundaries or when the seam shifts.

## 2 · AGREE

Play back the branch and the hunt plan with reasons. Tell the founder what the run will
ask permission for, in kinds: web search, page fetches (one prompt per new domain),
shell commands for the raw-page pulls, and the one-time transcript tool install used at
HANDOVER (the install ladder HANDOVER defines). Say allow each once for the session and
the AUTO beats run unbroken. Get a yes; the yes covers the
install. A declined permission is stated plainly in the output as a gap in the data,
never silently worked around.

## 3 · HUNT

Search at least 6 ways, last 60-90 days only. Later runs: the saved vocabulary from
`squad/lane.md`. First run (no lane file yet): derive the 6+ queries from the SAY
answers, seeded by the buyer channels from question 4; at least half must name the
BUYER's problem in the buyer's words, not the service category. Question 4 skipped:
HUNT first finds 2-3 candidate buyer channels itself and confirms them topically (the
channel-identity rule) before deriving the queries. The queries that found
winners get saved to `squad/lane.md` at HANDOVER.

For every promising video: title, channel, subscribers, views, age, URL. Identify
channels by searching and confirming, never by guessing a handle. A row without
a link does not exist.

No API installed (the default fresh install): the zero-quota toolkit IS the primary path,
run clean with no flag. The numbers live in JSON embedded in the raw HTML
(`ytInitialData` / `ytInitialPlayerResponse`); a plain markdown fetch strips them, so
raw curl is the method: curl the page, grep the field. A markdown-fetch miss is a
tooling miss, never evidence the niche is thin. The toolkit, one line per datum:

- Finding candidates: curl the results page
  (`youtube.com/results?search_query=<the+query>`) and grep `videoRenderer` for video
  ids, then date-verify each row on its watch page. Built-in web search is the
  supplement, not the primary, since it cannot filter results by upload date and the
  60-90 day window is the rule this beat runs on.
- Channel identity: the oEmbed endpoint (`youtube.com/oembed?url=<video-url>&format=json`).
- Channel id from a handle: curl the channel page, grep `"channelId":"UC` (one step;
  oEmbed returns only the handle URL).
- Baselines: the channel RSS feed by channel id
  (`youtube.com/feeds/videos.xml?channel_id=UC...`), the last ~15 uploads with per-video
  view counts. When `squad/offer-research.md` carries `## CHANNEL BASELINES`, start from
  those medians and re-verify them; never recompute a channel cold that the Winning Offer
  already measured.
- Views, date, duration on one video: curl the watch page, grep `viewCount`,
  `publishDate`, `lengthSeconds`.
- Subscribers: curl the channel about page, grep `subscriberCountText`.
- Likes (the bought-reach test): the watch page again, grep `likeCount`.
- Thumbnails: download the jpg (`i.ytimg.com/vi/<id>/hqdefault.jpg`) into
  `squad/week/thumbs/<winner-date>/src/` (this run's date, the date the winner file
  carries), then Read the local file. HANDOVER keeps the ranked survivors' jpgs and
  deletes the rest. Never describe a thumbnail you did not view; the
  honest fallback is a THUMBNAIL UNREACHABLE label, same law as the transcript and
  comments rules.
- The transcript: the approved tool from HANDOVER.

Empty greps on EVERY page mean a consent or bot wall (common outside North America),
never a thin niche: retry with a `CONSENT=YES+1` cookie header, and say so plainly if it
persists. Search snippets never count as verification. A wired scraping tool (Apify,
where set up) may speed the fan-out; keyless stays the default and the run never needs
it. The Quota-dies flag is only for an API that failed mid-run.

## 4 · RANK

**The loop line first, before anything is ranked.** Read the founder's own last published
row in `squad/content-log.md`, resolve their channel from that row's video id (oEmbed), and
print ONE line: the last pick, the shape it cloned (matched against `squad/lane.md`'s SHAPE
TEMPLATES), the layer it was recorded on (the first line of that episode's `00_PREP.md`),
and what it did against the founder's OWN baseline under the laws below. Anything not
recorded prints `not recorded`, never a guess. That line is the whole of "gets better every
week" in this lane: last week's result on screen at the moment this week's pick gets made.
No log file, or no published row yet: say so in one line and move on.

Two numbers; the first rules:

    breakout = views / the channel's own baseline
    (baseline = median views of that channel's last 10-20 comparable long-form uploads)
    subs multiple = views / subscribers (secondary; use alone only when uploads are
    unpullable, marked as the weaker read)

**The baseline laws, stated once here.** Long-form means over 4 minutes. A one-minute
vertical upload YouTube does not call a Short still drags a median far enough down to turn
a loser into next week's winner: on the author's own channel the unfiltered median reads
1,007.5 against a true 2,207.5, so every multiple comes back 2.19x too high.

- **The founder's OWN channel: verify every upload's real duration on the watch page.**
  Once per run, at the loop line. One channel, about fifteen requests, and it is the number
  every multiple divides by. Wherever an API is installed in this run, never trust an
  `is_short` field; read the duration. That field returns false for one-minute vertical
  uploads and true for a zero-second live stream.
- **A competitor's channel keeps the priced rule**: no duration filter, the median marked
  approximate, real durations verified only for the top 3 candidates' channels. The RSS
  feed carries no durations at all, and fifteen extra requests per channel is not worth
  spending on a row nobody will pick.
- **The 2026-08-24 seam: refuse, do not label.** On 2026-08-24 YouTube began counting a
  view from the first frame, so a window straddling that date mixes two definitions of the
  word. Print `baseline uncomputable, window straddles 2026-08-24` and rank that channel on
  the flagged subs multiple. A caveat printed next to a number does not stop a founder
  copying an inflated winner, and the pick is the one thing this skill protects.
- **Under 8 comparable long-form uploads there is no distribution.** Print `baseline
  uncomputable, N uploads` and rank on the flagged subs multiple. Same rule for a thin
  competitor channel and for the founder's own.

Discard below 0.5x. Discard bought reach: a spike with almost no likes or comments
relative to its views, or a video running as an ad, is not a winner; drop it and say
why. Keep the top 8-12, sizes noted, links attached.

The widen ladder, stated once, here: 0.5x is the discard floor. Nothing clears 1x = no
winner yet; say so and widen one notch, the run's single widen. **A notch is one step up
the specificity ladder**: the buyer's wider job, or the parent category of the problem, in
the buyer's own words, same 60-90 day window, same vocabulary discipline. Never a jump to
a different market. Worked example: bookkeeping for dental practices widens to running a
dental practice's money (overhead, collections, payroll: the same buyer's wider job), not
to bookkeeping for small businesses (a different buyer) and not to a six-month window.
Still under 1x after the widen: carry the best row forward flagged as a below-baseline
CONTENT FIT pick, and the founder decides at the DIG gate with the number in view.
Nothing clears 0.5x after the widen: reframe with the catch-surface note in
`squad/lane.md` (the thin-after-one-widen edge rule), never widen again. A forced pick is
worse than an honest miss.

Then write the checkpoint: the ranked candidate table (numbers, links, baselines) to
`squad/week/YYYY-MM-DD-hunt.md`. A session resumed after a crash, a usage cap, or a
/clear reads today's hunt file and re-enters at SEAM instead of re-hunting; HANDOVER
folds it into the winner file.

## 5 · SEAM

Name what repeats across survivors: topic angle, title shape, promise. Three 2x videos
with one shape beat one lucky 10x. Write each winning title shape as a template with
slots, next to the linked video that proved it and that video's RANK numbers: the
breakout multiple, the baseline it was measured against, and today's date as the date
measured. The Package ranks shapes on those written numbers instead of recomputing them.

## 6 · THE BRANCH

**DIG (no idea):** pick ONE winner, the best intersection of multiple, seam, and the
founder's business. Weekly runs: before presenting, re-verify the lane's NEXT IN LINE
rows against fresh numbers; a surviving row competes as a candidate. Present: the pick,
the 3-5 runner-ups (one line each), and why. The runner-ups feed NEXT IN LINE.
STOP: the founder fixes the pick before anything gets built on it.

**DRESS (idea in hand):** the founder's idea gets 2-3 title candidates, every one a
strict clone of a top shape from step 5, labeled with the shape and linked to the winner
it clones. One variable changed per title. Number slots stay `[X]` until the founder
supplies real figures; never invent one, though when `squad/credibility-bank.md` exists
you may offer its receipts for the slots, the founder confirming each at the gate. Also
name the closest winner to the idea; its winner file still gets built (the Package and
the Payoff Script need source material either way).

## 7 · HANDOVER: the winner file

Build ONE file, `squad/week/YYYY-MM-DD-winner.md`:

- The winner: title, channel, numbers, URL (DRESS: plus the chosen title candidates).
- **The transcript**, pulled in full. The working pull is a one-time transcript tool
  install (e.g. `yt-dlp`), run on the okay batched into the AGREE gate; the watch page
  alone returns no captions on a fresh keyless install. The install ladder, stated once
  and referenced from AGREE: brew, else pip3 or pipx, else the standalone binary curled
  into the repo root; on Windows, skip straight to the standalone `yt-dlp.exe`. The binary
  lives in the repo root on every OS.
- **The thumbnail, described**: exactly what text it carries and what it shows, from the
  downloaded file the run actually Read (the toolkit's download-then-Read step), never
  from the title or the numbers. Download failed = the THUMBNAIL UNREACHABLE label,
  never a guess.
- **The comments, mined**: top questions, complaints, and "you never showed X" moments,
  verbatim with like counts. The pull rides the same approved tool, no second approval
  needed, capped to the top ~100 by likes; uncapped, a popular winner pulls for silent
  minutes and reads as a broken run. The exact command, so every session behaves the
  same: `yt-dlp --write-comments --extractor-args
  "youtube:comment_sort=top;max_comments=100,all" <url>`. What the winner's audience
  wanted and did not get is our angle's sharpest edge.
- **The angle**: what we add or fix, two sentences. When the offer document named a week-one
  attack, its line goes here too; the Package and the Payoff Script read this file, not
  the offer document.

Fold today's hunt checkpoint (`squad/week/YYYY-MM-DD-hunt.md`) into the winner file and
remove it; the checkpoint's job ends here. The candidate thumbnails in
`squad/week/thumbs/<winner-date>/src/` outlive the run: keep the top 8-12 ranked
survivors' jpgs, the winner's among them, and delete only the unranked rest. Those
survivor jpgs are the Proven Package's cage-distillation input, the pictures it distills
this lane's own thumbnail cages from when none of its shipped cages was proven in this
niche. Say in the winner file how many survivor jpgs the folder holds.

First run: also write `squad/lane.md` here (the template below), from the vocabulary
that actually hunted and the shapes step 5 proved, with this week's runner-ups in its
NEXT IN LINE section, numbers and links attached, counted the way the template defines.

STOP: approval plus the voice pass on any title: the founder changes any word in a title
that does not sound like them. Then close, word for word,
branch-marked: DIG closes "Picked and dug. Packaging it is the Package's job, writing it
is the Payoff Script's, making it is the system's. This skill stops here." DRESS closes
the same, opening "Dressed and dug." instead.

## SHELF · the founder's own screens (the `shelf` mode)

The founder recorded a job they were doing anyway. This mode turns that recording
into rows the next script can be written to. Two beats.

| Beat | Mode |
|---|---|
| S1 READ | AUTO: the transcript in, the rows drafted, nothing written yet |
| S2 SHELF | **STOP · GATE: the founder cuts the rows and answers the safety call on each survivor** |

**Input, and there is only one.** A transcript path: `.txt`, `.md`, `.srt`, `.vtt`.
The recording's own path too when the founder gives it, and it goes in the row so
the file can be found later. A recording path with no transcript gets one line
back naming the free local transcriber for their laptop (MacWhisper on a Mac,
Buzz on Windows) and waits; nothing uploads and no transcript is made here. No
transcript at all, no run: a row written off the founder's memory of a recording
is exactly the invented screen this whole mode exists to kill.

**What a row is.** One real moment the transcript proves happened: something
finished, something broke, or the founder said out loud why they did what they
did. The spoken reasons are the index, so a job the founder narrated comes back
full and a silent job comes back nearly empty. Say that in one line rather than
filling the file.

Six columns, and every cell comes off the transcript or off the founder:

    | Date | Time in the recording | On the screen | The file or URL behind it | Why it matters | Safe to show |

The time comes from the transcript when it carries one (`.srt` and `.vtt` do); a
plain `.txt` leaves that cell empty for the founder to fill, never estimated. The
why line is the founder's own spoken reason, tightened, never written for them.
A moment the transcript does not carry is not a row.

**S2, the gate.** Print the drafted rows and stop.

- The founder cuts every row they would not put in front of a stranger.
- Every survivor gets the safety call, one word: `own` (an account or a file
  that is yours), `sanitised` (names and numbers changed), or `permitted`
  (written permission from the client). That answer fills the last column,
  because the Payoff Script settles it before any beat gets drafted and this is
  where it gets answered once, with the work still fresh.
- A row nobody can put in any of those three buckets comes out.

Then append the survivors to `squad/screens.md` (created on the first run with
the header row, appended every run after, never rewritten), write the `screens`
row into `.claude/squad-roots.md` the first time, and close, word for word:
"On the shelf. The Payoff Script asks for your real step list and your safety
call; this file is both answers. This skill stops here."

Resume: the shelf IS the state. Rows already sitting in `squad/screens.md` mean
that transcript is done, and it never gets read twice.

## The outputs (three files, plus the survivor thumbnails)

1. `squad/lane.md`: first run creates it; it holds still between runs and refreshes at
   season boundaries or when the seam shifts. Its template:

       # THE LANE
       <the niche, one line>

       ## SEARCH VOCABULARY
       <the 6+ queries that found winners>

       ## SHAPE TEMPLATES
       <one block per shape: the full skeleton text with slots, the niche that
       proved it, the link to the proving video, and its breakout multiple with
       the baseline it was measured against and the date measured (worked
       example: 4.1x against a 38,000-view baseline, measured 2026-08-26). The
       Proven Package ranks shapes on that written multiple; a shape carrying no
       multiple makes it recompute the number this beat already had.>

       ## NEXT IN LINE
       <the 3-5 runner-ups behind this week's winner (both branches), one line each
       with numbers and links; five rows maximum, the winner not among them; written at
       HANDOVER, refreshed when the seam shifts. Weekly runs always re-hunt fresh:
       this section is the tiebreaker and the fallback when the fresh hunt is thin,
       never a substitute for hunting.>

2. `squad/week/YYYY-MM-DD-winner.md`: the winner file, every `pick` run. The handoff
   to the Proven Package and the Payoff Script.

3. `squad/screens.md`: the `shelf` mode only. One standing file, appended, never
   rewritten, and the `screens` row it adds to `.claude/squad-roots.md` the first
   time it writes.

Nothing else gets written. The RANK checkpoint (`squad/week/YYYY-MM-DD-hunt.md`) is working state, not an output;
HANDOVER folds it into the winner file and removes it. The candidate thumbnails HUNT
downloads are not working state: the top 8-12 ranked survivors' jpgs stay in
`squad/week/thumbs/<winner-date>/src/` (the folder the Proven Package already owns) as
that skill's cage-distillation input, and HANDOVER deletes only the unranked rest.

## Edge rules (learned in testing, nine niches)

- **Quota dies** (an installed API failed mid-run; a fresh keyless install is NOT this
  state): fall back to plain web search plus the zero-quota toolkit defined in HUNT.
  Flag it; never fabricate a search you could not run. When even per-item lookups die,
  proceed on CONTENT FIT for outline-stage work only, mark RANK incomplete in every
  file this run writes, and re-verify the numbers before any title locks.
- **Baseline exclusions**: compute the median EXCLUDING the candidate video itself and
  any confirmed bought-reach spikes. Mixed-topic or mixed-format channels: median over
  comparable uploads only (long-form with long-form, same topic). Shorts are
  identifiable with one keyless test: fetching `youtube.com/shorts/<id>` returns the
  short directly and redirects to `/watch` for long-form. The duration floor, the seam
  refusal and the 8-upload minimum are RANK's baseline laws; RANK states them once and this
  list does not restate them.
- Baseline uploads may be older than 90 days; only the WINNER pick must be recent.
- **Channel stats unpullable** (zeroed counts, broken uploads list): keep the row's
  verifiable parts, mark the baseline uncomputable, rank on the flagged subs multiple.
- **Shorts never get ranked.** Shorts are cuts OF the long-form made later, not the
  hunt's input, and their natural low engagement breaks the bought-reach test.
  Hunt and rank long-form only.
- **Channel identity needs a topical check**: read a sample of actual content, not just
  the name (a right-named channel can belong to a different industry).
- **Comment-poor winner** (quiet B2B niches): report every comment verbatim, state the
  shortfall as a finding, and optionally add the nearest real on-topic thread clearly
  labeled as off-winner evidence. Near-zero comments is data, not failure.
- **Comments UNREACHABLE** (the `--write-comments` pull failed; tooling, not scarcity):
  say so, record the visible total count if any surface shows it, substitute the
  transcript's sharpest lines clearly
  labeled as transcript-not-comments, and mark the section for a re-pull before the
  Package finalizes. Never present the substitution as mined comments.
- **Transcript UNREACHABLE** (the tool fails, or the video carries no captions): state
  the failure, substitute the video's description plus its on-screen text clearly
  labeled as description-not-transcript, and mark the section for a re-pull before the
  Package finalizes. Never present the substitution as the transcript.
- **Non-English winner**: the transcript still gets pulled in full, plus a condensed
  English pass for the handoff; say which parts are translation.
- **DRESS collisions**: if the closest winner by mechanism and the best-mineable winner
  diverge, the winner file follows the video whose SHAPE the chosen title clones; note
  the other. If the founder's own idea turns out to be a dead shape in the data, that
  finding goes to the gate, said plainly; the run map does not fork for it. And when the
  winner's lever is not the founder's to borrow (a famous brand, a huge claim), clone
  the shape's DNA, the transferable ingredient (a real, specific, high-stakes number),
  never the untransferable lever.
- **Thin after one widen**: say so plainly, then reframe instead of retreating. YouTube
  stays the anchor and the archive (the recording's home, the search shelf, the system's
  input); a thin YouTube niche means your buyer gets caught on LinkedIn posts and
  community rooms instead. Record that in `squad/lane.md` so the repurposing skill
  weights those legs when it arrives. The system does not change; the catch surface
  does. Never widen again.
- **A thin niche produces a thin file that says so.** Density is the market's property,
  not the skill's promise; a plainly-stated thin read at full rigor is a PASS.
- **Season refresh**: at a season boundary the founder says so. The full first-run hunt
  reruns on fresh data, `squad/lane.md` is rewritten, and NEXT IN LINE is re-picked.
  Between seasons the lane holds still.

## Rules

- Every message to the founder is scannable: a short header, then bullets or a
  table. The ranked candidates, the shape templates, and the run map go in TABLES;
  findings go in short bullets with the key number in bold. Never a wall of paragraphs.
  The founder reads while deciding, not studying.
- Real numbers only; unverifiable rows get dropped. Every row carries its URL.
- Buyer language wins ties: an angle answering a real pasted reply beats a higher
  multiple that answers none.
- Clone the shape, never the words. The one-variable swap IS the difference.
- The shelf carries no moment the transcript does not prove, and no screen the
  founder has not called `own`, `sanitised` or `permitted`.
- The one widen runs on RANK's ladder; RANK states it once, including what one notch
  is, and this list does not restate it.
- Weekly. The lane file holds still between runs and refreshes at season boundaries or
  when the seam shifts; the hunt is always fresh.
