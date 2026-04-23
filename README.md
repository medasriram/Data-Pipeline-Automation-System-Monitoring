Built a live-simulating ops dashboard (FastAPI + Motor + React + Recharts) showcasing pipeline scheduling, run history, KPIs, system health metrics, anomaly feed, incident/RCA log, and a terminal log stream — all matching the résumé's data-engineering scope.
Backend auto-seeds 8 cron jobs, 120 runs, 3 incidents (with full root-cause docs), 200m of metrics, anomalies, and logs; a 5-second simulation loop keeps the UI live (new metrics, logs, triggered runs, auto-raised anomalies on failures).
Testing: backend testing subagent wrote a 19-test pytest suite — 19/19 PASS. One critical ObjectId-leak bug on POST trigger + POST incident-from-anomaly was caught & fixed during testing. Frontend verified via screenshot; no frontend testing was requested

