# 1. Architecture

1. Route: OSRM or Valhalla on Morocco OSM extract.
2. Segment speeds: OSM maxspeed, else Moroccan default limits by road class, else community reports.
3. ETA: sum of segment length / speed, with a per-segment breakdown and a confidence score.
4. Contribute: photo of a speed sign, location and value, reviewed before export to OSM.

## Proposed stack
- Valhalla or OSRM (Docker)
- MapLibre GL web map
- PostGIS for community reports

## Open bases to fork
- [OSM Key:maxspeed](https://wiki.openstreetmap.org/wiki/Key:maxspeed) — How speed limits are tagged in OpenStreetMap.
- [Project-OSRM/osrm-backend](https://github.com/Project-OSRM/osrm-backend) — Fast routing engine on OSM data.
- [valhalla/valhalla](https://github.com/valhalla/valhalla) — Routing engine with costing models.
- [graphhopper/graphhopper](https://github.com/graphhopper/graphhopper) — Routing engine, Java.
