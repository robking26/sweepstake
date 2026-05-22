# The Sweepstake — 2026 World Cup

A live-draw site for an eight-person, six-teams-each World Cup sweepstake.

## The format

- **48 teams** across the four official FIFA seeding pots
- **8 players**, **6 teams each**
- **Pot-based snake draft** — order is randomised once, then alternates
  direction each round (1→8, 8→1, 1→8…) so going first isn't a permanent
  advantage
- Pots are drawn through in order, so every player ends up with a balanced
  spread of seeds, mid-tier sides, and dark horses
- The draw goes live at **16:00 UK time** today (deterministically seeded
  so every viewer sees the exact same draw)

## Pot composition

| Pot | Teams |
|-----|-------|
| 1   | Spain, Argentina, France, England, Brazil, Portugal, Netherlands, Belgium, Germany, USA, Mexico, Canada |
| 2   | Croatia, Morocco, Colombia, Uruguay, Switzerland, Japan, Senegal, Iran, South Korea, Ecuador, Austria, Australia |
| 3   | Norway, Panama, Egypt, Algeria, Scotland, Paraguay, Tunisia, Ivory Coast, Uzbekistan, Qatar, Saudi Arabia, South Africa |
| 4   | Jordan, Cape Verde, Ghana, Curaçao, Haiti, New Zealand, Sweden, Türkiye, Bosnia & Herzegovina, Czechia, Iraq, DR Congo |

## Pick distribution

Pots have 12 teams, divided across 8 players. The schedule:

| Round | Pot drawn from | Direction |
|-------|---------------|-----------|
| 1     | Pot 1 (×8)    | 1 → 8     |
| 2     | Pot 1 (×4) + Pot 2 (×4) | 8 → 1 |
| 3     | Pot 2 (×8)    | 1 → 8     |
| 4     | Pot 3 (×8)    | 8 → 1     |
| 5     | Pot 3 (×4) + Pot 4 (×4) | 1 → 8 |
| 6     | Pot 4 (×8)    | 8 → 1     |

Every player ends with 6 teams: roughly 1–2 from each pot.

## Deploying to Vercel

This is a single static HTML file. No build step.

1. Create a new GitHub repo and push these files:
   - `index.html`
   - `vercel.json`
   - `.gitignore`
   - `README.md`
2. In Vercel: **Add New → Project → Import** your repo
3. **Framework Preset**: leave as **Other** (Vercel will detect static)
4. **Build Command**: leave empty
5. **Output Directory**: leave empty (root)
6. Deploy

Vercel will serve `index.html` at the project root. Share the URL.

## Changing players or teams

Open `index.html` and edit the `PLAYERS` array or the `POTS` object near
the top of the `<script>` block. The deterministic seed means refreshing
won't reshuffle — but if you change the player list or the date, the draw
order changes accordingly.

## Changing the draw time

Look for `getDrawTimestamp()` in `index.html`. It targets **15:00 UTC**
(= 16:00 BST) of today. Change the `15` to a different UTC hour if needed.

## How the determinism works

All randomness uses a seeded PRNG (mulberry32) keyed off the draw's UTC
timestamp. Every viewer who loads the page sees the same pick order and
the same team in each slot. The spin animation is cosmetic — the result
is fixed from the moment the page loads.
