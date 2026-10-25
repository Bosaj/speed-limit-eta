# Speed-Limit ETA

> Estimate journey time from the speed limits along a route, for roads where navigation apps have poor data.

**Status:** pre-alpha scaffold (no code yet). **Feasibility rating:** 3/10 — navigation apps already estimate ETAs; only useful where their data is weak.
**Idea:** #06 in the owner's ideas backlog. **Author:** Oussama Elhadji (`@Bosaj`) <oussousselhadji@gmail.com>.

---

## Problem

On some Moroccan rural and regional roads, ETAs are unreliable and speed-limit data is incomplete.

## Why build it (gap analysis)

Google Maps and Waze use live traffic, so a standalone tool needs a clear advantage: transparency (show the limit of each segment), a "legal-speed" ETA for fleets and driving schools, and community-added speed-limit signs where OSM is missing data.

## Prior art & open bases to fork

- [OSM Key:maxspeed](https://wiki.openstreetmap.org/wiki/Key:maxspeed) — How speed limits are tagged in OpenStreetMap.
- [Project-OSRM/osrm-backend](https://github.com/Project-OSRM/osrm-backend) — Fast routing engine on OSM data.
- [valhalla/valhalla](https://github.com/valhalla/valhalla) — Routing engine with costing models.
- [graphhopper/graphhopper](https://github.com/graphhopper/graphhopper) — Routing engine, Java.

## Proposed architecture

1. Route: OSRM or Valhalla on Morocco OSM extract.
2. Segment speeds: OSM maxspeed, else Moroccan default limits by road class, else community reports.
3. ETA: sum of segment length / speed, with a per-segment breakdown and a confidence score.
4. Contribute: photo of a speed sign, location and value, reviewed before export to OSM.

## Tech stack (proposed)

- Valhalla or OSRM (Docker)
- MapLibre GL web map
- PostGIS for community reports

## Roadmap

- v0.1 — Route + segment speed table for Morocco.
- v0.2 — ETA with confidence and breakdown.
- v0.3 — Community speed-sign reports.
- v0.4 — Fleet / driving-school mode.

---

## For LLM agents & contributors continuing this project

This repo is a **scaffold**: README + standard files, no implementation yet. If you are an AI agent asked to "continue developing", read this section first.

- Moroccan default limits by road class must come from the official Code de la route; cite it in code.
- Do not compete with live traffic ETAs; position as transparent "legal-speed" ETA.

**Ground rules:** keep this README in sync with reality as you build; prefer forking/reusing the bases above over greenfield code; write tests for anything correctness-critical; never commit secrets (see `.gitignore`); follow Conventional Commits (see `CONTRIBUTING.md`).

## Getting started

```bash
# nothing to run yet — this is a scaffold.
```

## 📄 License
**Proprietary & Commercial Software License** — All Rights Reserved © 2026 Oussama Elhadji (`@Bosaj`) <[oussousselhadji@gmail.com](mailto:oussousselhadji@gmail.com)>.

Unauthorized copying, distribution, resale, or reverse engineering is strictly prohibited. See [LICENSE](LICENSE) for full legal terms.
