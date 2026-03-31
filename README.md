The first MLB analytics-engine built for the new  2026  ABS  era. 

Measures umpire strike-zone-bias that survives the 2026 Automated Ball-Strike correction filter — the signal every legacy model missed.

The Problem: 
Every existing umpire analytics tool — Covers, Baseball Cube, UmpScorecards, FantasyGuru — measures historical called-zone behavior. That data is now structurally obsolete.

On Opening Day 2026, Major League Baseball introduced the Automated Ball-Strike (ABS) Challenge System. For the first time in the sport's history, players can challenge a home-plate umpire's ball-or-strike call and have it 
reviewed by Hawk-Eye cameras in under two seconds. This changes everything. An umpire with a historically tight zone still has a tight zone — but now batters can correct borderline calls. Each team gets exactly two 
challenges per game; once they're gone, the umpire's influence grows in late innings for depleted teams. Some teams are measurably better at challenging than others — a team winning 65% of challenges extracts far more 
value from the system than one winning 31%.

No existing public model accounts for any of this. StrikeZoneIQ was built from the ground up for the world that began on March 25, 2026.

What StrikeZoneIQ Does:
For every MLB game on the daily slate, the model answers one question: given who is behind the plate, how each team is managing their ABS challenges, what ballpark they are playing in, and what the weather is doing — 
what is the true expected run environment, and where does the market misprice it?

The model runs four parallel input heads. Head 1 measures umpire zone distortion that survives the ABS correction filter — the bias on the 95%+ of pitches never challenged. Head 2 tracks live challenge inventory per team 
and flags late-inning walk risk when a team's backstop is depleted. Head 3 scores each team's ABS decision quality by role — batter, pitcher, catcher — and adjusts strikeout and walk projections accordingly. Head 4 
multiplies umpire bias against park run factors and live wind conditions into a single compound run-environment scalar. All four head embeddings feed a fusion layer that outputs: fair total, over probability, market gap, 
edge percentage, quarter-Kelly stake, confidence tier (H/M/L), K/walk prop flags, and live depletion alerts.

Why Now:
The ABS data didn't exist before Opening Day 2026. Every model trained on pre-2026 data is answering the wrong question. StrikeZoneIQ has a first-mover advantage that compounds daily as the season progresses and 
per-umpire sample sizes grow. The model improves automatically. Run Section 3 daily and Section 4 weekly.

Target Audiences:
MLB organizations for umpire performance analytics and ABS system optimization. Licensed sportsbooks and prediction markets for totals line efficiency research. Sports media for data-driven game previews and umpire 
tendency reporting. Independent analysts and researchers — open methodology, reproducible results.

Regulatory Compliance:
On March 19, 2026, MLB named Polymarket its exclusive Official Prediction Market Exchange and simultaneously signed a landmark Memorandum of Understanding with the Commodity Futures Trading Commission — the first such 
agreement between a professional sports league and a federal regulatory agency. A key component of the partnership includes working together to restrict markets that present an integrity risk to MLB, such as individual 
pitches, manager decisions, and umpire performance. These restrictions are binding on all brokers operating through Polymarket's U.S. Rulebook. StrikeZoneIQ was designed from the ground up with these restrictions in mind. 
The model predicts game-level run totals only — a standard, fully legal market available on every licensed sportsbook and prediction platform. The model does not predict individual pitch outcomes, manager decisions, or 
umpire call-by-call performance, all of which are explicitly restricted. Umpire and ABS data are used exclusively as inputs to a game-level run environment model — not as direct prediction targets. The distinction is 
material and intentional. All data sources are publicly available. No proprietary MLB data feeds, no Sportradar licensing, no restricted Hawk-Eye raw data access. Prediction markets fall under the regulatory jurisdiction 
of the CFTC as Designated Contract Markets. StrikeZoneIQ produces analytics outputs, not prediction market contracts. This compliance statement reflects the regulatory environment as of March 2026. Users should monitor 
the Schiff-Curtis legislation and any subsequent CFTC rulemaking.

Data Sources:
MLB Stats API — schedule, umpire assignments, live challenge inventory (free/public). Baseball Savant/Statcast — pitch-by-pitch ABS challenge log and zone coordinates (free/public). Odds API — live Over/Under lines and 
line movement (paid, the-odds-api.com). OpenWeatherMap — pre-game weather at each venue (free tier sufficient). FanGraphs — park run factors, three-year average (free/public).

Architecture:
Six Python source modules in the ingestion package handle resilience primitives, the MLB Stats API client, Baseball Savant scraper, weather client, feature engineering, and model architecture. One master Jupyter notebook 
(.ipynb) contains all five pipeline stages. 64 tests across two test files — all passing.

Getting Started:
Requires Google Colab (free tier works, T4 GPU recommended), an Odds API key from the-odds-api.com, and an OpenWeatherMap key (free tier). Clone the repository, upload py_files_nb3.zip to Colab, open the master notebook, 
paste your API keys in Setup Cell 1, and Runtime → Run all. Run Section 3 daily before first pitch, Section 4 weekly for retraining, Section 6 anytime for backtesting.

Model Performance:
The model reaches statistical significance around late May 2026 when per-umpire ABS pitch counts consistently exceed 100 unchallenged pitches. Early-season outputs carry confidence=L. Expected MAE drops from ~6.0 on 
opening week to ~2.0 by late May to ~1.5 at full season scale. AUC improves from undefined early to ~0.65 or better with a full season of data.

Code Standards:
Google Python Style Guide compliant throughout. Full type annotations, Google-format docstrings, pylint-clean, pytest with 80%+ coverage enforced.

License:
MIT License. Data sourced from publicly available APIs. Users are responsible for compliance with applicable terms of service and regulations in their jurisdiction.

Intellectual Property:
The StrikeZoneIQ name, branding, visual identity, whitepaper content, methodology documentation, and the specific selection, coordination, and arrangement of data inputs and model outputs are original creative works 
protected under U.S. copyright law. Copyright 2026 StrikeZoneIQ. All rights reserved. Raw statistical facts — individual pitch coordinates, game scores, challenge outcomes — are not copyrightable. The StrikeZoneIQ model 
architecture, feature engineering methodology, ABS residual bias computation, compound adjuster formula, fusion layer design, and all documentation, branding, and UI/UX are original works and are protected.

Terms of Service — Key Restrictions:
Access to StrikeZoneIQ outputs, APIs, and data feeds is governed by the StrikeZoneIQ Terms of Service. Key restrictions include: Users and licensees are expressly prohibited from using StrikeZoneIQ outputs, predictions, 
feature vectors, model scores, or any derivative thereof to train, fine-tune, validate, or benchmark any competing or independent machine learning model, statistical model, or algorithmic system without express written 
consent. Users are expressly prohibited from scraping, harvesting, bulk-downloading, or systematically extracting StrikeZoneIQ data outputs through automated means without a commercial API license. Redistribution of 
StrikeZoneIQ predictions or outputs in any commercial product or service without a valid licensing agreement is prohibited. The StrikeZoneIQ methodology, architecture documentation, and whitepapers may not be reproduced, 
republished, or adapted without attribution and written permission. Full Terms of Service available upon commercial licensing inquiry.

StrikeZoneIQ v2.0-alpha — 2026 MLB Season — Built for the new ABS era
