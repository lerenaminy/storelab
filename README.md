# StoreLab · Café v0.1

Imagine your store. Build it. Test it.

A desktop-first café layout editor and exploratory operations simulator, in Traditional Chinese. Plain HTML/CSS/JavaScript, no dependencies, no secret keys, no server required. GitHub Pages compatible.

## Run

```sh
npm run dev
# http://localhost:4173
npm run check
npm test
```

## Use

Describe dimensions/area and seats, or enter them manually. Review assumptions, then create the layout. Add furniture and equipment; drag objects in 2D, use the inspector to resize/rotate/delete. Keyboard: focus an object, arrow keys move 0.25 m, R rotates, Delete removes. The isometric view is read-only.

Choose a scenario, adjust inputs and run. Replay sampled customer states; seek the timeline or enable path heat. Save two snapshots and compare with identical current parameters and demand seed. Save projects to this browser, and export JSON backups for other devices. No account or cloud project storage is included.

Research/assumption drawer is part of the product. Walk-in time is arrival-to-handoff; delivery time starts at remote order and includes courier travel after drink readiness. Average/P90 exclude unfinished/blocked orders, which are counted separately. Seat utilization includes reserved seats during the arrival window. Simulations start empty and drain for up to 120 extra minutes. Heat is movement sampling, not certified crowd density.

## What is implemented, and what is next

Implemented: metric editing, collision/boundary checks, drag and keyboard controls, 8 object types, three scenarios, seeded demand, resource-constrained queues, obstacle routing, dine-in/takeaway/delivery journeys, playback, heat, A/B comparisons, local projects, JSON import/export, provenance and release workflow.

Local natural-language generation is a small rule parser + template, clearly labeled. The assistant supports adding furniture/plants and moving counter/pickup/merchandise near entry. It is not a hosted LLM. Full managed generative AI is deferred to v0.3; no AI key is embedded in the public website.

Optional own AI endpoint: enter an HTTPS URL in the workbench. On explicit generation request, the app POSTs `{brief,layout,request}` as JSON. The endpoint must support browser CORS and return `{layout:{name,width,height,objects:[{id,type,x,y,w,h}]},assumptions:string[]}`. Types are in engine.js. Output is validated and shown for review. The app doesn't collect/store an API key or call an external AI provider by default. Endpoint integration needs a user's own tested backend and has not been verified with a live model.

Known scope: one person/one beverage, two-seat table units, approximate body clearance, fixed customer walking speed, static shortest paths, overlap permitted between people waiting, simple uncalibrated local walking delay, no staff walking, no abandonment, no groups, no cleaning, no costs/revenue or compliance assessment. These make this an experiment tool, not a reliable operational forecast. Research-backed reference does not imply measured café parameters.

## Deployment

Repository: https://github.com/lerenaminy/storelab
Target: https://lerenaminy.github.io/storelab/

`.github/workflows/pages.yml` checks and tests before deploying every push to main. Enable Settings → Pages → Source: GitHub Actions for that workflow. If the connected GitHub installation cannot write workflow files, use the built-in Pages branch deploy instead: main / (root), using the included `.nojekyll`. Either path serves relative assets under /storelab/ correctly. Do not add secrets to the repository. Future versions update the same URL.

## Documentation

- [Product definition, behavior contracts and roadmap](docs/PRODUCT.md)
- [Parameter evidence and calibration plan](docs/RESEARCH.md)
- [Release history](CHANGELOG.md)
- [Verification record](docs/QA.md)
