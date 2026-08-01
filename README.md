# Map-O-Matic

**A browser-based tool for building, symbolizing, and laying out maps for print.**

Live tool: **[jcinnamon.github.io/map-o-matic](https://jcinnamon.github.io/map-o-matic/)**

Map-O-Matic pairs a GIS-style map builder with a print-layout composer. Bring in your own data — or pull ready-to-map data from online sources — symbolize it, project it, and arrange it into a submission-ready map with a title, legend, north arrow, and calibrated scale bar. Projects and datasets are organized on a home screen and stored in your browser. No installation, no account, no server. Your data never leaves your computer.

![Map-O-Matic screenshot](img/screenshot.jpg)

## Modules

| Module | What it does |
|---|---|
| **Home** | A landing page listing all your projects (thumbnail, layer count, last edited) with rename/duplicate/delete/import/export, plus a Data Library shared across every project. |
| **Map Maker** | Add data by upload, from your library, or from online sources. Search for a place to jump the map there. Choose from open vector and raster basemaps (or a blank canvas), or switch to any of 13 map projections with full pan/zoom/rotate. Symbolize with single symbol, unique values, graduated colour, or graduated point size. Filter, calculate new fields, browse the attribute table and field list, and run 18 spatial tools. |
| **Map Composer** | A drag-and-resize page composer: map frames, titles, legends, north arrows, calibrated scale bars, neatlines, images, inset maps, and functional templates. Group, align, distribute and lock elements. Exports to print-ready PDF or PNG. |

The two modules connect with **Send to Composer** — style your map in Map Maker, click once, and it lands on the layout page as a map frame with an auto-built legend (and a calibrated scale bar, when the map has one). Feature labels can come across as editable text objects rather than being baked into the image, so they can be nudged, restyled or removed on the page. Map Composer also works completely on its own: upload any styled map image and build a layout around it.

## Quick start

1. Open the tool. The first time, it creates a starter project; after that you land on the **Home** screen — open a project or start a new one.
2. **Map Maker:** click **+ Add data ▾** to upload a file, pull from your library, or fetch from an online source (Natural Earth, OpenStreetMap, an open-data portal, or any GeoJSON/CSV/feature-service URL). Use the search bar to jump to a place (it drops a marker you can remove from its popup). Select a layer — each has its own **Table** and **Fields** buttons — to set its symbology, filter, and labels.
3. Click **Send to Composer**. Your styled map and a matching legend appear on the layout page automatically.
4. **Map Composer:** add a title, north arrow, and neatline from the toolbar, or start from a **Template** and double-click its placeholders to fill them. Drag, resize, and rotate anything; collapse the side panel for more room.
5. **Export ▸** for a print-ready PDF or PNG — or a georeferenced image, a zip of your data layers, or a full project archive.

The in-tool **Help** button covers everything in more depth.

## Projects, the data library, and where things live

Every project — its data, symbology, and layout — is stored in your browser (IndexedDB), listed on the **Home** screen with a thumbnail and last-edited time. The project dropdown in the top bar switches between them without a trip home; work autosaves as you go. Every dataset you add, from any source, lands in a shared **Data Library** reusable across all your projects — add it to a new project with **+ Add data → From my library**, where you can tick several datasets and add them all at once instead of re-fetching them one at a time. The Data Library tab on the Home screen also has a **Remove all** button that clears every dataset not currently used by a project (in-use datasets are kept and reported). The landing screen itself carries a short intro banner and a footer crediting the open libraries the tool is built on; clicking the **Map-O-Matic** wordmark from anywhere returns you there.

Because storage lives in the browser, it's tied to that browser on that computer. On a shared or lab machine, download a project file or a full project archive (Export) before you leave — importing it elsewhere restores everything, including the datasets it uses.

### Working across computers (optional)

The **☁ Sync** button in the top bar points Map-O-Matic at a folder you already sync — your OneDrive, Google Drive or Dropbox folder. Projects are then written there as ordinary files whenever they save, so you can pick up the same work on another computer. Nothing is sent to any server we run: the files go to your own storage, and everything continues to work in the browser exactly as before.

Projects found in that folder but not yet on the computer you're using appear on the Home screen under *In your sync folder, not on this computer*, one click away from opening. If a project was changed on another machine since you opened it, Map-O-Matic warns you before overwriting and offers to load the newer version or branch off a separate copy.

This uses the browser's File System Access API, so it needs **Chrome or Edge**; in Safari and Firefox the button explains that and the Export/Import project file route still works. Projects embed their datasets, so files can run to tens of megabytes — writes are batched rather than continuous.

## Two ways to build a map

**A. All in Map-O-Matic.** Add data in Map Maker, symbolize and filter it, then Send to Composer. Scale is calibrated automatically from the map's real coordinates (Web Mercator view only — projected views don't carry a single scale).

**B. Bring your own map image.** Made a map in other software? Export it as an image and upload it in Map Composer via *Map Frame*. Calibrate the scale bar by drawing a reference line between two points of known distance.

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

**Layers panel.** Each layer card shows a visibility checkbox, name, and an **ACTIVE** badge on the selected layer, with **Table** (attribute table) and **Fields** (full field list with types) icon buttons alongside zoom/rename/duplicate/export/delete. Drag a card by its grip to reorder — the top of the list draws on top of the map. Click anywhere on a card — or its grey **Activate** button (shown on every non-active card) — to make it active. Hidden layers can't be the active one; switching one off passes the selection to the next visible layer. The toolbar's ↩/↪ buttons (or Ctrl+Z / Ctrl+Shift+Z) undo and redo Map Maker changes, including attribute edits. A **"Current layer:"** status line above the map keeps track of what you're editing, and the panel is resizable by its right edge.

**Selecting features.** Click a feature on the map to select it, or click a row in the attribute table — the two stay in sync, highlighting the feature on the map and its row in the table. Ctrl/Cmd-click adds to the selection, Shift-click selects a range of table rows, and clicking a class in the Style tab selects every feature in it. A count appears in the map toolbar with a **Selected ▾** menu: zoom to selection, invert it, clear it, copy it into a new layer, or export just those features as GeoJSON or CSV.

**On-map controls.** Under the zoom buttons sit three tools: a **globe view**, a **measure-distance** tool (click points, read the running great-circle total, double-click to finish), and a **basemap-layers** panel that turns parts of the vector basemaps on and off — country/admin borders, place labels, roads and railways, water, buildings, land use and parks, and points of interest. The **globe view** wraps the actual basemap onto a true 3-D sphere (MapLibre GL's globe projection), keeping the basemap's own styling and overlaying your layers on top — drag to spin, scroll to zoom, and click **Back to flat map** to return. It's a live rendered globe rather than the flat orthographic projection preview offered under Projections.

**Basemaps.** The default set is open. Five vector styles come from **OpenFreeMap** — *Positron* (light, the default), *Bright*, *Liberty* (full streets), *Dark* and *Fiord* (muted) — built on OpenStreetMap data through the OpenMapTiles schema and rendered with MapLibre GL, so they stay crisp at any zoom. Two open raster layers sit alongside them: **OpenStreetMap** standard, and **Sentinel-2 Cloudless** — a cloud-free Copernicus mosaic from EOX, fully open but only ~10 m resolution, so it's context rather than street-level detail. For sharper imagery there are two higher-resolution options, **Satellite** and **Satellite Hybrid** (imagery plus roads, labels and boundaries from open OpenStreetMap-derived data): the reference overlay is open, but the imagery itself is proprietary (free to use with attribution, sourced from Vantor/Maxar and Earthstar Geographics), so it doesn't meet the open bar the way the rest do. The attribution for whichever basemap you pick shows under the picker; the Sentinel-2 mosaic is CC-BY-NC-SA (free for teaching and study, not commercial reuse). Projects saved before the switch that named an Esri or CARTO basemap are quietly mapped to the closest current one — old imagery projects land on Satellite.

**Projections.** Switch from the Web Mercator editing view into any of 13 projections: world (Equal Earth, Robinson, Winkel Tripel, Mollweide, Mercator, Orthographic), regional conic (Albers Equal-Area, Lambert Conformal, with adjustable centre and standard parallels), azimuthal (Equidistant, Stereographic), and historical/novelty (Gall–Peters, Goode Homolosine, Bonne). The projected view is fully interactive and behaves like the normal map: scroll or double-click to zoom (Shift+double-click zooms out), on-screen **+/−** buttons, drag to pan (or rotate the globe on Orthographic/azimuthal projections), with **Fit to data** and **Fit to world** buttons to reset the view. Polygons on interrupted projections (Goode Homolosine) are pre-stitched so they don't tear across the interruption gaps. An optional graticule and world-land backdrop can be toggled; raster basemaps can't be reprojected client-side, so they hide while a projection is active.

**Right panel.** Three tabs: **Style** (symbology), **Data** (Filter and Labels, in collapsible sections), and **Tools** (the spatial toolbox, grouped under headings you can fold away).

**Symbology.** Single symbol, unique values (categories — scanned across the *entire* dataset, with the top N most frequent values coloured individually and the rest grouped into an editable "Other" category, or **Show all** to list and colour every value), graduated colour (quantile / equal interval / natural breaks–Jenks / manual classification, up to 12 classes, with optional rate normalization by a second field), graduated symbol size, **proportional (unclassed) symbols** where area scales with the value, **bivariate** symbols where size follows one field and colour another, and **dot density** for polygons. Labels support the full typography set below, with an optional halo, and can be offset into any of nine positions around a symbol (default top-right, with an adjustable distance) so they sit clear of the marker rather than on top of it.

**Point symbols.** Click the symbol button to open a picker showing every marker at once. Thirty built-in markers grouped the way cartography texts do — *abstract* (circle, square, triangle, diamond, pentagon, hexagon, star, cross, saltire, bar), *associative* (tent, tree, water, industry, settlement, peak, rainfall, vegetation, route, place marker), and *iconic* (school, hospital, airport, port, railway, fuel, accommodation, café, waste, power). Each takes the layer's colour, size and outline, and you can upload your own SVG. The same definitions drive both the map and the projected view.

**Colours.** Every colour control opens the same picker: a saturation/lightness field with a hue slider, numeric entry in **hex, RGB, HSL, HSV, CMYK, CIE Lab, CIE LCh or OKLCh**, a palette of map colours, the colours used recently, an eyedropper for matching something already on screen, and — where it makes sense — a crossed-out **No colour** swatch for unfilled symbols, borderless polygons, or an unshaded class. The perceptual spaces are there for a reason: Lab and LCh are where you can reason about even lightness steps in a sequential scheme. A colour typed outside the sRGB gamut is flagged rather than silently changed.

**Colour ramps.** Classes are listed highest-first, as they read on a legend, and their ranges never share a value — one class ends where the next begins plus a decimal place. Every class colour can be edited individually, or set to no colour. Ramps import from QGIS colour-ramp XML, a plain list of hex codes, a CSS `linear-gradient(...)`, or an ArcGIS `.clr` file, and are interpolated to whatever class count you ask for, so 10–12 classes work even though ColorBrewer itself stops at nine. With **Manual breaks**, each break is its own editable number, with buttons to add one or space them evenly.

**Typography.** Both map labels and every Layout text element share the same type controls: 11 system fonts plus 10 Google fonts (loaded on demand), bold, italic, underline, colour, alignment, letter spacing, and line height.

**Attribute table.** Opens as a floating window you can drag and resize, so the map stays live underneath. Dock it to the bottom or the right when you want map and table side by side, with a divider to set its size. It stays open as you switch layers, reloading for whichever layer is active, and remembers its size between sessions.

**Filtering.** Build conditions with AND/OR. The value box has a **populate values** button that lists every distinct value in the chosen field with its frequency and a search box, so you can pick rather than type.

**Spatial tools** — the **Tools** tab in the right panel (all client-side, via Turf.js): buffer (with dissolve), select by location (intersects / within / contains / within-distance, with invert), points-in-polygons statistics (count, sum, mean, min, max), clip, erase, intersect (with attribute join), union, dissolve by attribute, merge layers, centroids, convex hull, bounding box, simplify (Douglas–Peucker generalization), nearest-neighbour join, and a distance matrix (CSV download).

Each layer can be exported independently as valid GeoJSON or CSV — including any calculated fields — for use in other GIS software.

## Map Composer: composing the page

Elements: map frame (image, or from Map Maker), inset/locator map (with its own live basemap and optional data overlay), title and text, legend, north arrow (3 styles), scale bar, neatline (plain or tick-marked), images/logos, and sketching. Selecting an element in the Layers tab opens its properties.

**Legends** take area, point and line swatches plus bold heading rows, reorderable with ↑/↓, and can be trimmed to fit their contents so an added border sits tight around the text. The title, layer headings and item labels are styled independently — typeface, size, colour, bold and italic for each — along with row spacing and swatch size. The panel behind the legend has its own background fill and optional border.

**Scale bars** come in five styles: alternating checker, plain bar, line with end ticks, double/stacked showing two units at once, and text-only representative fraction (`1:50,000` or `1 cm = 500 m`). Set the number of divisions, bar height, colour, and label size. Drag the bar's side handles to change its length and the distance it represents follows, rounded to one decimal place (this can be turned off), switching between m/km as the number gets awkward. Scale is calibrated automatically from Map Maker, or manually by drawing a reference line between two points of known distance.

**Sketching.** Straight lines, arrows, rectangles, ellipses, polygons, a freehand pen and a highlighter. It works the way a simple graphics program does: pick a tool, draw one shape, and the pointer comes straight back with the new shape selected and its handles showing — clicking elsewhere never starts another shape by accident. Settings live in the right panel: stroke colour, width, opacity, line style (solid/dashed/dotted), end caps, and fill colour and opacity for closed shapes.

**Arrows and lines** keep their endpoints, so they can be re-aimed by dragging either round handle long after they were drawn. They also rotate: drag the round handle above the shape to swing it about its centre (hold Shift for 15° steps), or type a bearing in the panel — 0° points up the page, which is what you want for a direction arrow on a north-up map. Arrowheads are editable at any time — filled triangle, open V, barb, circle, square or none, at any size, on the end, the start, both ends or neither. Polygons can be reshaped by double-clicking them and dragging their individual points.

**Grouping, aligning and locking.** Shift-click or drag a box to select several elements, then group them (Ctrl/Cmd+G) so they move, scale and rotate as one — the quickest way to handle the shower of labels that arrives with a map from Map Maker. Double-click a group to open it and edit one part; click empty space to close it again. Ctrl/Cmd+Shift+G breaks a group apart. A multiple selection also gets align (six edges and centres) and distribute-evenly buttons; a single element aligns to the page instead. Any element can be locked against accidental edits, and unlocked again from the Layers tab.

**Zoom.** The top bar has zoom in/out buttons with the current level, plus a menu for Fit whole page, Fit width, Zoom to selection, and preset levels. Ctrl/Cmd+scroll zooms about the cursor, and Ctrl/Cmd with `+`, `−` or `0` works from the keyboard. Zoom only affects the screen — exports always render the page at full size.

**Borders.** Any element can carry a border: colour, width, line style (solid/dashed/dotted), corner radius, padding, and an optional drop shadow. Legends use the same controls under *Legend panel*, alongside the panel's background fill.

**Templates** are functional starting layouts — classic portrait, landscape with side panel, two-frame comparison — with placeholders you double-click to fill: a map-frame placeholder opens the image picker (or is filled automatically by Send to Composer), a legend placeholder becomes a real, editable legend, both sized to fit the slot.

Every element on the page shares the full typography controls (font, bold/italic/underline, colour, alignment, spacing, line height where applicable) and an optional **border** toggle (width, colour, padding) in its Properties panel.

The right-side Properties/Layers panel collapses for more screen room and can be dragged wider or narrower (its width is remembered). Undo/redo (Ctrl+Z / Ctrl+Shift+Z), snap-to-centre/margin guides, and a toggleable 0.5" margin guide (never exported) are built in.

## Sharing a map on the web

The quickest way to share a finished, interactive map is the **🔗 Share** button in the top bar. It packs the whole map — your styled layers, the basemap, the view and a legend — into a single link. No upload, no account, nothing sent to any server: the map travels inside the link itself. Whoever opens it sees the live map in a clean read-only viewer (pan, zoom, click a feature for its attributes, switch basemaps). The dialog gives you the link, a **View in browser** button to preview it in a new tab, and a ready **`<iframe>` embed code** to paste into ArcGIS StoryMaps (an *Embed* block) or any web page.

**One-click publish (optional).** If your instructor has enabled it, the **Export ▸ Interactive web map** dialog also offers **Sign in with GitHub & publish**, which puts the map on your own GitHub Pages and gives you a permanent link in one step. It needs a one-time setup by the instructor (a GitHub OAuth App plus a small "gatekeeper" service) — see `map-o-matic-publishing-setup.md` and `map-o-matic-gatekeeper-worker.js`. Without it, the guided Netlify Drop route above works with no setup at all.

For this to open for other people, Map-O-Matic has to be online at a stable address — your published copy (e.g. GitHub Pages) — since the link points back to it. A link made from a file sitting on your own computer only opens on that computer. Only very large maps overflow a link; when that happens Share says so and points you to the file export below, which works at any size. (Point symbols are packed efficiently, so typical multi-layer course maps fit comfortably.)

## Exporting


One dialog covers it all: the layout as print-ready **PDF**, **PNG**, or editable **SVG** (vector — text and shapes stay editable in Illustrator, Inkscape, or similar software); the Map Maker view as a **georeferenced PNG** with a world file (Web Mercator only — projected views export as a plain image, since they don't have a single consistent ground scale); **all data layers** zipped as GeoJSON; or a full **project archive** — layout PDF + PNG, every layer, and the portable project file, all in one zip.

**Interactive web map (embed).** A separate export builds a single self-contained **HTML file** — a working Leaflet map of your styled layers, with popups, a legend, an open basemap and fit-to-data, all baked in. This is the option for very large maps or when you want a permanent URL of your own: host the file anywhere (GitHub Pages, your sync folder's public link, any web host) and it stays interactive, with a matching **`<iframe>` snippet** to paste where you uploaded it. For most maps the **🔗 Share** link above is the faster, zero-hosting route. Only the visible layers are included. After the file downloads, the dialog walks you through publishing it: a button opens **Netlify Drop** (drag the file on, it's live in under a minute), and pasting the address it gives back rewrites the embed code with your real URL.

## Built with

Single-file HTML/JS application. [Leaflet](https://leafletjs.com/) and [MapLibre GL JS v5](https://maplibre.org/) (map rendering, including the 3-D globe view; open vector basemaps from [OpenFreeMap](https://openfreemap.org/)), [Fabric.js](http://fabricjs.com/) (layout canvas), [D3](https://d3js.org/) + [d3-geo-projection](https://github.com/d3/d3-geo-projection) (map projections), [Turf.js](https://turfjs.org/) (spatial analysis), [chroma.js](https://gka.github.io/chroma.js/) (colour ramps), [simple-statistics](https://simplestatistics.org/) (Jenks classification), [PapaParse](https://www.papaparse.com/) (CSV), [shpjs](https://github.com/calvinmetcalf/shapefile-js) (shapefile parsing), [JSZip](https://stuk.github.io/jszip/), [jsPDF](https://github.com/parallax/jsPDF), and [html2canvas](https://html2canvas.hertzen.com/) (export).

## Notes and limitations

Projects and the data library live in the browser and computer where they were created — use Export (project file or archive) as backup, especially on shared or lab computers. Map capture (Send to Composer, inset-map snapshots) depends on the basemap server allowing cross-origin image capture; the open OpenFreeMap and Sentinel-2 basemaps are tested to work, but if a capture fails, switch basemaps or take a manual screenshot and add it via *Map Frame*. Overlay tools (clip/erase/intersect) on complex or very large datasets can be slow in the browser — simplify first if needed. OpenStreetMap and open-data-portal results reflect community/agency data quality and coverage, which varies by place and theme.

## Citation

If you use Map-O-Matic in research or teaching:

> Cinnamon, J. (2026). *Map-O-Matic: A browser-based tool for building, symbolizing, and laying out maps* [Computer software]. https://jcinnamon.github.io/carto-studio/

## License

MIT © Jonathan Cinnamon.

---

[Jonathan Cinnamon](https://www.jonathancinnamon.com), Geography, UBC Okanagan
