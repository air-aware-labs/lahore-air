# Lahore · AirTrack

**When the air turns, and which streets carry it.** A rolling GEOS-CF analysis
+ forecast window run through AirTrack's Global/RoW v1.3 background model, with
the AirTrack hyperlocal v2.11 street layer on top. January and June 2026 remain
as frozen typical-day archives.

**Live:** https://air-aware-labs.github.io/lahore-air/

## What this is, and is not

Modelled hourly from NASA GEOS-CF. **Not a measurement.** Neighbourhood sensors
are not assimilated and do not drive the forecast; on the January and June
archives they are shown as measurements, labelled as such.

The street-layer acceptance tests are spatial and physical, not sensor based:

- **Continuous street variation.** Residential roads alone have a median
  within-hour p95/p05 factor spread of 1.083, so this is not a road-class
  colouring rule.
- **Major-road direction.** Motorway and primary medians exceed residential
  medians in all 24 shipped diurnal slices (minimum ratios 1.066 and 1.033).
- **Coverage.** The model evaluates all 82,090 OSM source segments. The packer
  selects the longest 30,000 non-service segments; 29,928 remain after clipping
  to the field and render as 43,785 short polylines, each taking its background
  value from a single 500 m cell.

Known limits are stated rather than hidden:

- **Transfer.** Hyperlocal v2.11 was trained in London. Here it is run inside
  its training envelope and used only as an hour-normalised relative factor;
  this is a showcase transfer, not a Lahore calibration.
- **Road hierarchy.** Secondary roads remain a known exception: their median
  factor is slightly below residential in 23 of 24 slices. Motorway and primary
  directionality passes; a complete class ordering does not.
- **Background field.** Street colour is a relative modulation on the 500 m
  Global/RoW field — which streets are worse than their neighbours this hour,
  not what a monitor at the kerb would record.

Sensor comparison is an optional background-field diagnostic only. It is not a
street-layer gate and is off by default in the unattended rebuild.

## Rebuild

From `../lahore-briefing`:

```
./run_live.sh
```

Preflight → fetch → field → streets → pack → publication gates. Exit 9 means
there is no newer GEOS-CF cycle than the published one. Set `SCORE_SENSORS=1`
only when an optional background comparison is wanted. Nothing is committed or
pushed.

Showcase, not a scorecard.
