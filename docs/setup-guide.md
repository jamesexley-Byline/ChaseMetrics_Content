# Chase Metrics — Setup Guide

## Overview

Chase Metrics operates on a split architecture:

1. **The Agent (this repo)** — A Claude Code agent that maintains the Player Intelligence Database. It gathers data, flags changes, and pre-populates data blocks for editorial use. It runs in this repository.

2. **The Cowork Channel** — A Claude project where Chase Metrics operates in editorial mode. It reads the data the agent prepares, forms Byline's editorial positions, writes THE TAKE, and sets CONFIDENCE levels.

The database (`database/chase-metrics-database.md`) is the bridge between the two layers.

## Getting Started

### 1. Open the repo in Claude Code

Navigate to the `ChaseMetrics_Content` directory and open Claude Code:

```bash
cd ChaseMetrics_Content
claude
```

Claude will read `CLAUDE.md` and understand its role as the data agent.

### 2. Available Commands

Run these slash commands inside Claude Code:

| Command | What it does |
|---------|-------------|
| `/weekly-scan` | Full weekly maintenance sweep — news, ADP, flags, new entries |
| `/player-lookup [name]` | Pull current data for a specific player |
| `/content-gaps` | Find players with data signals but no published content |
| `/flag-review` | List all NEEDS REVIEW entries for triage |

### 3. Weekly Scan Schedule

The weekly scan is designed to run every **Monday at 08:00 UTC**.

During NFL season (September–January), a lighter mid-week check runs on **Thursdays at 08:00 UTC** for injury report updates.

To run manually at any time:
```
/weekly-scan
```

### 4. Workflow: Agent → Cowork Channel

1. Run `/weekly-scan` or `/player-lookup` in this repo
2. Review the generated reports in `reports/`
3. Bring the data blocks into the Chase Metrics Cowork channel
4. Form editorial takes in the Cowork channel
5. Update the database with finalised editorial sections

### 5. Key Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Agent instructions and database schema |
| `database/chase-metrics-database.md` | The single source of truth |
| `database/ranking-change-log.md` | Append-only change history |
| `reports/` | Generated data blocks and weekly summaries |
| `docs/chase-metrics-cowork-channel-prompt.md` | The editorial layer prompt for the Cowork channel |

## Rules

- The agent never writes to THE TAKE, CONFIDENCE, or CONTENT HISTORY
- Every change gets a log entry
- Conflicts are flagged as NEEDS REVIEW, not resolved by the agent
- The Cowork channel is the editorial authority
