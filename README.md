# WE ARE EIGHT — 2026 World Cup Sweepstake

A live-draw site for an eight-person, six-teams-each World Cup sweepstake.
NYNJ-inspired broadcast branding. No backend — everything runs in the browser.

## The format

- **48 teams** across **6 seeded pots of 8**
- **8 players**, **6 teams each** — exactly one team from every pot
- **Snake draft** — order randomised once, then alternates direction each
  round (1→8, 8→1, 1→8…) so going first isn't a permanent advantage
- One pot drawn per round, six rounds total — perfectly balanced
- Draw goes live at **19:30 UK time** today (deterministically seeded so
  every viewer sees the identical draw)

## Pots

| Pot | Teams |
|-----|-------|
| 1 — Favourites  | France, England, Brazil, Argentina, Spain, Portugal, Germany, Netherlands |
| 2 — Contenders  | Norway, Belgium, Colombia, Japan, Morocco, USA, Uruguay, Switzerland |
| 3 — Challengers | Türkiye, Mexico, Croatia, Ecuador, Sweden, Senegal, Canada, Austria |
| 4 — Dark Horses | Paraguay, Scotland, Bosnia & Herzegovina, Ivory Coast, Egypt, Czechia, Ghana, Algeria |
| 5 — Outsiders   | South Korea, Tunisia, Australia, Iran, DR Congo, South Africa, Saudi Arabia, Qatar |
| 6 — Wild Cards  | Panama, Uzbekistan, New Zealand, Iraq, Curaçao, Cape Verde, Jordan, Haiti |

## Features

- Live countdown with a **"Remind me 5 min before"** button (downloads a
  calendar .ics with a built-in 5-minute alarm — works on iPhone, Android,
  desktop)
- Dramatic spin-and-reveal for each pick, with sound (drumroll, stinger,
  fanfare) and confetti
- Live feed ticker + live-updating squad power rankings
- One-line commentary per pick
- PNG export and copy-as-text of the final board
- Replay button to re-run the whole draw
- Keyboard: Space/Enter advances a pick, M toggles mute
- Reduced-motion and mobile/TV-cast friendly

## Deploying to Vercel

Single static HTML file, no build step.

1. Push `index.html`, `vercel.json`, `.gitignore`, `README.md` to a GitHub repo
2. Vercel → Add New → Project → import the repo
3. Framework Preset: **Other** · Build Command: empty · Output Directory: empty
4. Deploy, share the URL

## Changing the draw time

In `index.html`, find `getDrawTimestamp()`. It targets **18:30 UTC**
(= 19:30 BST). Change the hour/minute (in UTC) if needed.

## Changing players or teams

Edit the `PLAYERS` array or `POTS` object near the top of the `<script>`.
The deterministic seed means refreshing won't reshuffle, but changing the
players or the date will change the order accordingly.
