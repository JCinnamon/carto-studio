# carto-studio
Lightweight cartography and map making tool

# Carto Studio

**A browser-based tool for building, symbolizing, and laying out maps for print.**

Live tool: **[jcinnamon.github.io/carto-studio](https://jcinnamon.github.io/carto-studio/)**

Carto Studio pairs a GIS-style map builder with a print-layout composer. Bring in your own data or a styled map image, symbolize it, and arrange it into a submission-ready map with a title, legend, north arrow, and calibrated scale bar. No installation, no account, no server. Your data never leaves your computer.

![Carto Studio screenshot](img/screenshot.jpg)

## Modules

| Module | What it does |
|---|---|
| **Map Maker** | Upload GeoJSON, CSV (lat/long), or zipped shapefiles. Choose from nine basemaps (Esri, OpenStreetMap, Carto, or none). Symbolize with single symbol, unique values, graduated colour (quantile / equal interval / natural breaks / manual, ColorBrewer ramps), or graduated point size. Filter, calculate new fields, browse the attribute table, and run 14 spatial tools. |
| **Map Layout** | A drag-and-resize page composer: map frames, titles, legends, north arrows, calibrated scale bars, neatlines, images, inset maps, and templates. Exports to print-ready PDF or PNG. |

The two modules connect with **Send to Layout** — style your map in Map Maker, click once, and it lands on the layout page as a calibrated map frame with an auto-built legend. Map Layout also works completely on its own: upload any styled map image (e.g., exported from ArcGIS Online) and build a layout around it.

## Quick start

1. Open the tool in a modern browser (Chrome or Edge recommended).
2. **Map Maker:** click *+ Add data* and upload a GeoJSON, CSV, or zipped shapefile. Select the layer on the left, then set its symbology, filter, and labels on the right.
3. Click **Send to Layout**. Your styled map, a matching legend, and a calibrated scale bar appear on the layout page automatically.
4. **Map Layout:** add a title, north arrow, and neatline from the toolbar on the left, or start from a **Template**. Drag, resize, and rotate anything.
5. **Export ▸** for a print-ready PDF or PNG.

The in-tool **Help** button covers both workflows in more depth, including working from an ArcGIS Online export instead of Map Maker.

## Two ways to build a map

**A. All in Carto Studio.** Upload data in Map Maker, symbolize and filter it, then Send to Layout. Scale is calibrated automatically from the map's real coordinates.

**B. ArcGIS Online → Layout only.** Style and classify your map in ArcGIS Online as usual, export it as an image with the Print widget, and upload it in Map Layout via *Map Frame*. Calibrate the scale bar by drawing a reference line between two points of known distance.

An optional **Live Embed** tool drops in an interactive ArcGIS Online web map (via its Embed URL) for on-screen reference — it prints as a placeholder, so submissions still need an image or Map Maker frame.

## Map Maker: symbology and spatial tools

Symbology: single symbol, unique values (categories), graduated colour (with optional rate normalization by a second field), and graduated/proportional point size. Labels with halo option.

Spatial tools (all client-side, via Turf.js): buffer (with dissolve), select by location (intersects / within / contains / within-distance, with invert), points-in-polygons statistics (count, sum, mean, min, max), clip, erase, intersect (with attribute join), union, dissolve by attribute, merge layers, centroids, convex hull, bounding box, simplify (Douglas–Peucker generalization), nearest-neighbour join, and a distance matrix (CSV download).

Each layer can be exported independently as valid GeoJSON or CSV — including any calculated fields — for use in ArcGIS Online, QGIS, or elsewhere. (**Save project**, separately, bundles your whole session — data, styling, and layout — for reloading in Carto Studio; it is not a GeoJSON file.)

## Map Layout: composing the page

Elements: map frame (image or from Map Maker), inset/locator map (with its own live basemap and optional data overlay), title and text, legend (box/point/line swatches, editable rows, optional layer subheadings), north arrow (3 styles), scale bar (auto-calibrated or manually calibrated by reference line), neatline (plain or tick-marked), and images/logos. Three starting templates: classic portrait, landscape with side panel, and two-frame comparison.

Undo/redo (Ctrl+Z / Ctrl+Shift+Z), snap-to-centre/margin guides, and a toggleable 0.5" margin guide (never exported) are built in.

## Where your data lives

Everything runs in your browser. Datasets, styling, and layouts exist only in the browser tab and in any file you explicitly save. The map tiles (basemap imagery) and the optional Live Embed are the only features that need an ongoing internet connection. **Save project** downloads a single JSON file with your full session — data, symbology, and layout — for backup or continuing later.

## Built with

Single-file HTML/JS application. [Leaflet](https://leafletjs.com/) (map rendering), [Fabric.js](http://fabricjs.com/) (layout canvas), [Turf.js](https://turfjs.org/) (spatial analysis), [chroma.js](https://gka.github.io/chroma.js/) (colour ramps), [simple-statistics](https://simplestatistics.org/) (Jenks classification), [PapaParse](https://www.papaparse.com/) (CSV), [shpjs](https://github.com/calvinmetcalf/shapefile-js) (shapefile parsing), [jsPDF](https://github.com/parallax/jsPDF) and [html2canvas](https://html2canvas.hertzen.com/) (export).

## Notes and limitations

Sessions are tied to the browser and computer where they were created — use **Save project** as backup before closing the tab. Map capture (Send to Layout, and inset-map snapshots) depends on the basemap tile server allowing cross-origin image capture; Esri and Carto basemaps are tested to work, but if a capture fails, switch basemaps or take a manual screenshot and add it via *Map Frame*. Overlay tools (clip/erase/intersect) on complex or very large datasets can be slow in the browser — simplify first if needed.

## Citation

If you use Carto Studio in research or teaching:

> Cinnamon, J. (2026). *Carto Studio: A browser-based tool for building, symbolizing, and laying out maps* [Computer software]. https://jcinnamon.github.io/carto-studio/

## License

MIT © Jonathan Cinnamon.

---

[Jonathan Cinnamon](https://www.jonathancinnamon.com), Geography, UBC Okanagan

