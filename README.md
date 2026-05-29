# Stallions Bush Scrims — COD Coach Analytics Report

A static coach-facing analytics report for Call of Duty scrim data.

This project turns raw Call of Duty match exports and an aggregate stats JSON file into a narrative-style coaching report focused on team performance, slaying impact, pressure, efficiency, win/loss patterns, player roles, and searchable raw player stats.

Live site:

https://bush-ai.github.io/stallions-bush-scrims-1/

---

## Purpose

This is a proof-of-concept for showing how raw Call of Duty export data can be converted into something useful for a coach.

The goal is not just to display stats. The goal is to help a coach quickly answer questions like:

- Who is slaying well?
- Who is creating pressure?
- Who is staying efficient?
- Who is dying too much relative to their impact?
- What changes between wins and losses?
- Which mode or map needs review?
- How do the team’s players compare to the rest of the lobby?

The report is designed to be coach-friendly, narrative-first, and supported by searchable stats.

---

## Team of Interest

The main team being reviewed is:

- SkiL
- Manny
- Swooty
- Okis

Opponent and lobby data are included for context, but the primary report focuses on this roster.

---

## What the Report Includes

### Coach Narrative Summary

A high-level written overview of team performance, including:

- Overall record
- Mode performance
- Team slaying trends
- Pressure and efficiency notes
- Key coaching questions

### Team Snapshot

Quick stat cards for important team-level metrics such as:

- Overall record
- Hardpoint record
- Overload record
- Team K/D
- Damage per game
- Non-traded kill percentage
- Win/loss performance differences

### Player Slaying Snapshot

A coach-focused table for the main roster, including:

- Kills per game
- Deaths per game
- Assists per game
- K/D
- KA/D
- Damage per game
- Damage per kill
- Non-traded kill percentage
- Average highest streak
- Suggested role label

### Player Narrative Cards

Each player gets a short coaching read with:

- Role label
- Key strengths
- Watch-out
- Coaching question
- Supporting stats

Example player roles may include:

- Main Slaying Anchor
- Stable Slayer
- Pressure Player
- Support / Objective Hybrid
- Efficiency Contributor
- Entry / Risk Player

### Win vs Loss Review

Compares player and team performance in wins versus losses.

This helps identify whether losses are connected to:

- Lower slaying output
- More deaths
- Lower damage pressure
- Poorer efficiency
- Objective or conversion issues

### Mode Review

Compares performance between game modes such as:

- Hardpoint
- Overload

The report stays slaying-focused but uses objective data as supporting context.

### Opponent / Lobby Context

Includes lightweight comparison against the rest of the lobby, such as:

- Full lobby K/D ranking
- Full lobby damage ranking
- Top opposing slayers
- Team vs opponent comparison

### Searchable Raw Stats Table

Includes a searchable and sortable table for all players across all games.

Common fields include:

- Game / match number
- Mode
- Map
- Team
- Player
- Result
- Kills
- Deaths
- Assists
- K/D
- KA/D
- Damage
- Damage per kill
- Non-traded kills
- Non-traded kill percentage
- Highest streak
- Objective fields when available

---

## Project Structure

```text
.
├── index.html
├── assets/
│   ├── index-*.js
│   └── index-*.css
├── data/
│   └── cod-coach-aggregate-stats.json
├── .github/
│   └── workflows/
│       └── deploy.yml
└── README.md
```

---

## Data Flow

The intended data flow is:

```text
Raw COD exports
        ↓
Aggregate stats JSON
        ↓
Static website
        ↓
Coach narrative report + searchable stat tables
```

The aggregate JSON is the main source for the narrative report.

The raw match/player data can be used for detailed stat tables and future drill-downs.

---

## Deployment

This project is deployed with GitHub Pages using GitHub Actions.

The workflow is located at:

```text
.github/workflows/deploy.yml
```

The deployment publishes the repository root directly as a static site.

No server is required.

No backend is required.

No database is required.

---

## GitHub Pages Setup

In GitHub, go to:

```text
Settings → Pages
```

Set:

```text
Source: GitHub Actions
```

Then push changes to the `main` branch.

The workflow will deploy the site automatically.

---

## Local Development

Because this is a static site, you can open `index.html` directly in a browser for basic review.

However, if the site loads JSON with `fetch`, use a local static server instead.

Example using Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

---

## Updating the Report Data

To update the report with new stats:

1. Generate or update the aggregate JSON file.
2. Place it in the `data/` folder.
3. Make sure the JavaScript points to the correct file path.
4. Commit and push the changes.
5. GitHub Actions will redeploy the site.

Recommended path:

```text
data/cod-coach-aggregate-stats.json
```

---

## Notes

This is a proof-of-concept, not a full analytics platform.

The current goal is to show that raw COD exports can be transformed into a useful coach review.

Future improvements could include:

- More visual charts
- Map-specific breakdowns
- Player trend lines
- Uploading new stat exports directly
- Automated aggregate generation
- Match-by-match drill-downs
- Role-based player comparisons
- Exportable PDF coach reports

---

## Built With

- HTML
- CSS
- JavaScript
- GitHub Pages
- GitHub Actions

---

## Report Philosophy

This project is designed to avoid being a simple stat dump.

The best coaching value comes from combining stats with interpretation.

Instead of saying:

> Player X had a low K/D.

The report should say:

> Player X created pressure, but their death rate suggests film review should focus on whether those deaths were productive entry deaths or avoidable early picks.

The report should use careful language such as:

- suggests
- appears
- may indicate
- worth reviewing
- the data points toward

This keeps the report useful without overclaiming from a small dataset.
