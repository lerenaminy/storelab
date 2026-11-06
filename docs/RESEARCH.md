# Parameter ledger · 2026-11-06

## Evidence and boundaries

**R1 — pedestrian reference, not café measurement.** Davidich & Köster (2013), *Predicting Pedestrian Flow*, PLOS ONE, DOI 10.1371/journal.pone.0083355. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0083355
The authors discuss the common 1.34 m/s mean and 0.26 m/s standard deviation from Weidmann; their own railway-station observations differed (morning mean 0.97 m/s). This is evidence that context matters, not a measured café distribution. StoreLab starts at 1.0 m/s, an explicitly chosen conservative placeholder; no universal café average is claimed. Model uses fixed user-selected speed per run; individual variability is deferred.

**R2 — external service benchmark, not preparation input.** Starbucks, 2025, *Back to Starbucks: Transforming our support organization*. https://about.starbucks.com/press/2025/back-to-starbucks-transforming-our-support-organization/
The company set a four-minute café wait goal. Its 2026-01-29 investor release reports peak café/drive-thru service below four minutes on average in fiscal Q1 2026: https://investor.starbucks.com/news/financial-releases/news-details/2026/Starbucks-Is-Back-Turning-Momentum-Into-Long-Term-Sustainable-Growth/default.aspx
StoreLab displays 240 seconds only as an external comparison. Public wording does not fully specify all start/stop timestamps; do not equate this with entry-to-handoff or a universal mean. Do not use 240 seconds as drink prep time or force simulation to meet it.

**R3 — process variability evidence.** Arnold et al. (2025), *An Analysis of Operational Processes in Coffee Shops Aimed at Improving Baristas’ Response to Highly-Customized Orders*, DOI 10.1177/10711813251369862. https://journals.sagepub.com/doi/full/10.1177/10711813251369862
Observational study across three differently organized shops. Timing cues differed between sites; customization and organization affect fulfillment. This supports separating workflows and calibration by shop. We do not transplant fitted equations or infer universal task durations.

## Explicit initial model inputs
| Parameter | Default | Status / calibration plan |
|---|---:|---|
| Walking speed | 1.0 m/s | Assumption informed by R1 context; measure unobstructed distance / time in target store |
| Ordering/payment | triangular 31.5 / 45 / 58.5 s | Assumption; observe start of customer interaction to payment complete |
| Brewed coffee preparation | triangular 42 / 60 / 78 s | Assumption, entire staff + machine task; not espresso extraction alone |
| Milk drink preparation | triangular 84 / 120 / 156 s | Assumption; ticket start to ready; includes milk and handoff prep |
| Menu mix | 40% brewed, 60% milk | Assumption; replace with POS order mix |
| Pickup interaction | 8 s | Assumption; ready customer reaches pickup to handoff complete |
| Dwell after returning | triangular 21 / 35 / 49 min | Assumption; measure occupied seat until departure |
| Merchandise browse | 15% probability, 20 s | Assumption; only active if merchandise exists |
| Arrival volume | weekday 24, rush 60, delivery peak 45 orders/h | Hypothetical scenarios, not observed demand |
| Takeaway share of walk-ins | 40% | Assumption; delivery excluded from denominator |
| Delivery share of all orders | 10% / 10% / 45% | Scenario assumption |
| Staff | 2 | One cashier + producer; one employee shares both tasks |
| Equipment capacity | 1 simultaneous drink per machine | Conservative abstraction, not real espresso group capacity |
| Seat unit | table + chairs 1.2 × 1.2 m / 2 people | Editable dimensions; approximate footprint |
| Clearance | 0.2 m body radius | Model assumption, not accessibility certification |
| Arrival process | exponential inter-arrival times | Assumption: constant-rate Poisson, no bursts/groups |
| Congestion delay | 0.25 s per nearby pedestrian per step | Uncalibrated local heuristic; capped, no physical pedestrian collision solver |

## Field experiment before claims
With store permission, collect anonymized timestamps for arrival, order start, payment end, preparation start, drink ready, pickup, seating and exit; record channel, drink category, staffing and layout. Record unimpeded walking segments with measured distances. Start with 30–50 orders per channel/time block as a pilot, then select sample size from observed variation. Split calibration and holdout sessions. Validate median/P90 waiting, throughput, queues and occupancy, not just averages. No faces or identifying data required. Publish error and uncertainty; investigate poor fits rather than tuning a single mean.

Revenue, rent, staffing cost, average order value, abandonment/patience, waste, machine breakdowns, groups, toilets, cleaning and regulatory clearance are needed for later commercial/operational planning. They are intentionally outside the first operational model. No financial profitability estimate appears in v0.1.
