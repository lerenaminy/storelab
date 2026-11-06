# Verification record · v0.1 · 2026-11-06

## Automated
`npm run check` and `npm test`: passed. Nine engine tests cover seeded reproducibility, full baseline completion, dine-in/seat/pickup/return and takeaway separation, delivery bypassing cashier, no-seat conversion, shared staffing/equipment capacity, walking-speed sensitivity without changing demand, obstacle routing, and invalid/blocked layout handling.

## Browser verification
Checked in the Codex browser at the narrow default viewport (474 px) and a temporary desktop viewport (1440 × 1000). Narrow layout stacks the workbench, simulator and library; desktop shows three columns.

Observed: default brief → explicit assumptions → valid 10 × 6 m / 12-seat draft; object selection and numerical position editing; 90° pickup rotation; added plant; snapshots A/B; same-seed comparison; save project and reopen after reload; weekday and morning-rush runs; seek to 20/25 minutes; customer states visible; heat overlay visible. Browser testing found and corrected SVG accessibility (interactive objects were hidden by role=img), a template seat-capacity issue, and scenario label consistency on project load.

Example outputs are model experiments, not real café measurements: baseline 60-minute demand with seed 42 generated 30 orders and completed 30; the high-volume test generated 75 and completed 75 including drain time. Never treat those sampled counts as a deterministic rate or evidence of prediction accuracy.

## Verification limits
No field validation, 5–8 participant usability study, measured café calibration, independent uncertainty analysis, or live external AI endpoint verification yet. JSON backup handlers have validation but file-picker roundtrip has not been manually verified. Pointer drag is implemented; numerical movement, rotation and selection were verified in the browser, with no separate pointer-trajectory regression test.

## Release
Source committed to https://github.com/lerenaminy/storelab . GitHub Pages configured for GitHub Actions. Initial deployment was blocked before starting because GitHub reported an account billing lock. The user asked to retry. Attempt #2 also failed before execution with the same billing-lock message. Pages source setting was saved successfully; public deployment remains unverified and blocked by the GitHub account. Run: https://github.com/lerenaminy/storelab/actions/runs/42178021198 .
