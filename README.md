# Carto Studio

**A browser-based tool for building, symbolizing, and laying out maps for print.**

Live tool: **[jcinnamon.github.io/carto-studio](https://jcinnamon.github.io/carto-studio/)**

Carto Studio pairs a GIS-style map builder with a print-layout composer. Bring in your own data — or pull ready-to-map data from online sources — symbolize it, project it, and arrange it into a submission-ready map with a title, legend, north arrow, and calibrated scale bar. Projects and datasets are organized on a home screen and stored in your browser. No installation, no account, no server. Your data never leaves your computer.

![Carto Studio screenshot](img/screenshot.jpg)

## Modules

| Module | What it does |
|---|---|
| **Home** | A landing page listing all your projects (thumbnail, layer count, last edited) with rename/duplicate/delete/import/export, plus a Data Library shared across every project. |
| **Map Maker** | Add data by upload, from your library, or from online sources. Search for a place to jump the map there. Choose from nine basemaps or a blank canvas, or switch to any of 13 map projections with full pan/zoom/rotate. Symbolize with single symbol, unique values, graduated colour, or graduated point size. Filter, calculate new fields, browse the attribute table and field list, and run 18 spatial tools. |
| **Map Layout** | A drag-and-resize page composer: map frames, titles, legends, north arrows, calibrated scale bars, neatlines, images, inset maps, and functional templates. Exports to print-ready PDF or PNG. |

The two modules connect with **Send to Layout** — style your map in Map Maker, click once, and it lands on the layout page as a map frame with an auto-built legend (and a calibrated scale bar, when the map has one). Map Layout also works completely on its own: upload any styled map image and build a layout around it.

## Quick start

1. Open the tool. The first time, it creates a starter project; after that you land on the **Home** screen — open a project or start a new one.
2. **Map Maker:** click **+ Add data ▾** to upload a file, pull from your library, or fetch from an online source (Natural Earth, OpenStreetMap, an open-data portal, or any GeoJSON/CSV/feature-service URL). Use the search bar to jump to a place (it drops a marker you can remove from its popup). Select a layer — each has its own **Table** and **Fields** buttons — to set its symbology, filter, and labels.
3. Click **Send to Layout**. Your styled map and a matching legend appear on the layout page automatically.
4. **Map Layout:** add a title, north arrow, and neatline from the toolbar, or start from a **Template** and double-click its placeholders to fill them. Drag, resize, and rotate anything; collapse the side panel for more room.
5. **Export ▸** for a print-ready PDF or PNG — or a georeferenced image, a zip of your data layers, or a full project archive.

The in-tool **Help** button covers everything in more depth.

## Projects, the data library, and where things live

Every project — its data, symbology, and layout — is stored in your browser (IndexedDB), listed on the **Home** screen with a thumbnail and last-edited time. The project dropdown in the top bar switches between them without a trip home; work autosaves as you go. Every dataset you add, from any source, lands in a shared **Data Library** reusable across all your projects — add it to a new project with **+ Add data → From my library** instead of re-fetching it.

Because storage lives in the browser, it's tied to that browser on that computer. On a shared or lab machine, download a project file or a full project archive (Export) before you leave — importing it elsewhere restores everything, including the datasets it uses.

## Two ways to build a map

**A. All in Carto Studio.** Add data in Map Maker, symbolize and filter it, then Send to Layout. Scale is calibrated automatically from the map's real coordinates (Web Mercator view only — projected views don't carry a single scale).

**B. Bring your own map image.** Made a map in other software? Export it as an image and upload it in Map Layout via *Map Frame*. Calibrate the scale bar by drawing a reference line between two points of known distance.

An optional **Live Embed** tool drops in an interactive web map (via its embed URL) for on-screen reference — it prints as a placeholder, so submissions still need an image or Map Maker frame.

## Adding data

**+ Add data ▾** in Map Maker offers three paths:

- **Upload** — GeoJSON, CSV with latitude/longitude columns, or a zipped Shapefile. Drag-and-drop onto the map also works.
- **From my library** — anything already fetched or uploaded in any project.
- **Online sources** — a built-in browser for:
  - **World base data**: Natural Earth countries, states/provinces, populated places, urban areas, land, ocean, coastline, rivers, and lakes at 110m/50m/10m detail.
  - **OpenStreetMap**: ten themed presets (schools, hospitals, parks, supermarkets, restaurants, bus stops, major roads, cycle paths, waterways, buildings) queried live via Overpass within the current map view.
  - **Open data portals**: keyword search across the Opendatasoft network or a specific portal domain, filtered to mappable datasets.
  - **From URL**: any GeoJSON link, CSV with lat/long, or Esri feature-service endpoint.

Datasets over 5,000 features prompt a choice — load all, load the first 5,000, or cancel — before committing to browser storage.

## Map Maker: layers, projections, symbology, and spatial tools

**Layers panel.** Each layer card shows a visibility checkbox, name, and an **ACTIVE** badge on the selected layer, with **Table** (attribute table) and **Fields** (full field list with types) icon buttons alongside zoom/rename/reorder/duplicate/export/delete. A **"Current layer:"** status line above the map keeps track of what you're editing. The panel itself is resizable — drag its right edge to give it more or less width.

**Selecting features.** Click a feature on the map to select it, or click a row in the attribute table — the two stay in sync, highlighting the feature on the map and its row in the table. Ctrl/Cmd-click adds to the selection, Shift-click selects a range of table rows, and clicking a class in the Style tab selects every feature in it. A count appears in the map toolbar with a **Selected ▾** menu: zoom to selection, invert it, clear it, copy it into a new layer, or export just those features as GeoJSON or CSV.

**Projections.** Switch from the Web Mercator editing view into any of 13 projections: world (Equal Earth, Robinson, Winkel Tripel, Mollweide, Mercator, Orthographic), regional conic (Albers Equal-Area, Lambert Conformal, with adjustable centre and standard parallels), azimuthal (Equidistant, Stereographic), and historical/novelty (Gall–Peters, Goode Homolosine, Bonne). The projected view is fully interactive and behaves like the normal map: scroll or double-click to zoom (Shift+double-click zooms out), on-screen **+/−** buttons, drag to pan (or rotate the globe on Orthographic/azimuthal projections), with **Fit to data** and **Fit to world** buttons to reset the view. Polygons on interrupted projections (Goode Homolosine) are pre-stitched so they don't tear across the interruption gaps. An optional graticule and world-land backdrop can be toggled; raster basemaps can't be reprojected client-side, so they hide while a projection is active.

**Right panel.** Three tabs: **Style** (symbology), **Data** (Filter and Labels, in collapsible sections), and **Tools** (the spatial toolbox, grouped under headings you can fold away).

**Symbology.** Single symbol, unique values (categories — scanned across the *entire* dataset, with the top N most frequent values coloured individually and the rest grouped into an editable "Other" category, or **Show all** to list and colour every value), graduated colour (quantile / equal interval / natural breaks–Jenks / manual classification, ColorBrewer ramps, with optional rate normalization by a second field), and graduated/proportional point size. Labels support the full typography set below, with an optional halo.

**Typography.** Both map labels and every Layout text element share the same type controls: 11 system fonts plus 10 Google fonts (loaded on demand), bold, italic, underline, colour, alignment, letter spacing, and line height.

**Attribute table.** Opens as a floating window you can drag and resize, so the map stays live underneath. Dock it to the bottom or the right when you want map and table side by side, with a divider to set its size. It stays open as you switch layers, reloading for whichever layer is active, and remembers its size between sessions.

**Filtering.** Build conditions with AND/OR. The value box has a **populate values** button that lists every distinct value in the chosen field with its frequency and a search box, so you can pick rather than type.

**Spatial tools** — the **Tools** tab in the right panel (all client-side, via Turf.js): buffer (with dissolve), select by location (intersects / within / contains / within-distance, with invert), points-in-polygons statistics (count, sum, mean, min, max), clip, erase, intersect (with attribute join), union, dissolve by attribute, merge layers, centroids, convex hull, bounding box, simplify (Douglas–Peucker generalization), nearest-neighbour join, and a distance matrix (CSV download).

Each layer can be exported independently as valid GeoJSON or CSV — including any calculated fields — for use in other GIS software.

## Map Layout: composing the page

Elements: map frame (image, or from Map Maker), inset/locator map (with its own live basemap and optional data overlay), title and text, legend, north arrow (3 styles), scale bar, neatline (plain or tick-marked), images/logos, and sketching. Selecting an element in the Layers tab opens its properties.

**Legends** take area, point and line swatches plus bold heading rows, reorderable with ↑/↓. The title, layer headings and item labels are styled independently — typeface, size, colour, bold and italic for each — along with row spacing and swatch size. The panel behind the legend has its own background fill and optional border.

**Scale bars** come in five styles: alternating checker, plain bar, line with end ticks, double/stacked showing two units at once, and text-only representative fraction (`1:50,000` or `1 cm = 500 m`). Set the number of divisions, bar height, colour, and label size. Drag the bar's side handles to change its length and the distance it represents follows, rounded to one decimal place (this can be turned off), switching between m/km as the number gets awkward. Scale is calibrated automatically from Map Maker, or manually by drawing a reference line between two points of known distance.

**Sketching.** Straight lines, arrows, rectangles, ellipses, polygons, a freehand pen and a highlighter. It works the way a simple graphics program does: pick a tool, draw one shape, and the pointer comes straight back with the new shape selected and its handles showing — clicking elsewhere never starts another shape by accident. Settings live in the right panel: stroke colour, width, opacity, line style (solid/dashed/dotted), end caps, and fill colour and opacity for closed shapes.

**Arrows and lines** keep their endpoints, so they can be re-aimed by dragging either round handle long after they were drawn. Arrowheads are editable at any time — filled triangle, open V, barb, circle, square or none, at any size, on the end, the start, both ends or neither. Polygons can be reshaped by double-clicking them and dragging their individual points.

**Zoom.** The top bar has zoom in/out buttons with the current level, plus a menu for Fit whole page, Fit width, Zoom to selection, and preset levels. Ctrl/Cmd+scroll zooms about the cursor, and Ctrl/Cmd with `+`, `−` or `0` works from the keyboard. Zoom only affects the screen — exports always render the page at full size.

**Borders.** Any element can carry a border: colour, width, line style (solid/dashed/dotted), corner radius, padding, and an optional drop shadow. Legends use the same controls under *Legend panel*, alongside the panel's background fill.

**Templates** are functional starting layouts — classic portrait, landscape with side panel, two-frame comparison — with placeholders you double-click to fill: a map-frame placeholder opens the image picker (or is filled automatically by Send to Layout), a legend placeholder becomes a real, editable legend, both sized to fit the slot.

Every element on the page shares the full typography controls (font, bold/italic/underline, colour, alignment, spacing, line height where applicable) and an optional **border** toggle (width, colour, padding) in its Properties panel.

The right-side Properties/Layers panel collapses for more screen room and can be dragged wider or narrower (its width is remembered). Undo/redo (Ctrl+Z / Ctrl+Shift+Z), snap-to-centre/margin guides, and a toggleable 0.5" margin guide (never exported) are built in.

## Exporting

One dialog covers it all: the layout as print-ready **PDF**, **PNG**, or editable **SVG** (vector — text and shapes stay editable in Illustrator, Inkscape, or similar software); the Map Maker view as a **georeferenced PNG** with a world file (Web Mercator only — projected views export as a plain image, since they don't have a single consistent ground scale); **all data layers** zipped as GeoJSON; or a full **project archive** — layout PDF + PNG, every layer, and the portable project file, all in one zip.

## Built with

Single-file HTML/JS application. [Leaflet](https://leafletjs.com/) (map rendering), [Fabric.js](http://fabricjs.com/) (layout canvas), [D3](https://d3js.org/) + [d3-geo-projection](https://github.com/d3/d3-geo-projection) (map projections), [Turf.js](https://turfjs.org/) (spatial analysis), [chroma.js](https://gka.github.io/chroma.js/) (colour ramps), [simple-statistics](https://simplestatistics.org/) (Jenks classification), [PapaParse](https://www.papaparse.com/) (CSV), [shpjs](https://github.com/calvinmetcalf/shapefile-js) (shapefile parsing), [JSZip](https://stuk.github.io/jszip/), [jsPDF](https://github.com/parallax/jsPDF), and [html2canvas](https://html2canvas.hertzen.com/) (export).

## Notes and limitations

Projects and the data library live in the browser and computer where they were created — use Export (project file or archive) as backup, especially on shared or lab computers. Map capture (Send to Layout, inset-map snapshots) depends on the basemap tile server allowing cross-origin image capture; Esri and Carto basemaps are tested to work, but if a capture fails, switch basemaps or take a manual screenshot and add it via *Map Frame*. Overlay tools (clip/erase/intersect) on complex or very large datasets can be slow in the browser — simplify first if needed. OpenStreetMap and open-data-portal results reflect community/agency data quality and coverage, which varies by place and theme.

## Citation

If you use Carto Studio in research or teaching:

> Cinnamon, J. (2026). *Carto Studio: A browser-based tool for building, symbolizing, and laying out maps* [Computer software]. https://jcinnamon.github.io/carto-studio/

## License

MIT © Jonathan Cinnamon.

---

[Jonathan Cinnamon](https://www.jonathancinnamon.com), Geography, UBC Okanagan
