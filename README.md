# NYC Boundary Mask GeoJSON

`nyc_tiles.geojson` is a GeoJSON Polygon that covers the entire planet with an NYC-shaped hole cut out of it. This is useful for **masking** or subduing areas outside of New York City when building web maps that feature NYC-specific data overlays — for example, rendering a semi-transparent fill over everything except the five boroughs.

## How it works

The feature is a single `Polygon` with two rings:

- **Outer ring** — a rectangle covering the full extent of the earth (`-180, -90` to `180, 90`)
- **Inner ring (hole)** — the boundary of New York City

Anything rendered with this polygon will cover the whole world except the area inside the NYC boundary.

## Preview

### Raw geometry on geojson.io

<img width="1155" height="704" alt="geojson_io___Powered_by_Mapbox_and_2026_Grading_-_Google_Docs" src="https://github.com/user-attachments/assets/470034e0-071d-4182-b7de-71e4cc44806e" />

### In use in the NYC Public Space app

<img width="944" height="620" alt="Cursor_and_NYC_Public_Space_and_Editing_nyc-boundary-mask-ge…g_nyc-boundary-mask-geojson" src="https://github.com/user-attachments/assets/ef838a36-82ca-4996-b35c-00a00b900679" />

## How it was created

1. Started with the **Borough Boundaries** dataset from the NYC Department of City Planning:
   https://www.nyc.gov/content/planning/pages/resources/datasets/borough-boundaries
2. Buffered and unioned the borough polygons in **QGIS** to produce a single, continuous NYC boundary.
3. Used the resulting coordinates as the interior ring (hole) of a GeoJSON `Polygon` whose outer ring spans the entire earth.
