Built a live-simulating ops dashboard (FastAPI + Motor + React + Recharts) showcasing pipeline scheduling, run history, KPIs, system health metrics, anomaly feed, incident/RCA log, and a terminal log stream — all matching the résumé's data-engineering scope.
Backend auto-seeds 8 cron jobs, 120 runs, 3 incidents (with full root-cause docs), 200m of metrics, anomalies, and logs; a 5-second simulation loop keeps the UI live (new metrics, logs, triggered runs, auto-raised anomalies on failures).
Testing: backend testing subagent wrote a 19-test pytest suite — 19/19 PASS. One critical ObjectId-leak bug on POST trigger + POST incident-from-anomaly was caught & fixed during testing. Frontend verified via screenshot; no frontend testing was requested

<img width="1056" height="691" alt="datapipeline" src="https://github.com/user-attachments/assets/62782f67-5dd2-4569-8d1c-567edd111332" />

<img width="1037" height="710" alt="Screenshot 2026-04-23 152426" src="https://github.com/user-attachments/assets/2c4c7759-a78f-4ff2-85a0-4cb943818288" />

<img width="1059" height="688" alt="datapipeline2" src="https://github.com/user-attachments/assets/2d8f72f8-10ad-41cc-abeb-4866c2e290e6" />
