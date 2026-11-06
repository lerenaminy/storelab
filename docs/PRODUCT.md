# StoreLab · Product definition v0.1

Decision record · 2026-11-06 · Approved direction: StoreLab is the platform; Café is the first scenario.

## Positioning
Imagine your store. Build it. Test it. Desktop-first exploratory physical-store planning, with mobile viewing. Audience: prospective café owners, existing small operators and curious learners. This is an educational scenario model, not a business forecast or building-code checker.

## First release contract
1. Start with a natural-language brief or dimensions, seats, décor and merchandise options. Review defaults explicitly. Local template generation works without a paid service; an optional user-controlled AI endpoint may return the same structured schema. Never represent template parsing as an LLM.
2. Edit a metric 2D floor: add, move, rotate, resize and delete tables, counter, pickup, entrance, equipment, merchandise and plants. Reject solid overlaps and out-of-bounds moves. Save locally; export/import JSON for portability. Table footprints include chairs; each table is two seats. Isometric view is a visual projection of the same data, not another simulation.
3. Run weekday, morning-rush and delivery-peak scenarios. Change arrival rate, staff, takeaway and delivery shares, walking speed, order time, drink times and dwell time. The same seed and settings generate the same demand for A/B comparison.
4. Show real model states and paths on the floor, replay speed/pause, queue, average and P90 arrival-to-handoff time, completed orders, seat utilization and blocked/no-seat outcomes.
5. Save snapshots and compare two layouts under the CURRENT identical scenario, seed and horizon. Report stochastic limitations, unfinished orders and definitions. Save input provenance with exported results.

## Customer journeys
- Takeaway: entrance → optional merchandise browsing → order/payment queue → order → pickup waiting zone → pickup handoff → exit.
- Dine-in: entrance → optional browsing → order/payment → find/reserve an available seat → seat while drink is made → pickup → return to reserved seat → dwell → exit. No seat: convert to takeaway, explicitly counted. One customer per order; no groups in v0.1.
- Delivery: order enters production remotely; courier appears when drink is ready → entrance → pickup → exit. Competes for production resources, never seats or cashier. Arrival-to-handoff includes production and courier travel; report channel separately.
- Staff: one cashier, remaining staff produce; a single staff member alternates cashier/production tasks, FCFS. Production constrained by both baristas and equipment count. No autonomous staff locomotion in this version.

## Spatial and simulation model
SI units. Axis-aligned rotated rectangles (90°). 0.25 m grid, 0.2 m body clearance around obstacles. BFS shortest path, four directions, no teleporting through walls. Service targets are accessible cells adjacent to the corresponding object. Seats use adjacent access cells. Entry is a portal, not an obstacle. Queue and waiting zones are floor markings. Local moving-agent occupancy adds a small stated delay; it is an uncalibrated heuristic, not a validated crowd model. Missing required objects or inaccessible endpoints prevent valid runs.

Hybrid discrete-event queues + fixed 0.5-second pedestrian integration. Seeded customer attributes independent of layout. One beverage per order, 40% brewed / 60% milk drink. Triangular service-time distribution, ±30% around a mode. Dwell ±40%. Arrivals exponential (stationary Poisson). One-hour arrival window, then up to two hours drain; report censoring. Replay samples every 5 simulated seconds. Occupancy measured during arrival window; service metrics include drained arrivals. No warm-up, so opening-hour bias applies.

## Parameter provenance
See RESEARCH.md. Research references, external benchmarks, and modeling assumptions must remain separate. All numerical inputs editable. A chair affects throughput only by footprint, path, congestion or seat capacity; there is no arbitrary layout score multiplier.

## UX direction
Warm off-white paper, evergreen ink, muted orange accents, subtle wood furniture. Three-column workspace: object library / spacious floor / simulation inspector. Clear active states, keyboard operation, visible empty/error/loading states. Guided creation and source drawer. Small-screen layout stacks panels. Results are exploratory and assumptions are always one click away.

## Release sequence and acceptance
- v0.1: editor, local persistence, deterministic executable café simulation, source ledger, replay and comparison, static GitHub Pages delivery.
- v0.2: field-calibrated parameters, 5–8 user task sessions, robust queue spatial packing, multiple replications / uncertainty intervals.
- v0.3: managed AI generation backend and validated partial edits, groups, staff routing, real menu workflows.
- Future: restaurant, retail, pop-up using scene + behavior contracts.

Usability targets (not yet achieved): first layout under 5 minutes; independently edit/rotate/delete; run two scenarios; save/compare A/B; explain assumptions. Automated verification targets: seed reproducibility, obstacle routing, queue capacity, channel journeys, shared resources, effect of speed, snapshot persistence. Browser verification checks visible interactions and responsive layout. No claim of real-world predictive accuracy before observed café validation.
