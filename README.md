# Wayanad Day 1 Dataset Bundle — SIH26191

## Source Verification Summary

| File | Source | Verified? | Notes |
|---|---|---|---|
| `wayanad_landslide_susceptibility.csv` / `.geojson` | KSDMA, extracted from NGDR-sourced Landslide-1.rar (doc.kml, layer ID `LS_WYD`) | ✅ Confirmed real, Wayanad-specific | 269 polygons: 110 High Hazard, 149 Medium Hazard, 10 Low Hazard |
| `wayanad_flood_susceptibility.csv` / `.geojson` | KSDMA, `Flood_KML.zip` → `Wayanad.kmz` | ✅ Confirmed real, Wayanad-specific | 63 polygons: 54 Flood plain, 9 Waterbody |
| `wayanad_dem_cop30.tif` | OpenTopography, Copernicus Global DSM 30m (COP30) | ✅ Confirmed correct extent | Bounds match requested box (75.77–76.44E, 11.45–11.98N); elevation range 1.4m–2234.7m, plausible for Wayanad plateau/hills |
| (not repackaged) `Flood-Probability-Report-2022_Final.pdf` | Kerala flood hazard probability study, 2022 | ✅ 427 pages, Wayanad-relevant pages: ~3, 21, 26, 415, 417, 421 (0-indexed) | Keep as reference PDF, cite, don't convert |
| (not repackaged) `Meppadi-Landslide-PDNA_...pdf` | Post-Disaster Needs Assessment, Meppadi/Wayanad landslide 2024, Govt. of Kerala | ✅ 647 pages, Wayanad content from page ~2 onward | This is your backtest event reference — keep as PDF |
| `National_Geospatial_Policy_2022.pdf` | Gazette of India, DST notification | ✅ Real, official | General policy context, not a data layer — cite only if discussing NGDR/data-sharing policy in your deck |

## What each processed file contains

- **CSV files**: one row per polygon — id, hazard/flood zone label, centroid lat/lon, vertex count, and original shapefile area/length attributes. Lightweight, good for quick lookups and joining to other tables.
- **GeoJSON files**: full polygon geometry with the same properties — this is what your model and mapping code should actually load (MapLibre, GeoPandas, etc).
- **wayanad_dem_cop30.tif**: raw elevation raster, EPSG:4326, ~30m resolution. Derive slope/aspect/curvature from this with GDAL or richdem.

## Attribution (keep this if you re-share any of this publicly)

- Landslide and flood susceptibility zones: Kerala State Disaster Management Authority (KSDMA), sourced via GSI/NGDR
- DEM: Copernicus Global DSM (COP30), distributed via OpenTopography
- Event report: Government of Kerala, Post-Disaster Needs Assessment — Meppadi Landslide 2024
