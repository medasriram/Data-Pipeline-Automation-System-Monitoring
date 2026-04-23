
Action: file_editor create /app/memory/PRD.md --file-text "# PRD — Data Pipeline Automation & System Monitoring (Ops Control Room)

## Original problem statement
Data Pipeline Automation & System Monitoring 2025 — Python, Bash, SQL, Linux, Pandas, Matplotlib, Jupyter.
- Engineered and maintained automated data pipelines on Linux using Python and Bash scripting; scheduled jobs via cron and monitored execution logs to detect anomalies proactively.
- Applied structured root-cause analysis to detect and resolve data anomalies; produced incident logs and resolution documentation, reducing recurring pipeline failures and improving reliability.
- Designed system monitoring dashboards to track KPIs and operational health metrics, simulating enterprise-grade monitoring workflows in a production-like environment.

## What this app is
Single-page ops \"Control Room\" dashboard that simulates an enterprise-grade data pipeline platform. It demonstrates every capability from the résumé bullet (scheduling, monitoring, anomaly detection, RCA incident logging, KPI dashboard).

## Architecture
- **Backend**: FastAPI + Motor (async MongoDB) + asyncio background simulation loop. All endpoints under `/api`.
- **Frontend**: React + Recharts + Lucide icons. Dense \"Control Room\" grid-borders layout, IBM Plex Mono/Sans, status-driven color system (red/amber/green).
- **Storage**: MongoDB — collections: `jobs`, `runs`, `metrics`, `anomalies`, `incidents`, `logs`.
- **No external integrations** (no auth, simulated data).

## User personas
1. **SRE / Data Engineer** — reviews job health, triggers reruns, investigates failures.
2. **Engineering Manager** — scans KPIs, open incidents, uptime.
3. **Portfolio viewer / recruiter** — inspects a demo showcasing ops/data-engineering skills.

## Core requirements (static)
- Cron-scheduled pipeline jobs with manual trigger + enable/disable
- Run history with exit code, rows processed, duration, error message
- Live KPI summary (success rate, anomalies, incidents, jobs enabled, etc.)
- Real-time system-health metrics (CPU/Mem/Disk/Net/Load) with 60m time-series
- Anomaly feed with severity; ack + escalate-to-incident
- Incident log with structured RCA + resolution workflow
- Time-series pipeline throughput chart (stacked success/failed per hour)
- Live terminal log stream (tail-f style)

## What's been implemented — 2026-01-23
- **Backend** (`/app/backend/server.py`):
  - 17 endpoints covering all surfaces listed above.
  - `seed_once()` bootstraps 8 jobs, 120 historical runs, 3 incidents (incl. full RCAs), 200 minutes of metrics, 4 anomalies, 60 log lines.
  - `simulation_loop()` runs every 5s: generates a new system metric + log line, fires a simulated pipeline run every ~30s, raises new anomalies periodically, auto-trims collections.
  - `_execute_job_run()` produces realistic runs (Gaussian duration, ~12% failure rate) and auto-raises anomalies on failure.
- **Frontend** (`/app/frontend/src/App.js` + `App.css`):
  - Top bar with live clock, uptime, refresh.
  - 6-up KPI band (runs 24h, success rate, avg duration, active anomalies, open incidents, jobs enabled).
  - Pipeline Jobs table with trigger/toggle buttons.
  - Pipeline Run History table with color-coded status & errors.
  - Throughput bar chart (24h, stacked).
  - System Health panel (4 live metric cells + 60m line chart).
  - Anomaly Feed with ack + create-incident actions.
  - Incidents table + drawer editor for RCA / resolution / status.
  - Live Log Stream (terminal styled).
  - Footer with service status summary.
  - Auto-refresh every 5s.
- **Testing**: Backend testing subagent wrote `/app/backend/tests/test_pipeline_ops.py` — 19/19 passing. Fixed one critical ObjectId leak on POST trigger & incident-from-anomaly.

## Test credentials
None — no auth in this app.

## Prioritized backlog
- **P0**: none (MVP complete & green).
- **P1**: persistence of simulation state across backend restarts (currently re-seeds only if empty — safe); richer Anomaly detail pane with run-level drilldown.
- **P2**: downloadable RCA markdown export; Jupyter-notebook style ad-hoc analysis panel; multi-environment selector (prod/stage); basic auth (JWT or Emergent Google OAuth); webhook/Slack integration on incident-open.

## Next tasks
- User acceptance / iteration based on feedback.
- Optional: deploy, add auth, wire to a real Prometheus/Postgres source.
"
Observation: Create successful: /app/memory/PRD.md
