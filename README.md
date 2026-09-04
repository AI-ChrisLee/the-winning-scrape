# The Winning Scrape

Decides your next video off what is already winning with your buyers. It hunts the last
60 to 90 days, ranks every video against its own channel's baseline, picks one
winner and digs it out: the transcript, the thumbnail text, what the comments asked for
and never got. With an idea already in hand, it dresses your idea in the title shapes
that are winning.

It also keeps your demo shelf: hand it the transcript of a job you recorded and it
writes the real screens your own work produced into `squad/screens.md`, so next week's
script gets written to footage that already exists.

## Install

Say this to Claude Code, in the folder your squad lives in:

    Install this skill: https://github.com/AI-ChrisLee/the-winning-scrape. Clone the whole folder into .claude/skills as the-winning-scrape, without the .git folder.

## Run

    Run the winning scrape.

It asks a few questions (do you already have this week's idea; which channels your
buyers watch), asks for one yes before the hunt, then comes back with the pick and the
runner-ups. You fix the pick or swap it, change any word in a title that is not yours,
and it writes `squad/week/<date>-winner.md` (and `squad/lane.md` on the first run).

The other mode, after you record a job:

    Stock my demo shelf.

Give it the transcript and it drafts one row per real moment, then stops. You cut the
rows you would not put in front of a stranger and say whether each screen is your own,
sanitised, or shown with permission. What survives lands in `squad/screens.md`.

The full procedure is `SKILL.md`. Stuck? Reply to the email that sent you here.
