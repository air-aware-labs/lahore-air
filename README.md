# Lahore · AirTrack

A private demonstration of AirTrack's rolling Lahore background field and
street-to-street layer, with frozen January and June views for comparison.

The existing GitHub Pages URL follows `main` and is not the reviewed branch.
Until PR #1 is merged or the Air Aware Labs route is deployed, run this branch
locally instead:

```sh
python3 -m http.server 8765
```

Then open <http://localhost:8765/>.

## Page contract

- `index.html`, logos, Leaflet and the January/June archive are fixed release
  assets.
- `current.json` points to one immutable live run when hosted. The checked-in
  version has an empty prefix for a clean flat-layout review.
- A scheduled run changes only `live.json`, `streets.json` and `fields/live/`,
  then promotes the pointer last.
- The first view stays sparse. Seasonal evidence and model details belong in
  the technical handoff, not in a paragraph over the map.
- The page remains `noindex,nofollow`.

## Model contract

The Global/RoW v1.3 background supplies the city field. Hyperlocal v2.11 is
used as a city-median-normalised relative street factor over all 82,090 source
segments; 29,928 render as 43,785 clipped polylines.

Sensors are not assimilated and are not a street-resolution gate. Detailed
feature coverage, acceptance checks and the Stadium Twin-style deployment plan
live in `will-projects` PR #19.
