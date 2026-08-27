# Lahore · AirTrack

Street-level AirTrack for Lahore. Default view is a rolling **GEOS-CF analysis
+ forecast** window run through Global/RoW v1.3. January and June 2026 remain
as typical-day archives.

**Live:** https://air-aware-labs.github.io/lahore-air/

The field is the model. Sensors are not assimilated and do not drive the
forecast. An optional city-wide `--regional-scale` can be applied at build
time if a regional bias has been diagnosed separately; it is off by default.

Rebuild from `../lahore-briefing`:

```
./run_live.sh
```

Showcase, not a scorecard.
