# TBM AI Safety System

## Introduction
TBM AI Safety System is an AI-powered Tool Box Meeting (TBM) platform
designed for construction sites. It streamlines daily safety briefings,
verifies worker comprehension through LLM-based evaluation, and enables
real-time anonymous hazard reporting — all optimized for multilingual
construction workforces.

## Key Features
- QR-based worker check-in and multilingual TBM delivery
- LLM-powered comprehension scoring (pass threshold: 70/100)
- Rule-based safety evaluation per hazard type (6 hazard categories)
- Mandatory safety re-education flow for workers who do not pass
- AI-generated additional safety instructions based on daily work type combinations
- Anonymous hazard signal reporting with LLM auto-mapping
- Manager review queue for hazard reports with TBM feedback loop
- Multi-stage LLM hazard mapping (worker package → admin candidate → new hazard)
- Admin dashboard with worker status tracking and completion management

## Hazard Rule Categories
1. Temporary Stairs
2. Scaffolding & Work Platforms
3. Welding & Cutting
4. Suspended Scaffold (Dalbi-gye)
5. Formwork Systems (Gang Form / Slip Form / Climbing Form)
6. Formwork & Shoring (Geupujib & Dongbari)

## How It Works
1. Admin sets up the daily TBM package and selects active work types
2. Workers scan QR code and receive TBM briefing on their device
3. Workers complete a comprehension check (scored by LLM)
4. Workers scoring 70+ receive AI-generated additional safety instructions
5. Workers scoring below 70 are directed to a mandatory safety re-education flow
6. After re-education, workers can submit anonymous hazard signal reports
7. Reports are auto-mapped by LLM and escalated to admin when thresholds are exceeded
8. Admin reviews new hazard candidates and approves them for the next TBM cycle

## Anonymous Hazard Reporting Flow
1. Worker taps "Report Hazard Signal" button on the main screen
2. Worker submits a free-text hazard description (anonymous)
3. LLM performs 3-stage auto-mapping:
   - Stage 1: Match against worker's own package
   - Stage 2: Match against admin-configured package candidates
   - Stage 3: Classify as new hazard candidate
4. Admin reviews report + LLM mapping result
5. Admin selects: Guide / Exclude / Hold
6. Approved hazards are registered and reflected in the next TBM

## Tech Stack
- Frontend: React Native (iOS / Android)
- Backend: Supabase (PostgreSQL + Auth + Realtime)
- AI/LLM: Google Gemini API via Google AI Studio
- STT: Speech-to-Text for voice input support
- Deployment: TBD

## Database Overview
- `tbm_sessions` — daily TBM sessions per site
- `worker_sessions` — individual worker check-in records
- `evaluation_results` — LLM scoring results per worker
- `hazard_reports` — anonymous worker hazard submissions
- `hazard_report_mappings` — LLM auto-mapping results
- `hazard_report_reviews` — admin review decisions
- `hazard_report_stats` — cumulative stats per package with alert thresholds

## Versioning
- v13: Core TBM flow + rule-based evaluation
- v13-1: Safety re-education flow with resume/pause support
- v14 (current): AI-generated additional instructions + anonymous hazard reporting

## License
MIT License
