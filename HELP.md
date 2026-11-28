# Open DroneLog Add-ons: Help Guide

This file collects every help guide built into the Open DroneLog add-ons (the **Thermal Analysis Studio**, **Photogrammetry** and the **360 Panorama Studio**) in one place. Inside the program, the same guides open from the **?** buttons and the Help panel.

New to the add-ons? Install them first with the step-by-step guide in the [README](README.md), then start with [Thermal Studio: getting started](#thermal-start), [Photogrammetry: getting started](#photo-start) or [360 Panorama Studio: getting started](#panorama-start).

> **Version:** written for add-ons 1.1.1 on Open DroneLog 3.4.0.

> **About this text:** these guides are copied word for word from the in-app help of the Airwulf build of Open DroneLog. Only what a single file needs is changed: headings sit one level lower, links between guides point inside this file, and every section has an anchor. The Airwulf build is based on [Open DroneLog](https://github.com/arpanghosh8453/open-dronelog) by Arpan Ghosh, which is licensed under the [GNU Affero General Public License v3.0](https://github.com/arpanghosh8453/open-dronelog/blob/main/LICENSE) (AGPL-3.0), and this help text is distributed under the same license.

For the main Open DroneLog program (flight logs, maps, charts, batteries), see the original project's [user manual](https://github.com/arpanghosh8453/open-dronelog/blob/main/docs/manual.md).

## Contents


**Thermal Studio**

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
- [Analysing part of a thermal picture: the analysis boundary](#thermal-boundary)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Heat flow network: nodes, conductors, solving](#thermal-network)
- [Vegetation indices from multispectral orthomosaics](#thermal-vegetation)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Side-by-side documents and temperature exports](#thermal-deliverables)

**Photogrammetry**

- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Delivering a claim package: originals, portal copies, custody sheet](#claim-package)
- [Orthomosaic export, linework files and volume tickets](#mapping-deliverables)

**360 Panorama Studio**

- [360 Panorama Studio: getting started, importing, sets and marking up photos](#panorama-start)
- [Stitching a 360: the Stitch panel, camera angles, size, warnings](#panorama-stitch)
- [Looking around a 360, the starting view and the exports](#panorama-export)

**Pictures: annotating and measuring**

- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)
- [Positions, ground control points and georeferenced orthomosaics](#measure-geo)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)

**Settings**

- [Editing the material catalogue: presets, units, packages, waste, prices](#settings-material-presets)
- [Branding your reports: logo, company and Part 107 number](#settings-branding)
- [AI usage: the usage bar, customers and projects, and the AI cost in reports](#ai-usage)
- [AI tools: letting Chat and external agents read and change add-on data](#ai-tools)
- [Saving clients and claim details for reuse](#clients)
- [Encrypting customer data with a password](#customer-encryption)

**Add-ons**

- [Buying, activating and renewing an add-on license, and updating add-ons](#addon-license)


---

# Thermal Studio

<a id="thermal-start"></a>

## Thermal Studio: getting started, importing, the library


The Thermal Studio turns radiometric drone pictures into a temperature for every pixel. You read the temperatures, isolate a range, find hot and cold spots, model heat flow, and put the findings into an inspection report. This topic covers switching the studio on, bringing pictures in, and managing the library.

<a id="thermal-start-what-this-studio-does"></a>

### What this studio does

Each row names a feature, where you find it, and the walkthrough that explains it.

| Feature | Where | Walkthrough |
|---|---|---|
| Import pictures, videos and Metashape exports | **+ Import photos / videos**, **📂 Import folder…** and **🌡 Radiometric file…** in the top bar, or drop files on the studio | [Importing](#thermal-start-importing), [Import folder](#claim-package-import-folder) |
| The library: search, filters, select all, delete, rename | The left column, headed `Assets (N)` | [The asset library](#thermal-start-the-asset-library) |
| Pairing thermal and visual pictures | **⇄ Pair pictures** in the top bar, the ⇄ badge on a library row, the **Visual twin** row under the picture | [Pairing](#thermal-start-pairing-thermal-and-visual-pictures) |
| Temperature statistics, palette and scale | **Temperature Statistics** and **Palette & Scale** in the **Analysis** panel | [Reading temperatures](#thermal-analysis-steps) |
| Emissivity and distance | **Measurement Parameters** in the **Analysis** panel | [Measurement parameters](#thermal-analysis-measurement-parameters) |
| Spot temperatures and differences | **Spot** (🌡) and **ΔT** (±) at the end of the toolbar's **Measure** group; the readings in **Spot readings** in the **Analysis** panel | [Spot readings](#thermal-deliverables-spot-readings), [Drawing them](#annotate-draw-annotations) |
| Material take-offs | **🧮 Material Takeoff** after **🧭 Scale** in the toolbar | [Take-offs](#materials-takeoff-steps) |
| Isolating a temperature range | **Range Isolation (Isotherm)** in the **Analysis** panel | [Isotherm](#thermal-isotherm-steps) |
| Analysing part of a picture | **⛶ Boundary** in the toolbar's **Measure** group; the boundary line in the **Analysis** panel | [The analysis boundary](#thermal-boundary-steps) |
| AI variance analysis and narrative | **AI Variance Analysis** in the **Analysis** panel | [Detecting anomalies](#thermal-anomalies-detecting-anomalies) |
| Heat flow network | **Node** (⬤) and **Link** (⌁) in the toolbar, **Heat Flow Network (Radiation Exchange)** in the **Analysis** panel | [Heat flow](#thermal-network-steps) |
| Vegetation indices | **Vegetation Index (Multispectral)** at the top of the **Analysis** panel, with a multispectral orthomosaic selected | [Vegetation indices](#thermal-vegetation-steps) |
| Side-by-side documents | **📄 Side-by-side…** in the top bar | [Side-by-side](#thermal-deliverables-side-by-side) |
| Temperature export (TIFF, CSV) | **🌡 Export temperatures…** in the top bar | [Temperature export](#thermal-deliverables-temperature-export) |
| Claim package | **📦 Claim package…** in the report builder's header | [Claim package](#claim-package-steps) |
| Thermal inspection report and inspection bundles | **📄 Report** in the top bar, then **Open report builder…** or **Import inspection bundle…** | [Thermal report](#thermal-report-steps) |
| Linework export (DXF, GeoJSON, ODL XML) | **📐 Export linework…** in the top bar | [Exporting linework](#mapping-deliverables-exporting-linework) |

<a id="thermal-start-before-you-start"></a>

### Before you start

- You need the desktop app for Windows. The web and Android versions have no add-ons, so they have no Thermal tab; their Add-ons window reads "Add-ons are available in the desktop app only."
- You need the Thermal add-on installed and enabled. Steps 1 to 4 below do that once.
- For temperatures you need radiometric files: a DJI or FLIR-format R-JPEG (`.jpg`), an Autel 640T radiometric TIFF, or a per-pixel temperature CSV. Ordinary photos and videos can be imported too, but they carry no temperatures.

<a id="thermal-start-steps"></a>

### Steps

1. Open **Settings** (the gear at the top of the sidebar) and click **Open Add-ons**. The **🧩 Add-ons** window lists the **Thermal Analysis Studio**.
2. If it reads **Not installed**, click **Download installer…**, run `OpenDroneLog-Thermal-Addon_<version>_x64-setup.exe`, then click **↻ Refresh** in the window.
3. Make sure **Enabled** is ticked. A **Thermal** tab appears in the sidebar.
4. Open the **Thermal** tab. The top bar shows **🌡️ Thermal Studio** and two badges:
  - **DJI Thermal SDK ready** (green): DJI R-JPEGs can be measured. **DJI SDK unavailable** (red) means the SDK runtime from the add-on is missing; hover the badge to read why. Run the add-on installer again.
  - **FLIR · Skydio · Autel built in** (blue): FLIR-format R-JPEGs (Teledyne FLIR, Skydio X10, Autel 640R), Autel 640T TIFFs and temperature CSVs are read without any SDK.
5. Look at the layout:
  - Left: the library, headed `Assets (N)`, with the search box and **Filters** above the rows.
  - Centre, top: the toolbar with the annotation tools, **📝 Note**, and the **Measure** group with **🧭 Scale**, **🧮 Material Takeoff**, **Spot**, **ΔT** and **⛶ Boundary**. **🧭 Scale** and **🧮 Material Takeoff** each open a window over the picture, near its top-left corner, a little below the zoom buttons; drag it by its title bar and resize it at its bottom-right corner (see [Giving a picture a scale](#measure-scale-steps)).
  - Centre: the viewer with the picture, the zoom strip (**Fit**), the cursor readout and the min and max markers. Under it the info strip and, for a thermal picture, the **Visual twin** row.
  - Right: the **Analysis** panel with its sections (statistics, spot readings, palette, isotherm, measurement parameters, variance analysis, heat flow).
  - Top right: **+ Import photos / videos**, **📂 Import folder…**, **🌡 Radiometric file…**, **⇄ Pair pictures**, **📄 Side-by-side…**, **🌡 Export temperatures…**, **📐 Export linework…** and **📄 Report**.

<a id="thermal-start-importing"></a>

### Importing

1. Click **+ Import photos / videos** (or **Import photos / videos** in the empty viewer). The file dialog opens.
2. Pick one or more files and confirm. While they are imported the button reads `Importing 3 of 10…`. Accepted: pictures `.jpg`, `.jpeg`, `.png`; videos `.mp4`, `.mov`, `.avi`; Metashape exports `.tif`, `.tiff`, `.pdf`, `.xml`, `.csv`, `.las`, `.laz`, `.ply`, `.obj`, `.kml`, `.kmz`.
3. Or drag files from your file manager onto the studio. The overlay reads "Drop thermal photos/videos or Metashape exports to import". Dropped `.csv` files are skipped, so flight logs dropped by mistake are not filed as pictures.
4. Wait for the list. The first new file is selected and its temperatures load (**Processing…** shows in the top bar).
5. Check the subtitle under the name. R-JPEGs are recognised from their content, whoever made them: the row reads, for example, `FLIR R-JPEG 640×480` or `DJI R-JPEG 640×512`. A plain photo reads `Image`, a video `Video`.
6. For an Autel 640T `.tif` or a temperature `.csv` exported from FLIR Thermal Studio or the Autel IR tool, click **🌡 Radiometric file…** instead. The dialog "Import radiometric data" accepts `.tif`, `.tiff`, `.csv`, `.txt`, `.jpg` and `.jpeg`, and files them as temperatures. Through the normal import a `.tif` or `.csv` is filed as temperatures only when it clearly is one (an ungeoreferenced single-band TIFF of at most 2048 px a side holding tenths of a kelvin or °C values, or a numeric matrix of at least 64×48 values in °C); anything else becomes a Metashape export.
7. Read any red bar under the top bar. Each file that could not be imported has a line there, for example `This file was already imported as "…"`. Close it with **✕**.

Metashape exports land in the same library: an orthomosaic or elevation model (DEM) shows as a picture you can annotate and measure, a multispectral orthomosaic can produce vegetation indices, and a PDF, XML, CSV, point cloud or KML/KMZ opens as a card with **Open in default application**.

A video plays in the viewer. To work on one moment, pause it and click **Capture frame** (top right of the picture). The frame is imported as a new PNG picture named `<video>_frame_<n>.png`. DJI thermal videos carry no radiometric data, so the frame has colours but no temperatures; measuring and annotating still work.

<a id="thermal-start-the-asset-library"></a>

### The asset library

1. Click a row to select it. The viewer and the **Analysis** panel load that picture; the row's **✏️** and **🗑** buttons stay visible on the selected row (on other rows they appear on hover).
2. Find pictures by name: type part of a name into the search box (`Search by name`) under the `Assets (N)` header. The list keeps the rows whose name contains the text, whatever the case.
3. Click **Filters** for more criteria. Each one you set narrows the list further:
  - the type chips, one per type in the library with its count, for example `JPG (12)`, `GeoTIFF (2)` or a Metashape kind such as `Orthomosaic (GeoTIFF) (1)`; click several to show any of them, click a chip again to drop it;
  - **Size (MB)**: a `min`, a `max` or both; a picture whose file cannot be found has no size and is hidden while a size is set;
  - **Captured**: a from date and, under it, a to date, both days included; a picture without a capture time counts by the day it was imported, and one with neither is hidden while a date is set;
  - **Camera** and **Dimensions**: pick one of the cameras or picture sizes in the library, for example `FLIR SC660 (3)` or `640 × 480 (3)`; `Any` drops the criterion. Each list is there only when the library has such values.
4. Read `Showing N of M` at the bottom of the filter bar, for example `Showing 12 of 140`. While the search box or a filter is set, **Clear filters** appears beside it; click it to empty both and see every row again. The filter is not saved: it starts empty each time you open the studio.
5. Tick the checkbox of each picture you want to delete; every row has one, documents included. Ticking does not open the picture. Or tick **Select all** under the filter bar: it ticks only the rows the filter shows. It shows a dash while only some of them are ticked; a click then ticks them all, and a click on a full tick clears them. `3 selected` beside it counts the ticks. When you change the filter, the ticks on rows it hides are dropped, so a delete never touches a picture you cannot see.
6. Click **Delete selected…** under it (greyed out while nothing is ticked). One question names the count, the pictures queued in the report (they leave the queue) and the Metashape files among them, for example `Delete 5 pictures from the library? Their files, annotations and measurements are removed. 1 is queued in the report and leaves the queue. 1 is a Metashape file shared with the Photogrammetry Studio.` Cancelling it deletes nothing.
7. Wait while the line under the button reads `Deleting 120 of 357…`. Meanwhile **Select all**, **Delete selected…**, the import buttons, **⇄ Pair pictures**, the note, renaming and the 🗑 buttons are greyed out, and dropped files are not taken. When it is done the ticks are cleared, the list reloads and the line reads `Deleted 357 of 357`. If some could not be deleted it reads `Deleted 355 of 357; 2 failed: <first error>`: the others are gone, the failed ones stay in the list. The row checkboxes stay live, but the delete takes the ticks you confirmed; ticks you change meanwhile are cleared when it ends. When some files of the deleted pictures could not be removed, the line ends `; 2 files were left in the app's data folder` (`; 1 file was left …` for one). A bulk delete that is refused because an import is still running reads `Nothing was deleted: another delete or an import is running.`
8. Rename a picture: double-click its name, or click **✏️**. Type the new name and press Enter (Esc cancels). The extension is kept and shown beside the box; the name is the one printed in reports, the stored file keeps its own name. If a filter hides the picture, renaming it from the info strip's **✏️** clears the filter first.
9. Delete one picture: click **🗑** on the row, or **🗑 Delete** in the info strip. Confirm `Delete "<name>" from the thermal library? The file, its annotations and measurements are removed.` When the picture is queued in the report, the question reads `Delete "<name>" from the thermal library? The file, its annotations and measurements are removed, and it leaves the report figure queue.` If files could not be removed or the queue could not be saved, the studio's error banner says so after the delete, for example `Deleted. 1 file could not be removed from the app's data folder (<name>); another program may be using it.` or `Deleted, but the report figure queue could not be saved: <error>`.
10. Read the info strip under the picture: the file name, the camera model, for FLIR files `S/N …` and `lens …`, how a TIFF or CSV was read, the format in green (or `Not radiometric`), `📍` with the GPS position, and the capture time.
11. Add a note: click **📝 Note** in the toolbar. Type the observed condition, context or follow-up into the box. The note is saved with the picture, printed under it in reports, and the button shows ` ●` while a note exists.

The row icons tell you the kind: 🌡️ radiometric, 🖼️ plain picture, 🎬 video, 🗺️ Metashape raster, 📄 Metashape document.

<a id="thermal-start-pairing-thermal-and-visual-pictures"></a>

### Pairing thermal and visual pictures

A drone that shoots a thermal frame also shoots a visual twin: a wide picture, a zoom picture, or both. The studio can link each thermal picture to its twins, so reports and side-by-side documents show the right pair.

1. Import the thermal and the visual pictures together, by any import button or by dropping them on the studio. Pairing runs at the end of the import, and the notice gains "· N pairs". If the pairing fails, the notice says "Pairing failed" and the pictures stay imported.
2. Or click **⇄ Pair pictures** in the top bar at any time. The notice reads "Paired N thermal pictures; M have no twin". The button is greyed out while an import, a pairing or a bulk delete runs, and while the capture tags of the pictures are being read (its tooltip then says so).
3. A picture with a twin shows a ⇄ badge after its name in the library; hover it to read, for example, "Paired with DJI_0001_W.JPG (wide)". Select the thermal picture: the **Visual twin** row under the info strip names the twin the documents show and its slot, for example `DJI_0001_W.JPG · wide`.
4. With no twin the row reads "No visual twin". Click **Pair with…**: a list titled `Pair <name> with…` opens. Type into `Filter by name…` and click the visual picture. The pictures taken closest in time to the thermal picture come first.
5. When there are two twins, **Use zoom** or **Use wide** chooses which one the documents show. **Change…** picks a different picture for the shown slot. **Unpair** removes the link.

The rules, in plain words: first the file names (`DJI_0001_T` goes with `DJI_0001_W` as wide and `DJI_0001_Z` as zoom); then the capture time, when the pictures were taken within about two seconds of each other and by the same camera; the zoom is the picture with the longer focal length. A picture is the twin of only one thermal picture.

> **Tip** A pair you made or removed by hand never changes on its own, not on the next import and not on **⇄ Pair pictures**. A twin imported later is not added to it. To give such a picture a new twin, click **Unpair**, then **Pair with…**; **Change…** only replaces the picture in the slot the row shows.

<a id="thermal-start-example-a-flir-picture-from-import-to-findings"></a>

### Example: a FLIR picture from import to findings

You import the public FLIR SC660 sample `IR_2412.jpg` with **+ Import photos / videos**.

- The row reads `FLIR R-JPEG 640×480`; the info strip reads `FLIR SC660`, `S/N 404003980` and `lens FOL38`.
- **Temperature Statistics** shows Min 22.7 °C, Max 35.3 °C, Mean 28.3 °C, so Δ (max−min) reads about 35.3 − 22.7 = 12.6° (the box rounds the unrounded difference).
- **Detect anomalies** with the default sensitivity finds 7 regions against a baseline (median) of 29.0 °C.
- You rename it `Office wall east`, type a note, and later add it to a thermal report.

<a id="thermal-start-tips-and-common-mistakes"></a>

### Tips and common mistakes

- A red **DJI SDK unavailable** badge only affects DJI R-JPEGs. FLIR-format pictures, TIFFs and CSVs still measure. Rerun the Thermal add-on installer to restore the SDK.
- An Autel TIFF or CSV that lands as `Orthomosaic (GeoTIFF)` or `Camera Reference (CSV)` went through the normal import. Delete it and import it again with **🌡 Radiometric file…**.
- The same file cannot be imported twice: files are recognised by their content, not their name. Renaming a file on disk does not get around this, and you do not need to.
- A frame captured from a DJI thermal video has no temperatures. For measurements, take R-JPEG stills in flight.
- Deleting removes the annotations, measurements, note and heat-flow network of that picture as well. There is no undo, for **Delete selected…** either: check `Showing N of M` before you tick **Select all**.

> **Under the hood**
> Imported files are copied into the active profile's data folder and deduplicated by their SHA-256 hash; the original on your disk is not touched. EXIF GPS position, capture time and camera model are read from every picture, and FLIR files add the camera model, serial number and lens from their FLIR data. DJI R-JPEGs are measured by the DJI Thermal SDK (`dirp_measure_ex`); FLIR-format files by a native Planck model of the raw counts; Autel 640T TIFFs are 16-bit values in tenths of a kelvin (°C = value × 0.1 − 273.15); CSV matrices are read as °C (header lines, a row-index column and missing cells are handled; decimal commas only with `;` or tab delimiters; kelvin values are converted only when you import through **🌡 Radiometric file…**). For TIFF and CSV imports the temperatures are kept as a raster beside the file and a palette-rendered preview is shown. Everything stays on your computer; only the AI narrative and AI drafts send data out, and only when you click them.

<a id="thermal-start-see-also"></a>

### See also

- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Heat flow network: nodes, conductors, solving](#thermal-network)
- [Vegetation indices from multispectral orthomosaics](#thermal-vegetation)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Side-by-side documents and temperature exports](#thermal-deliverables)
- [Viewing and annotating pictures](#annotate)
- [Giving a picture a scale](#measure-scale)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-analysis"></a>

## Reading temperatures: statistics, palette and scale, emissivity and distance


The **Analysis** panel shows the temperature statistics of the selected picture, its histogram and the colour scale, and lets you correct emissivity and distance. In the viewer you read the temperature under the cursor and see where the hottest and coldest pixels are.

<a id="thermal-analysis-before-you-start"></a>

### Before you start

- The Thermal add-on is enabled and you are in the **Thermal** tab of the desktop app.
- A still radiometric picture is selected: its library row has the 🌡️ icon and a subtitle such as `FLIR R-JPEG 640×480`. Plain pictures and videos show "Select a radiometric image or vegetation index to see value analysis."
- For DJI R-JPEGs the **DJI Thermal SDK ready** badge is green.

<a id="thermal-analysis-steps"></a>

### Steps

1. Select the picture in the library. **Processing…** shows briefly in the top bar, then **Temperature Statistics** fills in.
2. Read the six boxes: **Max**, **Min**, **Mean**, **Median**, **Std Dev** and **Δ (max−min)**.
3. Look at the histogram under them: the bars run from the coldest to the hottest pixel. Hover a bar to see its temperature and how many pixels fall in it (`<temperature>: <count> px`). A tall narrow peak is a uniform surface; a second peak is a second material or a warm area.
4. Move the mouse over the picture. The readout at the bottom left shows `(x, y) · temperature`, plus the position when the picture is georeferenced.
5. Find the markers on the picture: the red `+` with its temperature is the hottest pixel, the blue `+` the coldest.
6. To keep a reading on the picture, pick **Spot** (🌡) at the end of the toolbar's **Measure** group and click a point, or pick **ΔT** (±) and click two points (or drag from one to the other). The labels read `S1 34.2 °C` and `ΔT1 +6.2 °C`, the second point minus the first, and the **Spot readings** section under **Temperature Statistics** lists them with their pixel coordinates (see [Spot readings](#thermal-deliverables-spot-readings)).
7. Open **Palette & Scale** and click a palette: **Iron Red**, **White Hot**, **Black Hot**, **Rainbow**, **Arctic** or **Medical**. The colour bar under the buttons shows the palette with its low and high end.
8. Set the scale. **Auto** spreads the palette from the picture's min to its max. To fix it, type a low and a high value into the two boxes beside **Auto** (the greyed placeholders show the auto values). Pixels below the low end take the coldest colour, pixels above the high end the hottest. Click **Auto** to go back.
9. Change the unit if you need it: open Settings, then **Units**, and set **Temperature** to °C or °F. Every temperature in the panel, the readout, the markers and the reports follows; typed scale values are read in the unit shown.

<a id="thermal-analysis-measurement-parameters"></a>

### Measurement parameters

These are the inputs of the camera's temperature model. Change them when the camera's defaults do not match the surface you inspect.

1. Check that the picture is a DJI or FLIR-format R-JPEG. Autel TIFFs, temperature CSVs and vegetation indices hold final values, so the section is absent for them.
2. Click **Measurement Parameters** to open it (it starts closed).
3. Type the **Emissivity** of the surface, between 0.1 and 1 in steps of 0.01. The box starts with the value stored in the file, or the value you last typed in this session.
4. Type the camera-to-object **Distance (m)**, or **Distance (ft)** when your distance unit is imperial. You can write `12`, `12 m` or `40 ft`.
5. Read **Humidity:** and **Reflection:** under the boxes. They are the values stored in the file and cannot be changed here.
6. Click **Re-measure** (the section is offered only for pictures with measurement parameters). The temperatures are computed again; the statistics, histogram, markers and readout update, and any anomaly results are cleared because they belonged to the old temperatures.

Spot and ΔT values follow the emissivity and distance you set here. Side-by-side documents and temperature exports for a batch of pictures use each picture's own parameters unless you tick **Apply the current parameters (e, d, r, h, ambient) to every picture**. The thermal report's box of that name starts ticked, so a report uses these parameters unless you untick it. See [Side-by-side documents and temperature exports](#thermal-deliverables-spot-readings).

<a id="thermal-analysis-example-a-flir-sc660-picture"></a>

### Example: a FLIR SC660 picture

With the FLIR sample `IR_2412.jpg` selected (640×480 pixels):

| Box | Value |
|---|---|
| **Min** | 22.7 °C |
| **Max** | 35.3 °C |
| **Mean** | 28.3 °C |
| **Δ (max−min)** | about 35.3 − 22.7 = 12.6° |

The file's own parameters show as emissivity 0.95, distance 1 m, **Humidity:** 50% and **Reflection:** 20.0 °C. With **Auto** the Iron Red palette runs from 22.7 °C (darkest) to 35.3 °C (brightest). Typing `26` and `32` into the scale boxes spreads all colours over those 6 degrees, so differences of a few tenths become visible on the wall, while everything below 26 °C turns uniformly dark.

Switch **Temperature** to °F and the same Max reads 35.3 × 9/5 + 32 = 95.5 °F; the Δ reads 12.6 × 9/5 = 22.7° (a difference has no 32 offset).

<a id="thermal-analysis-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Shiny metal (bare aluminium, galvanised steel, polished pipes) has an emissivity of about 0.1 to 0.3 and mostly reflects the sky or nearby warm objects. A reading on it with the default 0.95 is far too low or simply wrong. Put matt tape or paint on the spot, or measure a painted part nearby.
- Reflections move when you move: if a hot spot shifts between two pictures taken from different angles, it is a reflection, not a defect.
- **Auto** stretches the palette over the whole picture (or over the working area when an analysis boundary is set). A hot chimney or the sun on a skylight then squeezes the wall into a few colours and hides small differences. Set the scale by hand around the temperatures of the surface you inspect.
- Emissivity and distance typed here stay in force for the next pictures you open in this session; they are not saved with the picture. They also apply to the anomaly detection and to every picture pair of an exported thermal report. Check the box values when you change to a different surface.
- **Std Dev** and **Δ (max−min)** are differences. In °F they are multiplied by 9/5 without the 32 offset, so do not convert them like temperatures.
- With an analysis boundary on the picture, the statistics, the histogram, the markers and the automatic palette range come from inside its outlines only; see [the analysis boundary](#thermal-boundary).

> **Under the hood**
> DJI R-JPEGs are measured by the DJI Thermal SDK (`dirp_measure_ex`), which applies the emissivity, distance, humidity and reflected temperature; FLIR-format files go through a native Planck model of the raw counts with the camera's calibration constants, plus the same object parameters and the atmosphere between camera and object. The values are refused outside the model's range (emissivity 0.1 to 1). TIFF and CSV imports are stored as final °C values. The statistics are computed over every valid pixel: the mean and the standard deviation over all of them, the median from every n-th pixel with n = ⌊pixels ÷ 65,536⌋ (65,536 to 131,071 samples; pictures smaller than that use every pixel), the histogram in 96 equal bins from min to max. The temperatures are kept in °C and metres internally; only what is shown or typed follows Settings → Units. For the accuracy see the camera's data sheet (and expect worse when the emissivity or the reflected temperature are wrong).

<a id="thermal-analysis-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
- [Side-by-side documents and temperature exports](#thermal-deliverables)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Heat flow network: nodes, conductors, solving](#thermal-network)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-isotherm"></a>

## Isolating a temperature range (isotherm)


An isotherm shows only the pixels between a low and a high temperature, so you see at a glance where a surface is warmer (or colder) than a limit. The panel counts those pixels, gives their share of the picture and their min, mean and max, and can restrict the anomaly search to them.

<a id="thermal-isotherm-before-you-start"></a>

### Before you start

- You are in the **Thermal** tab of the desktop app with the Thermal add-on enabled.
- A still radiometric picture (or a vegetation index) is selected and its **Temperature Statistics** are filled in.
- Know roughly which temperatures matter: read **Min**, **Max** and **Mean** first (see [Reading temperatures](#thermal-analysis)).

<a id="thermal-isotherm-steps"></a>

### Steps

1. Open **Range Isolation (Isotherm)** in the **Analysis** panel (it is open by default).
2. Tick **Isolate a temperature range**. The **Low** and **High** rows appear, set from the picture's mean to its max, each rounded to 0.1.
3. Drag the **Low** slider, or type a value in its box, to the lowest temperature you want to keep.
4. Drag or type **High** to the highest temperature. **Low** cannot pass **High**; the sliders reach at least one degree beyond the picture's min and max, rounded to whole degrees.
5. Choose the display after **Display:**
  - **Highlight**: pixels in the range keep their palette colour, all others turn dim grey, so you still see the building around them.
  - **Solo**: pixels outside the range turn almost black, so only the range is visible.
6. Read the box under the buttons: `Pixels in range: N (x%)` and `Range min/mean/max: …`. In the histogram the bars inside the range turn sky blue.
7. To search only this range for anomalies, keep the isotherm on and click **Detect anomalies** in **AI Variance Analysis**. The section says "Analysis will be restricted to the isolated range …".
8. Untick **Isolate a temperature range** to see the full picture again.

<a id="thermal-isotherm-example-warm-areas-on-a-flir-picture"></a>

### Example: warm areas on a FLIR picture

The FLIR sample `IR_2412.jpg` has **Min** 22.7 °C, **Max** 35.3 °C and **Mean** 28.3 °C.

1. When you tick **Isolate a temperature range**, **Low** starts at 28.3 and **High** at 35.3, so you already see every pixel warmer than the mean.
2. You raise **Low** to 32.0 to keep only the warmest areas and click **Solo**.
3. The box now gives the count and share of pixels between 32.0 °C and 35.3 °C. The numbers depend on the picture; if it reads, say, 15,360 pixels, that is 15,360 ÷ (640 × 480) = 15,360 ÷ 307,200 = 5.0 %.
4. `Range min/mean/max:` tells you how warm that area is on average, which is the number to quote, rather than the single hottest pixel.

<a id="thermal-isotherm-tips-and-common-mistakes"></a>

### Tips and common mistakes

- The isotherm is reset each time you select another picture: the checkbox goes off and **Low** and **High** start again at that picture's mean and max. Write down the limits if you want the same range on several pictures.
- The share `(x%)` is of all pixels of the picture, sky and background included. Crop the scene in flight, or compare counts rather than percentages between pictures.
- With the isotherm on, **Detect anomalies** only looks at pixels inside the range. A cold spot below **Low** is not found. Turn the isotherm off for a full search.
- Highlight and Solo change only the display. The statistics boxes above still describe the whole picture, or the working area when an analysis boundary is set.
- The limits follow Settings → Units → Temperature. In °F the slider steps are still 0.1 of the shown unit.
- With an analysis boundary, `Pixels in range` counts and divides inside its outlines only, and bounds you set stay when you change it; see [the analysis boundary](#thermal-boundary).

> **Under the hood**
> A pixel is in range when Low ≤ T ≤ High (both ends included). The count, the min, the max and the mean are computed over those pixels only; the share is count ÷ (width × height) × 100, or, with an analysis boundary, count ÷ the pixels of the working area that hold a value × 100. In Highlight mode an out-of-range pixel gets a grey level of 30 + 120 × its position on the colour scale (0 to 1), so warmer pixels stay lighter grey; in Solo mode it is drawn near black. The histogram has 96 bins; a bin is coloured when its centre lies in the range. When the anomaly search is restricted, the baseline (median) and σ are still those of the whole picture: only the pixels that may form a region are limited to the range. Nothing is saved: the range lives only while the picture is selected.

<a id="thermal-isotherm-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Vegetation indices from multispectral orthomosaics](#thermal-vegetation)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-boundary"></a>

## Analysing part of a thermal picture: the analysis boundary


An analysis boundary is an outline drawn on a thermal picture around the item or items you want to analyse. The statistics, the isotherm's pixel count and range figures, the palette range and the AI analysis then read only inside it, so a hot sky or a warm roof next door no longer decides the numbers. You can draw one outline or several: their union is the working area. There are no exclusion outlines, so to leave something out, outline what is around it.

<a id="thermal-boundary-before-you-start"></a>

### Before you start

- You are in the **Thermal** tab of the desktop app with the Thermal add-on enabled.
- A still radiometric picture (or an index raster) is selected and has loaded. On any other picture **⛶ Boundary** is greyed out; hover it to read why. On a video it reads `Measurements need a still picture (annotations are per asset, not per video frame)`. On a still picture without a loaded temperature matrix it reads `Spot, ΔT and Boundary read temperatures: they need a radiometric picture (or an index raster) that has loaded`.
- The picture's annotations have loaded. While they load, or when they could not be read, the picture is read-only and the tools fall back to pan and zoom.

<a id="thermal-boundary-steps"></a>

### Steps

1. Click **⛶ Boundary** in the **Measure** group of the toolbar. Hover it to read `Boundary — outline the item or items to analyse: statistics, isotherm, palette range and the AI analysis read only inside the outlines`. The shape chooser, the same as for **⬠ Area**, appears beside it.
2. Choose the shape with the three icon buttons of the chooser, ⬠ (polygon), ▭ (rectangle) and ◯ (circle). Hover a button to read what it does: `Polygon — click the corners`, `Rectangle — click two opposite corners, or drag (sides along the picture's edges)` or `Circle — click the centre, then a point on the rim, or drag from the centre`.
3. For a polygon, click the first corner on the picture. A hint above the cursor readout reads `Click the next corner · click the first corner, double-click or press Enter to finish · Backspace removes the last · Esc cancels`.
4. Click the other corners one by one. **Backspace** removes the last corner you placed; **Esc** cancels the outline.
5. Finish the polygon by clicking its first corner, by double-clicking, or by pressing **Enter**. A dashed outline stays, labelled `Boundary 1`, and everything outside it is shaded.
6. For a rectangle, click two opposite corners (the hint reads `Click the opposite corner · Esc cancels`) or drag from one corner to the other. For a circle, click the centre and then a point on the rim (the hint reads `Click a point on the rim · Esc cancels`), or drag from the centre.
7. Read the line at the top of **Temperature Statistics** (on an index raster the section is headed **Index Statistics**) in the **Analysis** panel, for example `Inside the analysis boundary: 1 outline, 30,000 px (9.8 % of the picture)`. While the picture is measured again, `Updating…` shows and the statistics, the palette labels and the isotherm box are dimmed until the new numbers arrive.
8. To add another item, draw another outline with the same tool. The next one is labelled `Boundary 2`, and the line then reads `2 outlines`. Outlines that overlap or sit inside each other count once.
9. To move an outline, click **Select** (↖), click the outline itself (a click inside it still selects the spot or measurement under the cursor), and drag it.
10. To remove one, click **Select** (↖), click the outline and press Delete, or drag the **Erase** tool (⌫) across its line (it only catches the outline, not the inside of the shape). The whole outline goes.
11. Click **↩ Undo** to remove the last annotation you drew, boundary or not. It does not bring back an outline you erased. With no boundary left, the numbers are those of the whole picture again.

A shape that is too small is dropped when you finish it: a rectangle less than 1 pixel wide or high, or a circle with a radius under 2 pixels. A polygon is dropped only when it has fewer than three distinct corners or no area at all; a thin hand-drawn sliver is kept. Nothing is stored and the picture is unchanged.

Drawing, moving or erasing a boundary clears the detected anomalies and retires the AI narrative, which then reads `The analysis changed; write the narrative again.` Run **Detect anomalies** and write the narrative again afterwards.

If measuring again fails, the numbers of the earlier outline are not shown. The statistics are replaced by `The analysis could not be updated; use Try again in the Analysis panel.`, the palette labels are blank, `Pixels in range` reads `—`, and the studio's error banner above the picture says why. The same line and **Try again** also appear when the very first analysis of a picture fails, for example one that arrives with more outlines than the limit. Click **Try again** (hover it to read `Run the analysis again`) under that line; it is there for every kind of picture and runs the analysis again for the boundary as it is. If the banner says the boundary itself was refused (for example too many outlines or corners), **Try again** fails again until you change the boundary; changing or erasing an outline starts a new analysis by itself.

<a id="thermal-boundary-what-follows-the-boundary"></a>

### What follows the boundary

With at least one outline, the working area is every pixel whose centre lies inside an outline. These follow it:

| What | With a boundary |
|---|---|
| **Temperature Statistics** (**Index Statistics** on an index raster), the histogram and the min and max positions | Computed over the working area only |
| The min and max markers on the picture | Lie inside it, because they follow the statistics |
| The isotherm's `Pixels in range` and its range min, mean and max | Counted over the working area only; the share is divided by the working area's pixels that hold a value, not by every pixel of the picture |
| The isotherm's starting **Low** and **High** | Set from the working area's mean and max when the picture is first analysed with the boundary already on it; a boundary drawn later leaves them where they are |
| The automatic palette range | The working area's min and max, in the viewer, the report figure and the side-by-side colour bar. Pixels outside clamp to the ends of the palette; reports and the side-by-side then print `≤` and `≥` on the colour bar's end labels and end the scale line with ` (inside the analysis boundary)`. A range you typed still wins |
| **Detect anomalies** | Baseline and σ from inside the outlines; findings only inside |
| The AI narrative | The picture the AI sees is grey outside the outlines, and it is told the numbers were taken inside a boundary |
| Anomaly entries brought into the thermal report with **⚡ Import detected** | Each one printed with `Detected inside the analysis boundary (14.7 % of the picture)`; an entry added with **+ Manual entry** carries no such line |
| The side-by-side Min, Max and Mean rows, on a picture with spots or ΔT | Labelled `(inside the analysis boundary)` |

The outline is also drawn on report figures, side-by-side sheets and claim-package figures whenever annotations are drawn there. Whether it is drawn or not, it governs the numbers.

<a id="thermal-boundary-what-does-not"></a>

### What does not

- **Spot** and **ΔT** readings, and the cursor readout, stay where you place them: a spot outside the outline still reads its own temperature.
- The Heat Flow Network is solved as you built it. Its nodes are placed by you, and an outdoor or sky reference usually sits outside the building, so the boundary does not limit them. The AI is told the nodes are placed by you.
- The **Highlight** and **Solo** display of the isotherm still covers every pixel of the picture that is in the range, outside the outlines too; only the figures are limited.
- **🌡 Export temperatures…** writes the whole picture: it is a copy of the data, not a calculation.
- A vegetation index you compute makes a new picture with its own annotations; it does not inherit the boundary.

<a id="thermal-boundary-when-nothing-is-inside"></a>

### When nothing is inside

Two cases leave nothing to measure. In both, no statistics, histogram or markers appear, `Pixels in range` reads `—`, and **Detect anomalies** and the narrative are greyed out (hover **Detect anomalies** to read why).

- The outline holds no data but the picture does, for example an outline drawn off the picture, or an index raster with only nodata inside. The panel says `No data inside the analysis boundary`. The palette and its labels use the whole picture, and the side-by-side prints the same sentence instead of its Min, Max and Mean rows.
- The picture has no valid value at all, with or without a boundary. The panel says `No data in this picture`, and the report figure and the side-by-side show a grey placeholder with no numbers on its colour bar.

<a id="thermal-boundary-a-damaged-or-unreadable-boundary"></a>

### A damaged or unreadable boundary

A stored boundary can be damaged (fewer than three valid corners), or the picture's annotations can fail to load. Calculations are then refused rather than guessed, and the panel says why:

- `1 analysis boundary on this picture is damaged (fewer than three valid corners)`, or `2 analysis boundaries on this picture are damaged (fewer than three valid corners)` for two. Click **Remove damaged boundaries** under the sentence to delete them; valid outlines stay.
- `This picture's annotations could not be read, so its analysis boundary is not known: <reason>`, or `The picture's annotations are still loading.` while they load.

A notice under the studio's error banner also tells you. When the last changes are not saved it reads `The last changes to this picture are not saved: <reason>`; when the annotations could not be read it reads `This picture is read-only until its annotations load: <reason>`. Click **Retry** to try again. When changes are unsaved, **Discard my unsaved changes** shows the stored copy instead.

In a report or a side-by-side, a picture whose boundary cannot be read is not printed full-frame. It is printed as stored, without its temperatures, with the note `The analysis boundary of this picture could not be read, so its temperatures were left out.` or, for unsaved changes, `The last changes to this picture's annotations are not saved, so its temperatures were left out.` When the last changes to a pair's visual picture are not saved, the pair carries `The last changes to the visual picture's annotations are not saved; it is printed as stored.`

<a id="thermal-boundary-example-a-house-and-a-shed-on-a-flir-picture"></a>

### Example: a house and a shed on a FLIR picture

A FLIR picture is 640 × 480 pixels, 307,200 in all. The temperatures below are illustrative; the pixel counts follow from the rule and hold for corners on whole pixels, so a rectangle drawn by hand gives nearby numbers.

1. You click **⛶ Boundary**, choose the rectangle and outline the house from (100, 120) to (300, 270): 200 × 150 = 30,000 pixels. The line reads `Inside the analysis boundary: 1 outline, 30,000 px (9.8 % of the picture)`, because 30,000 ÷ 307,200 = 9.8 %.
2. You outline the shed from (400, 200) to (460, 250): 60 × 50 = 3,000 pixels. The line reads `Inside the analysis boundary: 2 outlines, 33,000 px (10.7 % of the picture)`, because 33,000 ÷ 307,200 = 10.7 %.
3. **Temperature Statistics** now describe those 33,000 pixels only. Say they read Min 21.0 °C, Max 41.0 °C, Mean 29.5 °C (illustrative); the sky and the lawn no longer pull them.
4. You tick **Isolate a temperature range** and the box reads `Pixels in range: 1,650 (5.0%)` (illustrative): 1,650 ÷ 33,000 = 5.0 %, a share of the working area, not of the 307,200 pixels (all 33,000 hold a value on a FLIR picture).
5. You click **Detect anomalies**. A finding it imports into the thermal report prints `Detected inside the analysis boundary (10.7 % of the picture)`.

<a id="thermal-boundary-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Draw the outline a little inside the item's edge: a pixel counts when its centre is inside, so the edge pixels that blend with the background stay out of the numbers.
- A boundary is stored with the picture's annotations and stays when you reselect the picture. Remove it to analyse the whole picture again.
- The share in the boundary line is of the whole picture; the share in `Pixels in range` is of the working area's pixels that hold a value. They are different denominators.
- You cannot exclude a hole from an outline. To leave a window out of a wall, draw outlines around the wall pieces instead.
- Spots and ΔT lines are not limited by the boundary: check that the ones you quote lie where you mean.
- If the numbers do not change after an edit, wait for `Updating…` to go; if it never does, read the studio's error banner.

> **Under the hood**
> A pixel is inside when its centre lies inside an outline (even-odd rule for each outline), and the working area is the union of the outlines. A boundary may have 1 to 64 outlines, at most 20,000 corners in all and at most 250,000 runs. The image sent to the AI is the picture grey (`rgb(128, 128, 128)`) outside the working area, re-encoded as a JPEG when the stored preview is a JPEG and sent as a PNG when it is a PNG (an index raster, a TIFF or a CSV import). Statistics, the isotherm and the palette read the same working area, so the colours and the scale labels agree. An older build of the app keeps the boundary in the picture's annotations but computes full-frame values and labels them as full-frame.

<a id="thermal-boundary-see-also"></a>

### See also

- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Side-by-side documents and temperature exports](#thermal-deliverables)
- [Heat flow network: nodes, conductors, solving](#thermal-network)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-anomalies"></a>

## AI variance analysis, the AI narrative, and the provider key


**AI Variance Analysis** finds the regions of a picture that are clearly hotter or colder than the rest, grades them and suggests what they may be. The optional AI narrative turns the measured data into written findings, using an AI provider and a key you set in Settings.

<a id="thermal-anomalies-before-you-start"></a>

### Before you start

- You are in the **Thermal** tab of the desktop app with the Thermal add-on enabled.
- A still radiometric picture (or a vegetation index) is selected and its **Temperature Statistics** (**Index Statistics** for an index) are filled in.
- For the narrative only: an internet connection and either the Chat connection (set in the **Chat** tab under **Connection**, one key for Chat and the add-ons) or an own key from Claude (Anthropic), OpenAI or Google Gemini; see [AI provider keys](#thermal-anomalies-ai-provider-keys).

<a id="thermal-anomalies-detecting-anomalies"></a>

### Detecting anomalies

1. Open **AI Variance Analysis** in the **Analysis** panel (it is open by default).
2. Set **Sensitivity (z-score)**. The default `2.0` flags pixels at least 2 standard deviations away from the typical temperature of the picture. Raise it (`3`, `4`) for fewer, stronger findings; lower it (`1.5`) for more. The range is 0.5 to 8.
3. Set **Min region (px)**, the smallest patch that counts as a finding. The default is `24` pixels; raise it to ignore specks and single hot pixels.
4. Click **Detect anomalies**. The button reads **Analyzing…** while it runs.
5. Read the summary line: `Baseline (median): … · σ = … · N findings`, or "No significant anomalies at this sensitivity."
6. Read the finding cards, most significant first. Each shows:
  - `#1 · 🔥 Hot spot` or `#2 · ❄️ Cold spot` (on a vegetation index `▲ High` or `▼ Low`),
  - a severity badge `low`, `medium` or `high`,
  - a classification: `Electrical Fault`, `Thermal Bridging`, `HVAC Leakage`, `Insulation Void`, `Air Infiltration`, `Moisture Intrusion` or `Missing Insulation`,
  - `Δ:` (region mean minus baseline), `Area:` in pixels, `Max:`, `Min:` and `@ (x, y)`, the centre of the region.
7. Find the regions on the picture: dashed orange boxes for hot spots, dashed cyan boxes for cold ones, each labelled with its `#` number.
8. Change the settings and click **Re-run analysis** to try again, or click **Clear** to remove the results and the boxes.
9. To search only one temperature band, turn on **Isolate a temperature range** first (see [Isolating a temperature range](#thermal-isotherm)). The section then says "Analysis will be restricted to the isolated range …".

<a id="thermal-anomalies-writing-the-ai-narrative"></a>

### Writing the AI narrative

1. Detect anomalies first if you want them interpreted; the narrative also works on the statistics alone.
2. Look at the subheading `AI Narrative (Chat connection)` (or `Claude`, `OpenAI`, `Gemini`): it names the provider chosen in Settings. Without a key the section shows only "Pick an AI provider and add its API key in Settings (below the DJI API key) to generate narrative findings from the image and measured data.", or for the Chat connection "Set the key and model in Chat → Connection (or pick an own key in Settings, below the DJI API key) to generate narrative findings from the image and measured data."
3. Click the purple button. It reads **Generate AI narrative (runs on image + stats)** before a detection, **Generate AI narrative of findings** after one.
4. Wait: the button reads **Analyzing with AI… (can take a minute)**. The text appears below with a summary, findings by `#` number with their ΔT, and prioritised recommendations.
5. Click **Copy** to put the text on the clipboard (it changes to **✓ Copied**), or **Regenerate narrative** for a new version.
6. Check every statement against the picture before you use it. Selecting another picture discards the text.

<a id="thermal-anomalies-ai-provider-keys"></a>

### AI provider keys

1. Open Settings and scroll to **AI providers** (in the left column, below **External agents**). The AI narrative needs the Thermal license; the AI drafts of the report builders work with a Thermal or a Photogrammetry license.
2. Pick the **Provider**: `Chat connection (one key for Chat and the add-ons)`, `Claude (Anthropic)`, `OpenAI (GPT)` or `Google Gemini`. A provider that is ready to use shows ` ✓`.
3. With **Chat connection** nothing is pasted here: the key and the model are the ones set in the **Chat** tab under **Connection** (OpenAI, or any OpenAI-compatible provider such as OpenRouter). Settings then reads "Uses the Chat connection: …" with the model's name. The narrative sends the picture, so pick a model that accepts images.
4. For an own key, click **Get a key** to open the provider's key page in your browser, create a key there and copy it.
5. Paste it into the box (the placeholder shows the key's shape: `sk-ant-...`, `sk-...` or `AIza...`) and click **Save API Key**. The toast reads "AI analysis API key saved" and the status reads "API key configured".
6. To replace a key, paste the new one and click **Update API Key**. To remove it, click the **Personal** badge (it turns into **Remove** on hover).

Keys are kept per profile and per provider: switching the provider keeps each key, and another profile needs its own. The same choice powers the `✨ AI draft` checkboxes in the report builders. A profile where no provider was ever picked uses the Chat connection as soon as it has one, unless it already has an own key: then it keeps that key until you pick **Chat connection**. Once a provider is ready, the AI usage bar appears under the studios and shows what each customer's AI runs cost; see [AI usage](#ai-usage).

<a id="thermal-anomalies-example-a-street-scene-from-the-flir-adas-data"></a>

### Example: a street scene from the FLIR ADAS data

A radiometric TIFF made from a FLIR ADAS frame (640×512, Min −22.4 °C, Max 35.0 °C) is selected. With the defaults (`2.0`, `24`) **Detect anomalies** reports `Baseline (median): 13.6°C · σ = 9.34° · 12 findings`, all cold.

- Finding `#1` (the most significant) has a region mean of −13.5 °C; the median is 13.65 °C before rounding, so `Δ:` is −13.5 − 13.65 = −27.2°. In standard deviations that is −27.2 ÷ 9.34 = −2.9, past the −2.0 limit.
- Its severity is `high` because |Δ| is at least 8 °C.
- It is classified `Air Infiltration` because the region is long and thin. In a street scene a cold, long band like this is most likely the sky: the classification is a rule of thumb for building envelopes and knows nothing about what it looks at.

Raising **Sensitivity (z-score)** to `2.5` and **Min region (px)** to `50` leaves 4 findings.

<a id="thermal-anomalies-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Sky, open windows and shiny roofing are classic false cold or hot spots. Frame the surface you inspect, or isolate its temperature band first.
- With the isotherm on, only pixels inside the range can form regions. A cold spot below **Low** is not found.
- Severity is the higher of a fixed step (4 °C for `medium`, 8 °C for `high`) and a multiple of σ (3.5σ, 6σ). The size of the region plays no part, so a large, mildly cool area can be `low` while a small one is `high`.
- Results are not saved with the picture. Run the detection again after reopening a picture or after **Re-measure**, which clears them. Drawing, moving or erasing an analysis boundary clears them too and retires the AI narrative, which then reads `The analysis changed; write the narrative again.`
- An AI key costs money per request at the provider. Generating a narrative for every picture of a large survey adds up.
- With an analysis boundary, **Detect anomalies** takes its baseline and σ from inside the outlines and reports findings only there, and the AI narrative is sent the picture grey outside them; see [the analysis boundary](#thermal-boundary).
- The narrative can be wrong. It is a draft for a qualified thermographer to check, not a diagnosis.

> **Under the hood**
> Every valid pixel gets z = (T − baseline) ÷ σ, where the baseline is the median of the picture and σ its standard deviation. Pixels with z ≥ +threshold are hot, z ≤ −threshold cold; 4-connected neighbours of the same kind form a region, and regions smaller than the minimum are dropped. ΔT is the region's mean minus the baseline. Severity: high when |ΔT| ≥ 8 °C or |ΔT| ≥ 6σ, medium when |ΔT| ≥ 4 °C or ≥ 3.5σ, else low. Classification, hot: |ΔT| ≥ 10 °C on fewer than 900 px is an electrical fault, an elongated box (width to height above 3 or below 1/3) thermal bridging, |ΔT| ≥ 5 °C HVAC leakage, else an insulation void; cold: elongated is air infiltration, |ΔT| ≥ 6 °C moisture intrusion, else missing insulation. Regions are ranked by |ΔT| × (1 + ln area) and at most 24 are kept. The detection runs on your computer. The narrative sends the picture file, its file name, the statistics, the measurement parameters, the anomalies and any heat-flow results to the chosen provider (`claude-opus-5`, `gpt-6.1-sol` or `gemini-3.8-flash`); nothing else leaves the machine, and nothing is sent until you click. Report drafts send only the text facts of the report, no picture. Keys are stored in the profile's local database and sent only to their provider.

<a id="thermal-anomalies-see-also"></a>

### See also

- [AI usage: the usage bar, customers and projects, and the AI cost in reports](#ai-usage)
- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
- [Heat flow network: nodes, conductors, solving](#thermal-network)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-network"></a>

## Heat flow network: nodes, conductors, solving


The heat flow network models how heat moves between points of a picture. You place nodes that take their temperature from the picture, connect them with conductors for conduction, convection or radiation, and solve for the temperatures and heat flows in watts, either at equilibrium or over time.

<a id="thermal-network-before-you-start"></a>

### Before you start

- You are in the **Thermal** tab of the desktop app with the Thermal add-on enabled.
- A still picture is selected. On a radiometric picture each node samples the measured temperature; on any other picture it starts at 20 °C.
- Have the physical values ready: conductances (k × A ÷ L for conduction, h × A for convection) in W/K, εFA in m² for radiation, masses times specific heat (m·cp) in J/K for a transient solve, and any heater or solar power in W.

<a id="thermal-network-steps"></a>

### Steps

1. Click **Node** (⬤) in the toolbar. The **Heat Flow Network (Radiation Exchange)** section in the **Analysis** panel explains the tools until the first node exists.
2. Click on the picture where you want a computation point. A red dot appears, labelled `N1` with the sampled temperature.
3. Click the next point. `N2` appears, already linked to `N1` by the conductor `G1` (linear, 1 W/K). Hold Shift while clicking to start a new chain without a link.
4. Add extra links with **Link** (⌁): drag from one node to another. Parallel conductors between the same two nodes are allowed.
5. Click **Select** (↖), then click a node (or its line in the panel's list) to edit it:
  - **Label**, and **Kind**: `Diffusion (has mass)`, `Arithmetic (massless)` or `Boundary (fixed T)`.
  - **Initial temperature** (or **Temperature** for a boundary), a plain number in your temperature unit. A boundary also has **Prescribed temperature override**, which can follow a table over time.
  - **m·cp (mass × specific heat)** in J/K (diffusion only) and **Source (heater / dissipation / solar)** in W.
  - m·cp, **Source (heater / dissipation / solar)**, **Prescribed temperature override** and the conductor values can each be `constant`, `f(time)` or `f(temp)`; Source and the override also offer `none`. A table gets rows with **+ add row**.
6. Click a conductor to edit it: **Kind** `Linear — conduction kA/L or convection hA` with **Conductance G** in W/K, or `Radiative — σ·εFA·(T₁⁴−T₂⁴)` with **εFA (emissivity × view factor × area)** in m².
7. Pick `Steady state` or `Transient` in the panel. For a transient run type the duration in seconds and, after `s, dt`, a time step (blank = `auto`).
8. Click **Solve** (it reads **Solving…** while it runs). The counter reads `N nodes · M conductors · converged (N iter)`. A transient run that has to stop early reads `NOT converged` with an amber warning; a steady run that fails shows an error instead, such as "Newton iteration did not converge within 200 iterations".
9. Read the results. On the picture the conductors turn orange with an arrow in the direction of the flow, a width that follows the flow and a yellow label in W. The panel lists each conductor's flow and the table **Surface heat balance (per node, + = inflow)** with **Cond/Conv**, **Radiation**, **Source** and **Storage** per node. A transient solve adds a chart of the node temperatures over time.
10. Remove things with **Erase** (⌫) dragged over nodes or links, with Select and Delete, with **🗑** in an editor, or all at once with **clear network**. **clear result** removes only the solution.

<a id="thermal-network-example-heat-through-a-wall-then-radiation-to-the-sky"></a>

### Example: heat through a wall, then radiation to the sky

A wall seen from outside. You place three nodes in one chain and set:

| Node | Kind | Temperature |
|---|---|---|
| `N1` room air | `Boundary (fixed T)` | 20 °C |
| `N2` wall surface | `Arithmetic (massless)` | (solved) |
| `N3` outdoor air | `Boundary (fixed T)` | 0 °C |

Conductor `G1` (`N1` to `N2`) gets **Conductance G** 3 W/K, `G2` (`N2` to `N3`) 1 W/K. **Solve** in `Steady state` gives `converged (1 iter)` and:

- `N2` = (3 × 20 + 1 × 0) ÷ (3 + 1) = 15.0 °C,
- `G1` carries 3 × (20 − 15) = 15.0 W and `G2` carries 1 × (15 − 0) = 15.0 W: what enters the wall leaves it.

Radiation works the same way with a different law. A roof at 15 °C facing a clear sky at −10 °C with εFA = 0.9 m² (emissivity 0.9, view factor 1, 1 m²) loses σ × 0.9 × (288.15⁴ − 263.15⁴) = 5.670 × 10⁻⁸ × 0.9 × 2.099 × 10⁹ ≈ 107 W.

For a transient check: a diffusion node at 100 °C with **m·cp (mass × specific heat)** 100 J/K, linked by 10 W/K to a 0 °C boundary, cools with a time constant of 100 ÷ 10 = 10 s. A `Transient` run of 30 s with the automatic step (30 ÷ 200 = 0.15 s) ends at 100 ÷ (1 + 0.15 ÷ 10)^200 ≈ 5.09 °C (shown as 5.1 °C); the exact answer is 100 × e^−3 ≈ 4.98 °C. A step of `0.01` brings the result to within 0.1 °C of it.

<a id="thermal-network-tips-and-common-mistakes"></a>

### Tips and common mistakes

- A `Steady state` solve needs at least one **Boundary (fixed T)** node to fix the temperature level (without one the solve usually stops with "Singular system — check for nodes without any conductor" or "Newton iteration did not converge…", and any result it does give is meaningless), and every other node needs a conductor ("Node 'N4' has no conductors attached").
- A `Transient` solve needs a positive m·cp on every diffusion node. Make massless points `Arithmetic (massless)` instead.
- New nodes start as diffusion nodes with 100 J/K and links as 1 W/K. These are placeholders: set real values, or the watts mean nothing.
- Any edit clears the solution. Solve again after you change a value.
- The network is saved with the picture and comes back when you reopen it; the solution is not saved. The narrative of [AI variance analysis](#thermal-anomalies) includes the latest solution.
- The picture gives surface temperatures only. Air temperatures, conductances and εFA come from you.

> **Under the hood**
> This is a lumped-parameter network in the style of SINDA. Linear conductors follow Fourier's law `q = G × ΔT` (G = kA/L for conduction, hA for convection). Radiative conductors follow `q = σ × εFA × (T₁⁴ − T₂⁴)` with T in kelvin and σ = 5.670374419 × 10⁻⁸ W/(m²·K⁴). A diffusion node obeys m·cp × dT/dt = Σq + Q; an arithmetic node has no mass, so Σq + Q = 0 at every instant; a boundary node is held at its temperature (constant, or a table over time). The steady solver is Newton's method with the exact radiative derivative and a dense LU factorisation, converging when the change is below 10⁻⁶ K (at most 200 iterations). The transient solver is backward Euler, unconditionally stable, with dt = duration ÷ 200 unless you type one, and at most 200,000 steps. Tables are interpolated linearly and held flat beyond their ends. The limit is 400 nodes. Accuracy depends entirely on the values you enter; the solver itself is checked against exact cases (a two-boundary wall like the one above, an RC decay, radiative equilibrium). Everything runs on your computer.

<a id="thermal-network-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Viewing and annotating pictures](#annotate)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-vegetation"></a>

## Vegetation indices from multispectral orthomosaics


From a multispectral orthomosaic you compute a vegetation index such as NDVI, pixel by pixel. The result is a new picture in the library with the same analysis as a thermal picture: statistics, histogram, cursor readout, range isolation and anomaly regions.

<a id="thermal-vegetation-before-you-start"></a>

### Before you start

- You are in the **Thermal** tab of the desktop app with the Thermal add-on enabled.
- You have a multispectral orthomosaic exported from Agisoft Metashape (or another tool) as a 16- or 32-bit GeoTIFF with 4 or more bands (8-bit files are never treated as multispectral), for example from a DJI Mavic 3M, a P4 Multispectral or a MicaSense RedEdge or Altum.
- The TIFF is pixel-interleaved (the Metashape default). A band-sequential (planar) file imports as an ordinary orthomosaic without the index section; re-export it with pixel interleave.
- You know which band is which colour. The camera's or Metashape's band order tells you.

<a id="thermal-vegetation-steps"></a>

### Steps

1. Import the GeoTIFF with **+ Import photos / videos** or by dragging it onto the studio. Its row shows 🗺️ and `Multispectral Orthomosaic`; the viewer shows an RGB composite.
2. Select the row. The section **Vegetation Index (Multispectral)** appears at the top of the **Analysis** panel, with a line such as "5-band multispectral raster (16-bit)."
3. Check the band rows. Each **Band** row has a select with `B (Blue)`, `G (Green)`, `R (Red)`, `RE (RedEdge)`, `NIR (NIR)`, `T (Thermal)` or `— unused —`. The defaults follow the band count:
  - 4 bands: G, R, RE, NIR (Mavic 3M),
  - 5 bands: B, G, R, RE, NIR (P4 Multispectral, RedEdge),
  - 6 bands: B, G, R, RE, NIR, T (Altum).
4. Correct any band that differs. A role can be on one band only; choosing it on a second band clears the first.
5. Pick a **Preset**: `NDVI`, `GNDVI`, `NDRE`, `SAVI` or `VARI`. The formula box and the name box fill in. If a band the preset needs is not mapped, an amber line names it.
6. Or write your own formula: type it into the formula box (the preset switches to `Custom…`) and give it a name in the box beside the preset. Use the mapped roles as variables, `+ − × ÷` (or `+ - * /`), parentheses and numbers, for example `(NIR - RE) / (NIR + RE)`.
7. Click **Compute NDVI** (the button carries the name you gave; it reads **Computing…** while it runs).
8. Look at the new row: named after the index (`NDVI.png`), subtitle `Vegetation Index`, selected automatically. The picture uses the red to yellow to green **Vegetation** palette, and the panel shows **Index Statistics** with values to 3 decimals and no unit.
9. Work on it like a thermal picture: tick **Isolate a temperature range** to keep, say, values below 0.3, or click **Detect anomalies** to find patches that are clearly lower (`▼ Low`) or higher (`▲ High`) than the field around them.

<a id="thermal-vegetation-example-ndvi-of-a-crop-strip"></a>

### Example: NDVI of a crop strip

For one pixel the bands read NIR = 0.50 and R = 0.08 (reflectance). NDVI = (NIR − R) ÷ (NIR + R) = (0.50 − 0.08) ÷ (0.50 + 0.08) = 0.42 ÷ 0.58 = 0.724: dense, healthy canopy. A bare soil pixel with NIR = 0.25 and R = 0.20 gives 0.05 ÷ 0.45 = 0.111.

With the index computed:

1. **Index Statistics** shows the min, max and mean of the field; the info line under the panel title reads `NDVI = (NIR - R) / (NIR + R) · range <min> … <max>`.
2. You tick **Isolate a temperature range**, set **Low** to the minimum and **High** to `0.300`, and choose **Solo**. Only the stressed or bare patches stay visible; `Pixels in range:` gives their share of the picture.
3. You add an arrow and a note on the worst patch and put the picture in the report like any other.

<a id="thermal-vegetation-tips-and-common-mistakes"></a>

### Tips and common mistakes

- The bands are used as stored, without radiometric calibration. NDVI, GNDVI and NDRE are ratios, so a common scale cancels out; SAVI (its 0.5 assumes reflectance from 0 to 1) and VARI need reflectance bands. Export a reflectance orthomosaic from Metashape for those.
- An RGB orthomosaic with a marked alpha band is recognised and stays a normal orthomosaic. If a 4-band 16- or 32-bit file still shows as `Multispectral Orthomosaic` but its composite looks like an ordinary photo, its fourth band is probably an unmarked alpha band: do not compute indices on it.
- A wrong band mapping gives a plausible-looking but wrong map. Check that healthy vegetation reads high (NDVI above about 0.6) before you trust the result.
- Pixels where the formula divides by zero become no-data: blank in the stored image, drawn dark in the viewer, and left out of the statistics.
- The section appears only for the multispectral orthomosaic itself. The Photogrammetry studio has no index tools.

> **Under the hood**
> The presets are NDVI = (NIR − R) ÷ (NIR + R), GNDVI = (NIR − G) ÷ (NIR + G), NDRE = (NIR − RE) ÷ (NIR + RE), SAVI = 1.5 × (NIR − R) ÷ (NIR + R + 0.5) and VARI = (G − R) ÷ (G + R − B). Every band of the TIFF is read into 32-bit floats (8-, 16- and 32-bit integer or float samples) and the formula is evaluated per pixel; a division by zero yields no-data. In the studio and the report the colours span the index's min to max (or the typed Scale); only the stored PNG uses −1 to 1 when every value lies within ±1.2. The index is stored as a colour PNG plus the raw 32-bit raster beside it, keeps the source's GPS position and capture time, and goes through the same statistics, isotherm and anomaly code as temperatures; the anomaly classifications and the AI narrative, which are thermography-specific, are hidden for it. Everything runs on your computer.

<a id="thermal-vegetation-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Photogrammetry: getting started](#photo-start)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-report"></a>

## Thermal inspection reports, AI drafts and inspection bundles


The Thermal Inspection Report builder turns your pictures, anomalies, flights and take-offs into a professional thermography report in PDF, Word or RTF. You fill 11 numbered sections, let AI draft the summary and recommendations if you want, preview and edit the text, and export. An inspection bundle packs the whole job into one file you can open on another machine.

<a id="thermal-report-before-you-start"></a>

### Before you start

- The Thermal add-on is enabled and the Thermal Studio is open. See [Thermal Studio: getting started](#thermal-start).
- Your radiometric pictures are imported. For the anomaly log, run the detection first; see [AI variance analysis](#thermal-anomalies).
- For flight data, import the DJI flight logs in the main logbook.
- For take-offs in the report, add materials in the **🧮 Material Takeoff** window; see [Material take-offs](#materials-takeoff).
- For AI drafts, choose the Chat connection or add a provider key in Settings → **AI providers**. Drafting works with a Thermal or a Photogrammetry license. Everything else works without it.

<a id="thermal-report-steps"></a>

### Steps

1. Click **📄 Report ▼** in the top bar. The menu offers **Open report builder…** and **Import inspection bundle…**.
2. Click **Open report builder…**. The **Thermal Inspection Report** window opens with a blank report dated today. The thermographer's details and camera of your last report are filled in.
3. Type a name in the `Report name` box at the top.
4. Work down the numbered sections (see the table below). Each heading reads like `5 · Thermal Imaging Log / Comparative Matrix`, with its buttons on the right.
5. Click **Save as new**. `Report saved.` confirms it; from then on the button reads **Save**.
6. Click **Preview & edit** to see the report as it will export (see "Preview, export and bundles").
7. Click **Export ▼** and pick **PDF**, **Word (.docx)** or **RTF**, then choose where to save it.
8. Close the window with **✕**. Your saved report stays under **Saved reports** the next time you open the builder.

<a id="thermal-report-the-11-sections"></a>

### The 11 sections

| # | Section | What you do there |
|---|---|---|
| 1 | Header Data & Administrative Information | **Project name**, **Client**, property, date, site, inspector and credentials, camera; **📷 Fill camera from imagery** reads the camera from the pictures. Holds the **Executive summary**. |
| 2 | Environmental & System Conditions | Weather, ambient temperature, humidity, load; **⚙ Use analysis parameters** copies emissivity, reflected temperature, ambient, humidity and distance from the selected picture. |
| 3 | Flight Data (DJI) | Tick the flights that produced the imagery; **↻ Fill from flight logs** sets the date, time window, site position and aircraft. |
| 4 | Orthomosaic (Agisoft Metashape) | Pick an **Embedded orthomosaic image** (or `— none —`) and add a map link. |
| 5 | Thermal Imaging Log / Comparative Matrix | **+ Add imaging pair**, or **⚡ Pairs for anomalies** for every picture that has anomalies in the log (section 6; greyed out while the log is empty). Each pair has a **Visual (RGB) image**, a **Thermal (IR) image**, a **Caption / location** and **LRF / range data**; for a radiometric thermal picture also a **Palette** and a scale (blank = auto). |
| 6 | Anomalies & Findings | **⚡ Import detected** brings in the anomalies found on the selected picture; **+ Manual entry** adds one by hand. Each has an ID, location, temperatures, ΔT, severity, classification, finding and recommendation. |
| 7 | Materials and Projected Cost | **📦 Add materials from pictures** reads the take-offs on the pictures of the imaging pairs; **+ Add material** adds a row. |
| 8 | Asset Inventory & Exception List | **+ Add asset**, **+ Not inspected**, or **⚡ Exceptions from anomalies**. Status `Normal`, `Exception` or `Not inspected / inaccessible`. |
| 9 | Action Plan & Repair Prioritization | Work orders by severity. |
| 10 | Follow-Up & Re-inspection | Verification scans and the re-inspection interval. |
| 11 | Limitations, Definitions & Disclaimer | Prefilled standard text; edit it, or put it back with **↺ Standard text**. |

In section 5, a pair whose thermal picture carries spots or ΔT marks prints a two-column table, **Reading** and **Value**, with the parameters line under it. Three checkboxes in the section control the pictures: **Colour bar under thermal pictures** adds a temperature scale under each thermal figure (on for new reports), **Apply the current parameters (e, d, r, h, ambient) to every picture** decides whether the figures and readings use the parameters from the Analysis panel or each file's own, and **Include perimeters** prints each area's perimeter in the measurement lines under the pictures (off by default, also in reports made before this version: a report that printed perimeters prints them again only once the box is ticked). With two or more areas that have a value on a picture, its line also gives their sum, for example `total area 1000 m² ± 9 m² (2 areas)`, or `(2 of 3 areas)` when one has none. See [Side-by-side documents and temperature exports](#thermal-deliverables-spot-readings).

The materials section works as described in [Material take-offs: In the report](#materials-takeoff-in-the-report). Its From column names the pair and the picture, such as `Pair 2 (thermal)` or `Pair 2 (visual)`, because the two pictures of a pair are separate figures.

<a id="thermal-report-ai-drafts"></a>

### AI drafts

Four sections carry a **✨ AI draft** checkbox in their heading: Header Data (the executive summary), Anomalies & Findings, Action Plan & Repair Prioritization, and Follow-Up & Re-inspection.

1. Enter the facts first: conditions, anomalies, inventory, materials.
2. Tick **✨ AI draft**. The heading shows `writing…`, then the notice `AI draft applied to “…” — review and edit it; untick to restore your own text.` For anomalies, each entry's finding and recommendation is filled by its ID.
3. Read and edit the draft. It is your report.
4. Click **↻** next to the box to write a new draft, or untick the box to get your own text back.

Without a key the box is greyed out, and its tooltip reads `Configure an AI API key in Settings (AI providers) to enable AI drafting`. **Save** waits while a draft is being written.

<a id="thermal-report-preview-export-and-bundles"></a>

### Preview, export and bundles

1. Click **Preview & edit**. The **Edit** tab shows the report text: click any text to change it in place. The **PDF** tab shows the exported PDF. **Refresh** re-renders after you change pictures or sections.
2. Export with the preview's own export buttons (PDF, Word, RTF), or with **Export ▼** in the builder.
3. Click **Export Bundle** to save the whole inspection as one `.odlbundle` file. `Inspection bundle exported.` confirms it; if a picture had to be left out, the message adds `Not included:` and its name.
4. On another machine or profile, open **📄 Report ▼** → **Import inspection bundle…** and pick the file. A message reads `Bundle imported: N new asset(s), M already present, report "…"`, sometimes followed by `, N archived flight(s) in the bundle file` (the flights stay archived in the file; they are not added to your logbook). If some pictures could not be imported, a line `N picture(s) could not be imported:` names them. Pictures already in the library are not copied twice, and the report appears under **Saved reports** with its links intact.

With **Add the AI cost to the report's projected cost** ticked in Settings, a report that has a client gets an **AI analysis** row in **Materials and Projected Cost**; see [AI usage](#ai-usage-adding-the-ai-cost-to-a-report). The **Project name** prints under Header Data when it is filled in.

Saved reports appear as chips under **Saved reports**. Click one to load it; hover it and click its **✕** to delete it (the app asks first). **+ New blank** starts a fresh report.

<a id="thermal-report-example-a-roof-moisture-survey"></a>

### Example: a roof moisture survey

You flew a 6:12 shingle roof and found wet spots in the decking.

1. On the visual picture of the roof, give it a scale with Settings → Units set to imperial (see [Giving a picture a scale](#measure-scale)), outline the 2,000 ft² roof as area `A1` and add `Asphalt shingles — by roof surface` with a typed 6:12 pitch and a price of $38.50.
2. Open the builder, name the report `Roof survey`, tick the morning's flight in **Flight Data (DJI)** and click **↻ Fill from flight logs**. Click **Save as new**, then close the builder with **✕**.
3. For each thermal picture: select it in the studio and click **Detect anomalies** in the Analysis panel. Open the builder, click the `Roof survey` chip under **Saved reports**, click **⚡ Import detected** in section 6, **Save**, and close the builder. The builder covers the studio, and selecting another picture clears its detection result, so do one picture at a time.
4. In section 5 click **⚡ Pairs for anomalies**: every picture that has anomalies in the log (section 6) gets a pair, its visual twin matched by DJI file names (`…_T` or `…_R` beside `…_W`, `…_V` or `…_Z`). Tick **✨ AI draft** on Anomalies & Findings to word the findings.
5. In section 7 click **📦 Add materials from pictures**. The shingle row orders 74 bundles for $2,849.00; in the exported table its From cell starts with `Pair 1 (visual)`.
6. Tick **✨ AI draft** on the Action Plan; it can name the projected total.
7. **Save**, **Preview & edit**, then **Export ▼** → **PDF**.

The PDF opens with the title and the line `Generated by Airwulf, LLC · Thermal inspection workflow`.

<a id="thermal-report-tips-and-common-mistakes"></a>

### Tips and common mistakes

- **↻ Fill from flight logs** stays greyed out until a flight is ticked. It overwrites the header fields the logs fill.
- **⚡ Import detected** reads the detection result of the picture selected in the studio. The builder covers the studio, so close it, select the next picture, run **Detect anomalies**, then reopen the saved report and import again.
- Materials come only from pictures used in imaging pairs. Add the pair first, then **📦 Add materials from pictures**; rows already added are skipped.
- An anomaly imported while a boundary was set prints `Detected inside the analysis boundary (14.7 % of the picture)`, and a picture whose boundary cannot be read is printed without its temperatures; see [the analysis boundary](#thermal-boundary).
- Export a bundle, not just a PDF, when someone else will continue the inspection.
- A survey's bundle needs the Photogrammetry add-on: without it, **Import inspection bundle…** answers `Bundle import failed: The Photogrammetry add-on needs a valid license: …` and keeps nothing of the bundle. When a bundle brings pictures that only the Photogrammetry tab lists, a second line of the message says so, such as `3 pictures and the report show in the Photogrammetry tab.`, or `1 picture shows in the Photogrammetry tab, which needs the Photogrammetry add-on.` for a visual picture the inspection's author picked from that tab.

> **Under the hood**
>
> An AI draft sends only the facts entered in the report (conditions, flights, anomalies, inventory, the material count and projected total, and the waste allowance when prices exist) to the provider chosen in Settings, never the pictures. A bundle is a gzipped tar holding the report, every asset it refers to (thermal media and Metashape files with their previews), the annotations, the heat-flow networks and the linked flights' full telemetry; assets are matched by content hash on import. Every report names its publisher and the workflow under the title, "Generated by \<publisher\> · \<workflow\>": the publisher is the company saved under Settings → **Branding**, and "Airwulf, LLC" until one is saved.

<a id="thermal-report-see-also"></a>

### See also

- [AI usage: the usage bar, customers and projects, and the AI cost in reports](#ai-usage)
- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Side-by-side documents and temperature exports](#thermal-deliverables)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Saving clients and claim details for reuse](#clients)
- [Delivering a claim package: originals, portal copies, custody sheet](#claim-package)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-deliverables"></a>

## Side-by-side documents and temperature exports


Three buttons in the Thermal Studio's top bar turn the pictures you have already read into files you can hand over. **📄 Side-by-side…** builds a document with one page per picture: the visual twin on the left, the thermal picture on the right, the spot readings under them. **🌡 Export temperatures…** writes the temperature of every pixel as a TIFF or a CSV that other tools, and this app, can read back. **📐 Export linework…** writes the measurements and drawings of the selected picture as a DXF, GeoJSON or ODL XML file; it works as in the Photogrammetry tab and is explained in [Exporting linework](#mapping-deliverables-exporting-linework).

<a id="thermal-deliverables-before-you-start"></a>

### Before you start

- Pair the thermal pictures with their visual twins first. See [Pairing thermal and visual pictures](#thermal-start-pairing-thermal-and-visual-pictures). A picture without a twin still gets a page, with the placeholder "No visual twin".
- Place the spots and ΔT marks you want on the thermal pictures with the **🌡 Spot** and **± ΔT** tools. See [Viewing and annotating pictures](#annotate).
- **📄 Side-by-side…** and **🌡 Export temperatures…** need at least one radiometric picture in the library. Index rasters (vegetation) are not offered. **📐 Export linework…** needs a still picture with a measurement or drawing on it.

<a id="thermal-deliverables-steps"></a>

### Steps

<a id="thermal-deliverables-side-by-side"></a>

#### Side-by-side

1. Select a thermal picture and click **📄 Side-by-side…**. The dialog **📄 Side-by-side** opens.
2. Under **Pictures** choose **Selected picture**, **All thermal pictures with a twin (N)** or **All thermal pictures (N)**. A batch is in capture order.
3. For a batch, set the range **Pictures** [1] to [100]. A document holds at most 100 pictures. A range that is not the whole set adds `_<from>-<to>` to the file name.
4. Type the **Title** and pick a **Client** (or **No client**). The palette is the studio's; when the studio shows the vegetation palette of an index raster, the thermal pictures print in Iron. The **Selected picture** is printed with the studio's current scale and parameters; in a batch the scale is automatic for each picture.
5. Tick what to print:
  - **Readings**: the table of spots and ΔT, then Min, Max and Mean and the parameters line.
  - **Annotations**: your arrows, text and measurements on both pictures.
  - **Colour bar**: a temperature scale strip under each thermal picture.
  - **Apply the current parameters (e, d, r, h, ambient) to every picture**, batch only. Left unticked, each picture keeps the parameters stored in its own file. (The export's **Selected picture** also uses the current parameters.)
6. Pick the **Format**: PDF, Word (.docx) or RTF, then click **Build…**. The line "Rendering 12 of 100…" counts the pictures; **Cancel** stops the build and writes nothing.
7. Choose where to save. The message "Side-by-side saved: \<path\>" ends the job; "Not saved." means you dismissed the save dialog. A file you named is replaced when you confirm the dialog's own overwrite question. If the app had to change the extension of the name you typed and a file of the new name exists, the build ends with "A file named \<name\> already exists in that folder; choose another name" instead of replacing it.

One picture takes one page. The image is made as large as the page allows, within a 92 mm height cap and the shape of the two pictures. The text under it gets room first, but if the page is too full the image shrinks first. Only then are the notes cut, from six lines to two each, and the readings from nine rows to three plus "and N more readings". If the image would still fall under 40 mm, the build stops with "\<name\> does not fit on one page even at the smallest size; shorten its notes or rename it", naming the picture, and nothing is written. If a build would pass the document size limit it stops before rendering with "This selection would exceed the document limit; choose a smaller range".

<a id="thermal-deliverables-temperature-export"></a>

#### Temperature export

1. Click **🌡 Export temperatures…**. The dialog **🌡 Export temperatures** opens.
2. Choose **Selected picture** or **All thermal pictures (N)**.
3. Tick the formats: **TIFF (32-bit float, °C)** and **CSV**.
4. For a batch you can tick **Apply the current parameters to every picture**. Unticked, the box reads "Values use each picture's own parameters".
5. Click **Export…**. One picture in one format opens a save dialog. Anything else opens a folder chooser.
6. If files with the same names already exist, the dialog says "N files exist" and offers **Replace all**, **Skip existing** or **Cancel**. Cancel writes nothing.
7. Read the result line: "Exported N files to \<folder\>", and one line per output that failed or was skipped, such as `name: exists`.

A line below the result names an output that failed or was skipped (`name: exists`), a warning from an output (`name: <warning>`), and a leftover temporary file from an earlier export: "a leftover part file from an earlier export: \<name\>". Delete that file yourself; the app never removes it.

Names are `<picture>_temperatures.tif` and `<picture>_temperatures.csv`; a clash inside the batch gets a number.

| File | Holds | Precision |
|---|---|---|
| TIFF | one band of 32-bit float °C, NaN where there is no data; the parameters are written in its description | exact |
| CSV | `#` header lines (source, capture time, width, height, parameters), then one row per pixel row | three decimals, `NaN` for no data |

Both files import again with **🌡 Radiometric file…**. The app recognises its own files and reads them as written, without guessing kelvin, for pictures up to 2048 pixels a side.

<a id="thermal-deliverables-spot-readings"></a>

### Spot readings

The **Spot readings** section of the Analysis panel lists the spots and ΔT marks of the selected picture: `S1 34.2 °C · (12, 48)` and `ΔT1 +6.2 °C · (12, 48) → (40, 51)`, with the pixel coordinates. Under them is the parameters line, marked "(overridden)" when you changed emissivity or distance in this session. "…" means the temperatures are still loading; "Readings use the last successful analysis" means the latest re-measure failed. In documents the Δ is written `dT`, and the thermal report prints the same readings as a two-column table, **Reading** and **Value**, under each pair.

<a id="thermal-deliverables-example-an-h20t-flight-over-a-roof"></a>

### Example: an H20T flight over a roof

You flew a roof with an H20T. The library holds 3 thermal pictures, each with a wide twin and the ⇄ badge (plus their zoom pictures and a screenshot, which stay out of the documents).

1. On `DJI_0001_T.JPG` you click **🌡 Spot** on a vent (S1, 52.4 °C) and on the clean membrane beside it (S2, 31.0 °C). Then you drag a **± ΔT** from the membrane to the vent: ΔT1 +21.4 °C (the second point minus the first; dragging the other way reads -21.4). A third spot goes on a seam.
2. You choose **All thermal pictures with a twin (3)**, leave **Readings** ticked and build a PDF. It has 3 pages. The first carries the letterhead and title.
3. You select the vent picture, click **🌡 Export temperatures…**, tick both formats and click **Export…**. The folder chooser writes `DJI_0001_T_temperatures.tif` and `DJI_0001_T_temperatures.csv`.

<a id="thermal-deliverables-tips-and-common-mistakes"></a>

### Tips and common mistakes

- A picture with no spots prints no readings table. It prints the palette and scale instead.
- The values in a batch follow the pictures' own parameters. If a number differs from the studio, either tick the parameters box or compare the parameters line.
- Edits you made a moment ago are saved before the build starts. If saving a picture's annotations fails, the build still runs: that picture is printed as stored, without temperatures, with the note `The last changes to this picture's annotations are not saved, so its temperatures were left out.` The same happens, with the note `The analysis boundary of this picture could not be read, so its temperatures were left out.`, for a picture whose boundary cannot be read. When the last changes to a pair's visual picture are not saved, the pair carries the note `The last changes to the visual picture's annotations are not saved; it is printed as stored.`
- DOCX and RTF are laid out by Word or your reader when opened, so a page may break differently from the PDF.
- Open the CSV in a text editor first: the `#` lines are part of the format, and a spreadsheet may reformat them.

> **Under the hood**
> The values come from one preparation per picture: the same temperature matrix feeds the spot labels, the readings and the document. The side-by-side builder estimates the size of the pictures it embeds and stops at 120 MB for PDF and DOCX and 80 MB for RTF. Nothing reaches the folder half-written: each file is encoded to a temporary part and moved into place, and without permission to replace, an existing file is never overwritten. The TIFF is little-endian baseline with a 32-bit float sample and a `NaN` no-data tag. The CSV is UTF-8, CRLF, `.` decimal.

<a id="thermal-deliverables-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [Viewing and annotating pictures](#annotate)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Delivering a claim package](#claim-package)
- [Orthomosaic export, linework files and volume tickets](#mapping-deliverables)

<sub>[Back to contents](#contents)</sub>


---

# Photogrammetry

<a id="photo-start"></a>

## Photogrammetry: getting started, importing, the library and Metashape deliverables


The Photogrammetry tab collects the imagery and the Agisoft Metashape outputs of a survey and turns them into a survey report. You import photos, videos and Metashape deliverables into one library, annotate and measure the pictures, and queue the ones you want as report figures. This topic covers setting up, importing and the library.

<a id="photo-start-what-this-studio-does"></a>

### What this studio does

Each row names a feature, where you find it, and the walkthrough that explains it.

| Feature | Where | Walkthrough |
|---|---|---|
| Import photos, videos and Metashape exports | **+ Import photos / videos** or **📂 Import folder…** in the top bar, or drop files on the window | [Steps](#photo-start-steps), [Import folder](#claim-package-import-folder) |
| The library: kind tabs, search, filters, select all, delete, rename | The left column, headed `Library (N)` | [The library](#photo-start-the-library) |
| The figure queue | **+ Add to report** in the top bar or **+** on a library row; the right column, headed `Report images (N)` | [The figure queue](#photo-report-the-figure-queue) |
| Metashape deliverables (orthomosaics, elevation models, reports, point clouds) | Imported like photos and listed under the **Metashape** tab; a document opens as a card with **Open in default application** | [What is recognised](#photo-start-steps), [In the report](#photo-report-deliverables) |
| Scale and measurements | **🧭 Scale** and the tools of the toolbar's **Measure** group | [Giving a picture a scale](#measure-scale-steps), [Measuring](#measure-tools-measure) |
| Positions and ground control points | **GCP** (🎯) and **Position** (⌖) in the **Measure** group | [GCP](#measure-geo-gcp), [Position](#measure-geo-position) |
| Elevation models, slopes and volumes | An elevation-model GeoTIFF that pairs with the orthomosaic; **Slope** (⟋) and the areas in the **🧭 Scale** window | [Pair the elevation model](#measure-elevation-pair-the-elevation-model), [Volume inside an area](#measure-elevation-volume-inside-an-area) |
| Material take-offs | **🧮 Material Takeoff** after **🧭 Scale** in the toolbar, then **+ Material…** on a measurement or area row | [Take-offs](#materials-takeoff-steps) |
| Orthomosaic export (JPG with world file) | **🗺 Export orthomosaic…** in the top bar | [Exporting an orthomosaic](#mapping-deliverables-exporting-an-orthomosaic) |
| Linework export (DXF, GeoJSON, ODL XML) | **📐 Export linework…** in the top bar | [Exporting linework](#mapping-deliverables-exporting-linework) |
| Volume ticket | **🧾 Volume ticket…** in the top bar | [Printing a volume ticket](#mapping-deliverables-printing-a-volume-ticket) |
| Survey report and inspection bundles | **📄 Report** in the top bar, then **Open report builder…** or **Import inspection bundle…** | [Survey report](#photo-report-steps) |
| Claim package | **📦 Claim package…** in the report builder's header | [Claim package](#claim-package-steps) |

<a id="photo-start-before-you-start"></a>

### Before you start

- Use the desktop app. The library stores media in your local profile, so the tab is not available in the web version.
- Install the add-on: open **Settings** (the gear at the top of the sidebar) and click **Open Add-ons**, click **Download installer…** for Photogrammetry, run the installer, then click **↻ Refresh**. The add-on's badge reads `Enabled · v<version>` and the Photogrammetry tab appears in the sidebar.
- To hide the tab without removing anything, untick **Enabled** in the same screen.
- Have the survey photos or videos at hand, and the Metashape exports you want in the report: orthomosaic and DEM GeoTIFFs, the processing report PDF, the camera XML, point clouds.

<a id="photo-start-steps"></a>

### Steps

1. Open the Photogrammetry tab. The top bar shows the 📷 Photogrammetry title; the library is on the left, the viewer in the middle and the report queue on the right.
2. Click **+ Import photos / videos** and pick the files. Or drag them onto the window: the overlay reads `Drop photos, videos or Metashape exports to import`.
3. Wait while the button reads `Importing 3 of 10…`. The new items appear in the library.
4. Click a photo in the library. It opens in the viewer with the annotation toolbar above it.
5. Annotate it, add a **📝 Note** for the report, or open **🧭 Scale** to measure. See [Viewing and annotating pictures](#annotate) and [Giving a picture a scale](#measure-scale).
6. Queue it for the report with **+ Add to report** (see "The report queue" below).

The import accepts JPG, JPEG, PNG, MP4, MOV, AVI, TIF, TIFF, PDF, XML, LAS, LAZ, PLY, OBJ, KML and KMZ. The file dialog also takes a CSV (a Metashape camera reference); a dropped CSV is left for the flight importer. Metashape files are recognised and labelled like this:

| File | Listed as | Shown as |
|---|---|---|
| Orthomosaic GeoTIFF | `Orthomosaic (GeoTIFF)` | A picture, previewed at up to 4096 px |
| GeoTIFF with one numeric band, named with the word DEM, DSM, DTM, elev, elevation, height or heights | `Elevation model (DEM, GeoTIFF)` | A picture, previewed at full size; it pairs with an orthomosaic it overlaps |
| GeoTIFF with 4 or more bands (not an RGBA image: no declared alpha band, not a plain 4-band 8-bit file) | `Multispectral Orthomosaic` | A picture, as an RGB composite |
| Processing report PDF | `Processing Report (PDF)` | A document card |
| Camera file XML | `Camera Calibration (XML)` | A document card |
| Camera reference CSV | `Camera Reference (CSV)` | A document card |
| LAS, LAZ, PLY, OBJ | `Point Cloud` | A document card |
| KML, KMZ | `Map Overlay (KML/KMZ)` | A document card |

<a id="photo-start-the-library"></a>

### The library

The library lists everything you imported, with its count in the header (`Library (N)`). The kind tabs sit under the title and wrap onto a second row when the panel is narrow; the search box and **Filters** are below them.

1. Click **All**, **Photos**, **Wide**, **Zoom**, **Videos** or **Metashape** to show one kind. **Wide** and **Zoom** are the photos whose file name, as imported, ends in `_W` (or `_V`) and `_Z`, the way a DJI camera names its wide and zoom pictures.
2. Read the rows. The icon says what it is: 📷 photo, 🎬 video, 🗺️ Metashape image, 📄 Metashape document. The line below reads `Photo`, `Video` or the Metashape kind, then the capture date and, for a photo, its orientation (for example `Roof, nadir` or `Untagged`). A queued item shows `In report`, or `In report ×N` when it is queued more than once.
3. Find items by name: type part of a name into the search box (`Search by name`). The list keeps the rows whose name contains the text, whatever the case.
4. Click **Filters** for more criteria. Each one you set narrows the list further, inside the kind tab you chose:
  - the type chips, one per type in the tab with its count, for example `JPG (340)`, `MP4 (12)` or a Metashape kind such as `Point Cloud (1)`; click several to show any of them, click a chip again to drop it;
  - **Size (MB)**: a `min`, a `max` or both; an item whose file cannot be found has no size and is hidden while a size is set;
  - **Captured**: a from date and, under it, a to date, both days included; an item without a capture time counts by the day it was imported, and one with neither is hidden while a date is set;
  - **Camera** and **Dimensions**: pick one of the cameras or picture sizes in the tab, for example `FC6310 (340)` or `5472 × 3648 (340)`; `Any` drops the criterion. Each list is there only when the tab has such values.
5. Read `Showing N of M` at the bottom of the filter bar, for example `Showing 40 of 357`; M counts the rows of the tab. While the search box or a filter is set, **Clear filters** appears beside it; click it to empty both and see every row of the tab again. The filter is not saved: it starts empty each time you open the Photogrammetry tab, and switching between the kind tabs keeps it.
6. Tick the checkbox of each item you want; every row has one, documents included. Ticking does not open the item. Or tick **Select all** under the filter bar: it ticks only the rows the tab and the filters show. It shows a dash while only some of them are ticked; a click then ticks them all, and a click on a full tick clears them. `3 selected` beside it counts the ticks. When you change the tab or the filter, the ticks on rows it hides are dropped, so nothing you cannot see is added or deleted.
7. To queue the ticked items, click **+ Add to report** in the top bar. It adds only the ticked rows that can be figures (photos, videos, orthomosaics) and skips ticked documents; its count, for example `+ Add to report (4)`, is the number of ticked rows that can be figures; one already in the queue is not added again. Then the ticks are cleared and a notice such as `Added 4 to the report (9 total).` says what happened, plus `1 document(s) skipped — only photos, videos and orthomosaics can be figures.` when a document was ticked.
8. To delete the ticked items, click **Delete selected…** under **Select all** (greyed out while nothing is ticked). One question names the count, how many are queued in the report (they leave the queue) and how many are Metashape files shared with the Thermal Studio (they go there too), for example `Delete 357 pictures from the library? Their files, annotations and measurements are removed. 12 are queued in the report and leave the queue. 2 are Metashape files shared with the Thermal Studio.` Cancelling it deletes nothing.
9. Wait while the line under the button reads `Deleting 120 of 357…`. Meanwhile **Select all**, **Delete selected…**, the import buttons, the note, renaming and the 🗑 buttons are greyed out, and dropped files are not taken. When it is done the ticks are cleared, the list reloads and the line reads `Deleted 357 of 357`. If some could not be deleted it reads `Deleted 355 of 357; 2 failed: <first error>`: the others are gone, the failed ones stay in the list. The row checkboxes stay live, but the delete takes the ticks you confirmed; ticks you change meanwhile are cleared when it ends. When some files of the deleted pictures could not be removed, the line ends `; 2 files were left in the app's data folder` (`; 1 file was left …` for one). A bulk delete that is refused because an import is still running reads `Nothing was deleted: another delete or an import is running.`
10. Hover a row for its buttons: **+** adds it to the report, **✏️** renames it, **🗑** deletes it.
11. To rename, double-click the name or click **✏️**, type, and press Enter (Esc cancels). The name is printed in the report; the stored file keeps its name. If the kind tab or a filter hides the item, renaming it from the info strip's **✏️** clears the kind tab and the filter first.
12. To delete one item, click **🗑** and confirm. The file, its annotations and its measurements are removed, and it leaves the report queue. For a Metashape file the question warns that it is shared with the Thermal Studio, so it goes there too.
13. Click a document (a processing report, a camera file, a point cloud) to see its card: size, cameras, markers, coordinate system and format when known, and **Open in default application**. A document is not a figure, but it travels in the report's bundle when you tick it as a deliverable in the report builder.

The Metashape files are shared with the Thermal Studio: an orthomosaic imported here can be analysed and annotated there, and the other way round. Photos and videos you import here stay in the Photogrammetry library.

If the library cannot be read, a line under the top bar reads `The library could not be read:` followed by the reason, and the list may be empty or out of date. Click **Retry** on that line to read it again. Nothing in the library is changed by a failed read.

To hand a survey over as files, use the buttons in the top bar after **📂 Import folder…**: **🗺 Export orthomosaic…** writes the selected orthomosaic as a JPG with its world file and a presentation copy, **📐 Export linework…** writes the measurements of the selected picture as DXF, GeoJSON or ODL XML (also in the Thermal Studio), and **🧾 Volume ticket…** prints a numbered document for one measured volume. See [Orthomosaic export, linework files and volume tickets](#mapping-deliverables).

<a id="photo-start-the-report-queue"></a>

### The report queue

The right column, headed `Report images (N)`, is the list of figures for the survey report, in report order. Add the selected item or the ticked items with **+ Add to report**, a single row with its **+**, or a video frame with **+ Add frame m:ss.s to report**. Give each figure a caption, and drag **⋮⋮** or use **▲** and **▼** to reorder. The queue becomes the Survey Imagery section; see [The figure queue](#photo-report-the-figure-queue).

<a id="photo-start-example-a-warehouse-roof-survey"></a>

### Example: a warehouse roof survey

You flew a warehouse roof and processed it in Metashape.

1. Drag in the roof photos, `roof_ortho.tif`, `roof_DSM.tif` and `report.pdf`. The library shows the photos with 📷, the orthomosaic as `Orthomosaic (GeoTIFF)`, the DSM as `Elevation model (DEM, GeoTIFF)` because its name says DSM, and the PDF as `Processing Report (PDF)`.
2. Click **Metashape** to see only those three, then **All** again.
3. Rename `DJI_0412.JPG` to `North parapet crack`, so the report prints a useful name. The extension is kept: the row reads `North parapet crack.JPG`.
4. Tick the three photos that show the damage and the orthomosaic. The button now reads `+ Add to report (4)`; click it.
5. Open the orthomosaic in the viewer. The DSM overlaps it in the same coordinate system and its name says DSM, so it pairs automatically and the **🧭 Scale** window can measure slopes and volumes.

<a id="photo-start-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Name the DEM so it pairs: a one-band GeoTIFF that overlaps the orthomosaic in the same coordinate system pairs automatically only when it has one numeric band and its name has the word DEM, DSM, DTM, elev, elevation, height or heights.
- Documents cannot be figures. **+ Add to report** skips a ticked document, and with a document selected **+ Add to report** is greyed out (tooltip `Documents cannot be report figures — photos, videos and orthomosaics can`).
- Deleting a Metashape file here deletes it from the Thermal Studio too. There is no undo, for **Delete selected…** either: check `Showing N of M` before you tick **Select all**.
- Rename before you export: the name, not the file name on disk, is printed in the report.
- Queue order is figure order. Fix it in the queue, not in the library.

> **Under the hood**
>
> Imported files are copied into the profile's data folder and recognised by their content and name: a picture GeoTIFF gets a PNG preview of at most 4096 px, an elevation model one at full size (up to 120 Mpx); a raster with one numeric band is an elevation model when its name says so; four or more bands make a multispectral orthomosaic; PDF, XML, CSV, point clouds and KML or KMZ are kept as documents with their metadata. Annotations are saved with each picture and drawn into its report figure. The library lives in the local profile, which is why the tab is desktop only.

<a id="photo-start-see-also"></a>

### See also

- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Delivering a claim package: originals, portal copies, custody sheet](#claim-package)
- [Orthomosaic export, linework files and volume tickets](#mapping-deliverables)

<sub>[Back to contents](#contents)</sub>

<a id="photo-report"></a>

## Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export


The Photogrammetry Survey Report builder turns a survey into a client-ready document in PDF, Word or RTF: project data, linked DJI flights, the Metashape deliverables with an embedded orthomosaic, your annotated pictures as numbered figures, measurements, material take-offs, findings and conclusions. The figures come from the report queue in the Photogrammetry tab, in the order you set there.

<a id="photo-report-before-you-start"></a>

### Before you start

- Your photos, videos and Metashape files are in the library. See [Photogrammetry: getting started](#photo-start).
- The pictures you want as figures are annotated and queued (see "The figure queue").
- For flight data, the DJI flight logs are imported in the main logbook.
- For measurements and materials, they are drawn on the queued pictures. See [Measuring lengths, angles and areas](#measure-tools) and [Material take-offs](#materials-takeoff).
- For AI drafts, the Chat connection or a provider key is chosen in Settings → **AI providers**. Drafting works with a Thermal or a Photogrammetry license; the AI narrative of the Thermal Studio needs the Thermal license.

<a id="photo-report-the-figure-queue"></a>

### The figure queue

The right column of the Photogrammetry tab, headed `Report images (N)`, holds the figures. Its order is the order of the figures in the report.

1. Select a photo, video or orthomosaic in the library and click **+ Add to report**. The notice reads `Added 1 to the report (N total).` The item gets a numbered row in the queue.
2. To add several at once, tick their checkboxes in the library, then click **+ Add to report**. Documents have no checkbox, so they cannot be ticked.
3. Or hover a library row and click its **+**. The notice names the file.
4. For a video, play or scrub to the moment you want and click **+ Add frame m:ss.s to report** under the player (for example `+ Add frame 0:07.5 to report`). The notice reads `Frame m:ss.s queued as figure N.`, and the row shows `⏱ frame m:ss.s`.
5. Type a caption in each row's `Figure N caption` box. A picture's **📝 Note** prints under its figure as well.
6. Reorder by dragging **⋮⋮**, or with **▲** (move up) and **▼** (move down).
7. On a video row, move the player and click **set to current** to take the player's position as the frame.
8. Remove a figure with **✕**. The picture stays in the library.

A still picture is queued once: adding it again says `Already in the report.` A video can be queued once per frame, so its library row can show `In report ×2`, but the same frame cannot be added twice (`That frame is already in the report.`).

The queue is saved in your profile and read when the tab opens. If it cannot be read, adding to it is refused and nothing is written, so the figures you queued earlier stay saved: the notice reads `Nothing was added: the report queue could not be read (…)`, with the reason. Add again once the reason is gone; the queue is read first and your new figure goes after the saved ones. Ticked items stay ticked after a refusal.

<a id="photo-report-steps"></a>

### Steps

1. Click **📄 Report ▼** → **Open report builder…**. The **Photogrammetry Survey Report** window opens with a blank report dated today.
2. Type a name in the `Report name` box.
3. Work down the 13 numbered sections (see the table below). Each heading reads like `9 · Survey Imagery`.
4. Click **Save as new**, later **Save**. `Report saved.` confirms it.
5. Click **Preview & edit**. In the **Edit** tab, click any text to change it in place; the **PDF** tab shows the exported file; **Refresh** re-renders after you change figures or sections.
6. Click **Export ▼** and pick **PDF**, **Word (.docx)** or **RTF**.
7. Click **Export Bundle** to save the whole survey as one `.odlbundle` file.
8. To open a survey's bundle on another machine or profile, click **📄 Report ▼** → **Import inspection bundle…** and pick the file. A message reads `Bundle imported: N new asset(s), M already present, report "…"`; with linked flights it adds `, N archived flight(s) in the bundle file` (they stay in the file and are not added to your logbook). Pictures already in the library are not copied twice, and the report appears under **Saved reports** in the builder, its name ending in `(imported)`.

| # | Section | What you do there |
|---|---|---|
| 1 | Header Data & Project Metadata | **Project name**, **Client**, site, date, **Flight time (from the flight logs)**, **Site position (from the flight logs)**, pilot, summary. AI. |
| 2 | Survey Scope | Objective, area, accuracy, deliverables requested. AI. |
| 3 | Environmental Conditions | **Weather conditions**, **Wind**, **Lighting**. |
| 4 | Flight Data (DJI) | Tick the flights that took the imagery; **↻ Fill from flight logs**. |
| 5 | Hardware, Software & Accuracy | **↻ Fill from flights & imagery** reads the aircraft, image count and altitude from the logs, the camera from the photos, the aligned cameras and CRS from the camera XML. |
| 6 | Processing Notes | Alignment, dense cloud, mesh, control points. AI. |
| 7 | Core Visual Deliverables (Agisoft Metashape) | **Embedded orthomosaic image**, the map link, the deliverables checklist, and rows from **+ Add…** or **⚡ From imported files**. |
| 8 | Topographical & Elevation Data | DEM/DSM, DTM and contour rows, from **+ Add…** or **⚡ From imported files**. |
| 9 | Survey Imagery | The figure queue, with captions, **▲**, **▼** and **✕**. |
| 10 | Advanced Analysis & Measurements | **📏 Add measurements from pictures**, **+ Add measurement**. |
| 11 | Materials and Projected Cost | **📦 Add materials from pictures**, **+ Add material**. |
| 12 | Findings & Observations (Asset Inspection Notes) | **+ Add finding**, **+ Add observation**. AI. |
| 13 | Conclusions & Recommendations | Overall condition, priorities, follow-up. AI. |

<a id="photo-report-flights"></a>

#### Flights

In **Flight Data (DJI)**, tick each flight that produced the imagery. Linking fills the survey date, the time window, the site position and the aircraft, and each later link widens them; values you typed stay. **↻ Fill from flight logs** re-applies everything and overwrites. The flights' operations data is printed in the report, and their full telemetry goes into the bundle.

<a id="photo-report-deliverables"></a>

#### Deliverables

In **Core Visual Deliverables (Agisoft Metashape)**, pick the orthomosaic to print in the report under **Embedded orthomosaic image** (or `— none —`), and paste a hosted map under **Orthomosaic map link (hosted Metashape / web map output)**. Under **Deliverables listed in the report**, tick the Metashape files to list; **Select all** and **None** help. The line below reads `N of M selected · only ticked files are listed in the report and included in its bundle.` **⚡ From imported files** adds a row per Metashape product (orthomosaic, point cloud, mesh); **+ Add…** adds one of a kind you choose. Each row has a status (`Produced` or `Not produced`), a specification and where it is hosted.

<a id="photo-report-measurements-materials-and-findings"></a>

#### Measurements, materials and findings

**📏 Add measurements from pictures** adds a row for each distance, angle, area, volume, position and slope on the queued pictures, with its method and the figure that shows it; see [Measuring lengths, angles and areas: In the report](#measure-tools-in-the-report). **📦 Add materials from pictures** does the same for the take-offs; see [Material take-offs: In the report](#materials-takeoff-in-the-report). Both skip rows already added. An area's perimeter gets a row of its own only with **Include perimeters** ticked before you press the button; perimeter rows already in the table stay when you clear it. Above the measurements a line sums the area rows, for example `Total area 1000 m² over 2 area rows`, and under the materials a line sums their plan areas, each area once, for example `Total plan area 600 m² of 1 measured area (plan area, not roof surface)`; overlapping areas are counted twice in both. A finding has a category, a severity (`Low severity`, `Medium severity`, `High severity`), a location, a **Documented in figure** link, an **Observation** and a **Recommendation**; an observation is a neutral note without a grade.

With **Add the AI cost to the report's projected cost** ticked in Settings, a report that has a client also gets an **AI analysis** row in **Materials and Projected Cost**; see [AI usage](#ai-usage-adding-the-ai-cost-to-a-report).

<a id="photo-report-ai-drafts"></a>

#### AI drafts

Sections 1, 2, 6, 12 and 13 have a **✨ AI draft** checkbox. Tick it to fill the section from the facts in the report; untick to get your own text back; **↻** writes a new draft. Without a key the box is greyed out.

<a id="photo-report-example-a-warehouse-roof-survey"></a>

### Example: a warehouse roof survey

1. Queue three damage photos and the orthomosaic. Move the orthomosaic to the top with **▲**, and type captions such as `North parapet crack` in the caption boxes.
2. Open the builder and name it `Riverside warehouse roof survey — Phase 2`. Tick the two flights in **Flight Data (DJI)**, click **↻ Fill from flight logs**, then **↻ Fill from flights & imagery**.
3. In section 7 pick `roof_ortho.tif` as the embedded orthomosaic, tick the orthomosaic, the DSM and the processing report, and click **⚡ From imported files**.
4. On the orthomosaic you outlined the roof as `A1`, a 2,000 ft² plan area at 6:12, with shingles priced at $38.50. Click **📦 Add materials from pictures**: one row, 74 bundles, $2,849.00, of which waste $231.00; in the exported table its From cell starts with `Figure 1`.
5. Add two findings, then tick **✨ AI draft** on Conclusions.
6. **Save as new**, **Preview & edit**, **Export ▼** → **PDF**. The title is followed by `Generated by Airwulf, LLC · Photogrammetry survey workflow`.

<a id="photo-report-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Queue order is figure order. Rows that point at a figure renumber themselves when you reorder, but a figure number you typed into a text (a caption, an observation) does not, so check those after reordering.
- **↻ Fill from flight logs** stays greyed out until a flight is linked.
- Documents (PDF, XML, point clouds) cannot be figures. List them as deliverables instead; only ticked files travel in the bundle.
- A thermal inspection's bundle needs the Thermal add-on: without it, **Import inspection bundle…** answers `Bundle import failed: The Thermal Analysis Studio needs a valid license: …` and keeps nothing of the bundle. With both add-ons it imports from this tab too, and a second line of the message names the tab its pictures and report show in, such as `12 pictures and the report show in the Thermal tab.` Its Metashape files show in both tabs.
- **+ New blank** appears once a saved report exists. When figures are queued it asks whether to clear them too; choose Cancel to keep them for the new report.
- Both "Add … from pictures" buttons read only the queued pictures: queue first, then import.

> **Under the hood**
>
> An AI draft sends only the facts entered in the report (project data, flights, deliverables, measurements, the material count and projected total, findings) to the provider chosen in Settings, never the images. The bundle is a single `.odlbundle` file holding the report, its figures' assets with their annotations, the ticked deliverables, the embedded orthomosaic (even when it is not ticked) and the linked flights' full telemetry; **Import inspection bundle…** in the **📄 Report ▼** menu of either studio reads it back, and a survey's bundle needs only the Photogrammetry add-on. Every report carries the publisher line "Generated by \<publisher\> · \<workflow\>" under the title: the publisher is the company saved under Settings → **Branding**, and "Airwulf, LLC" until one is saved.

<a id="photo-report-see-also"></a>

### See also

- [AI usage: the usage bar, customers and projects, and the AI cost in reports](#ai-usage)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Measuring lengths, angles and areas](#measure-tools)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Saving clients and claim details for reuse](#clients)
- [Delivering a claim package: originals, portal copies, custody sheet](#claim-package)

<sub>[Back to contents](#contents)</sub>

<a id="claim-package"></a>

## Delivering a claim package: originals, portal copies, custody sheet


A claim package is one folder an adjuster or contractor can use as delivered: the report's pictures as untouched originals renamed by what they show, JPEG copies small enough for an upload portal, the videos, a branded chain-of-custody sheet, a manifest and a checksum file.

<a id="claim-package-before-you-start"></a>

### Before you start

- The desktop app, with the Thermal or the Photogrammetry add-on enabled, and a report open in its builder: **📄 Report ▼** → **Open report builder…**.
- The report's client, address and date name the package folder; its client and claim details fill the cover sheet (see [Saving clients and claim details for reuse](#clients)).
- For your letterhead, save your company in **Settings** → **Branding**.

<a id="claim-package-steps"></a>

### Steps

1. Click **📦 Claim package…** in the builder's header, after **Export Bundle**. It shows the package name and lines such as `Pictures: 12 elevations, 8 roof slopes, 4 nadir, 2 untagged`, `Thermal: 6` and `Videos: 2`.
2. If pictures the report names were deleted from the library, it says `N pictures the report refers to are no longer in the library and are left out.`
3. Click **Choose folder…** and pick where the package goes; the package folder is created inside it.
4. Check **Portal copy size (MB)**. It starts at your setting and accepts 1 to 5; changing it here applies to this package only.
5. Choose what to write: **Originals** (on), **Portal copies** (on), **Videos** (on, when the report has videos) and **Metashape files** (off; it shows how many). **Build** stays greyed out until a folder is chosen and something would be written; hover it to see why.
6. Click **Build**. The dialog reads `Copying 7 of 31…`; **Cancel** stops after the current file. If that name or its `.building` already exists there, nothing is written and the dialog proposes `<name>_2`; click **Build** again. A leftover `<name>.building` keeps the name taken until deleted.
7. When it is done, a summary such as `31 files, 184.2 MB; 2 portal copies above the target, 1 copied unchanged (camera data)` shows. Click **Open folder** to see it in Explorer.
8. If the build is stopped, cancelled or fails, the dialog asks **Delete the incomplete package folder?** **Yes** removes it. **No** keeps it: the app lets go of the folder and says `<name>.building` can be deleted in Explorer.
9. If only the last step failed (every file is written, but renaming the folder did not work, often because antivirus software held it), choose **Retry**, **Delete** or **Leave it**. **Retry** is not offered when a folder with the final name appeared meanwhile or your license lapsed; after any other error only **Leave it** is. If deleting fails part-way, choose **Retry deletion** or **Leave it**; otherwise only **Leave it** is offered, or, when the app no longer holds the folder, the path to delete in Explorer.

To set the default size, open **Settings** → **Claim packages**, enter **Portal copy size (MB)** (1 to 5, 3 by default) and click **Save**.

<a id="claim-package-what-the-folder-holds"></a>

### What the folder holds

The folder is named `<client>_<address>_<date>`, with the project or report name for a blank client and `Claim_package_<today>` when all are blank; spaces and punctuation become `_`, at most 80 characters. It holds `Originals/` (byte-for-byte copies, renamed), `Portal/` (the upload copies, same names), `Videos/`, `Metashape/`, `Custody.pdf`, `manifest.json` and `checksums.sha256`; only folders that receive a file are created. While being written it is called `<name>.building`.

The imaging rows of the thermal report start from the library's twins (see [Pairing thermal and visual pictures](#thermal-start-pairing-thermal-and-visual-pictures)), and the package names pictures after the rows.

<a id="claim-package-naming"></a>

### Naming

Each picture is named from its camera pitch and heading, read from the file, or from your correction in the 🧭 Scale window when you made one.

| Pitch | Name |
|---|---|
| −75° or below | `Roof_Nadir_01` |
| above −75°, up to and including −20° | `Roof_Slope_East_01` |
| above −20° | `North_Elevation_01` |
| unknown, or no heading for a slope or elevation | `Photo_01` |

The direction is the side of the building the picture shows, the opposite of where the camera points. By camera heading (0° north, 90° east):

- 135° to under 225°: `North`
- 225° to under 315°: `East`
- 315° and up, or under 45°: `South`
- 45° to under 135°: `West`

A camera looking south (180°) photographs the north elevation, `North_Elevation_01`; at 100° or 140° the picture shows the west or the north side. A nadir picture needs no direction.

Numbers run in capture order, separately for each name: `North_Elevation_01`, `North_Elevation_02`, `East_Elevation_01`; a name with 100 or more pictures uses three digits. A thermal picture paired with a visual one in an imaging row takes the visual's name with `_Thermal` added, and takes no number of its own; a second and third thermal of the same visual get `_Thermal_2` and `_Thermal_3`. An unpaired thermal picture is named from its own tags and counts with the visual ones: `Roof_Nadir_03_Thermal` is the third nadir picture of the package, a thermal one.

<a id="claim-package-import-folder"></a>

### Import folder

1. In either studio, click **📂 Import folder…**, next to **+ Import photos / videos**, and pick the card's folder.
2. The app looks three folder levels deep for jpg, jpeg, png, mp4, mov and avi files and asks, for example, `Import 427 files? 300 wide, 60 zoom, 60 thermal, 7 videos.` Deeper folders are reported as skipped, dotted names ignored, TIFF files left to the single-file import.
3. Confirm. **+ Import photos / videos** reads `Importing 57 of 427…`, and at the end a notice says `Imported N, skipped K already in the library, E failed.`

Each studio files the pictures in its own library. A folder with more than 5,000 pictures and videos is refused: `The folder holds more than 5,000 files; import a subfolder.`

In the Photogrammetry library the **Wide** and **Zoom** chips filter by the file name's ending (`_W` or `_V` wide, `_Z` zoom); **Photos** shows every photo. Each card shows a badge such as `North elevation`, `Roof slope, east side`, `Roof, nadir` or `Untagged`, from the file's own tags (not your corrections); the Thermal library shows it on every picture except radiometric ones.

<a id="claim-package-example-riverside-holdings-llc-12-main-st"></a>

### Example: Riverside Holdings LLC, 12 Main St

1. A photogrammetry report for `Riverside Holdings LLC`, site `12 Main St`, surveyed 2026-11-03, holds 26 figures: 19 wide photos at −2° to −8° (five each facing about 180°, 90° and 0°, four about 270°); 4 roof slopes at −45° facing about 270°; 2 nadir at −89°; one video frame.
2. **📦 Claim package…** proposes `Riverside_Holdings_LLC_12_Main_St_2026-11-03` and lists `Pictures: 19 elevations, 4 roof slopes, 2 nadir` and `Videos: 1`.
3. After **Build**, `Originals/` holds `North_Elevation_01…05.jpg`, `West_Elevation_01…05.jpg`, `South_Elevation_01…05.jpg`, `East_Elevation_01…04.jpg`, `Roof_Slope_East_01…04.jpg` and `Roof_Nadir_01…02.jpg`.
4. `Portal/` holds 25 copies under 3 MB, two of them reduced to 4000 pixels. `Videos/Video_01.mp4`, `Custody.pdf` with your letterhead, `manifest.json` and `checksums.sha256` complete it.

<a id="claim-package-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Videos are copied byte for byte into `Videos/`; they get no portal copy.
- Thermal R-JPEG portal copies are never shrunk; one over the size stays above the target.
- After a finished build or **Leave it** there is no **Build** button; close and reopen the dialog to build again.

> **Under the hood**
>
> One MB is 1,000,000 bytes. A portal copy is re-encoded only when the file's own bytes show a plain photo: radiometric pictures, files with camera-maker data (DJI thermal R-JPEGs among them), PNG and anything unusual are copied unchanged; the sheet counts them, and one larger than the size is counted above the target. A photo at or under the size is copied; otherwise the highest quality from 92 to 62 that fits is used; failing that, the longest edge is reduced to 4000, 3000 and 2400 pixels at quality 78; if nothing fits, the smallest copy is kept and counted above the target. EXIF and XMP are carried over unchanged; a reduced copy keeps the original's EXIF pixel size and thumbnail.
>
> Each original is checked against the SHA-256 digest recorded when it was imported; if the library copy changed, the build stops. The sheet then states `The N originals are byte-for-byte copies of the files as imported into Open DroneLog; each was verified against the SHA-256 recorded at import.`, or says how many have no recorded digest. The sheet lists the media files' digests; the manifest lists them and the sheet's; the checksum file lists every file, the manifest included. The checksums show the files match the manifest; they do not prove the capture data genuine, nor any custody outside the package.

<a id="claim-package-see-also"></a>

### See also

- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Saving clients and claim details for reuse](#clients)
- [Side-by-side documents and temperature exports](#thermal-deliverables)
- [Branding your reports: logo, company and Part 107 number](#settings-branding)

<sub>[Back to contents](#contents)</sub>

<a id="mapping-deliverables"></a>

## Orthomosaic export, linework files and volume tickets


Three buttons turn a measured survey into files other people can use. **🗺 Export orthomosaic…** writes a Metashape orthomosaic as a JPG with its world file, so a GIS or CAD program places it on the map, plus an optional presentation copy with a scale bar, a north arrow, the title and your letterhead. **📐 Export linework…** writes the measurements and drawings of a picture as DXF, GeoJSON and ODL XML. **🧾 Volume ticket…** prints a numbered, signable document for one measured volume: cut, fill and net with their ±, the sources, a figure and, with a material, the tonnage.

<a id="mapping-deliverables-before-you-start"></a>

### Before you start

- Use the desktop app with the Photogrammetry add-on. The three buttons are in the top bar of the Photogrammetry tab, after **📂 Import folder…**; **📐 Export linework…** is also in the Thermal Studio's top bar.
- For an orthomosaic export: a Metashape orthomosaic GeoTIFF in the library with three or four bands of 8- or 16-bit colour. Otherwise the button is greyed out and its tooltip says why, for example `A one-band or float raster (thermal or elevation) has no colours to export` or `Select an orthomosaic to export it`.
- For linework: a still picture with at least one measurement or drawing on it (`Select a still picture with a measurement or drawing on it`). Map coordinates need a georeferenced orthomosaic or easting/northing GCPs; see [Positions, ground control points and georeferenced orthomosaics](#measure-geo). Heights need a paired elevation model; see [Elevation models](#measure-elevation).
- For a ticket: a picture with an **⬠ Area** that has a volume, from the elevation model or a solid (`Select a still picture with an area that has a volume`). See [Volume inside an area](#measure-elevation-volume-inside-an-area).
- For the letterhead on the presentation copy and the ticket, save your company in **Settings** → **Branding**; for a client line, save the client first (see [Saving clients and claim details for reuse](#clients)).

<a id="mapping-deliverables-exporting-an-orthomosaic"></a>

### Exporting an orthomosaic

1. Select the orthomosaic in the Photogrammetry library and click **🗺 Export orthomosaic…**. The dialog **🗺 Export orthomosaic** opens.
2. Under **Resolution** choose **Full (the raster as stored, up to 120 megapixels)** or **Web (up to 24 megapixels)**. The line below gives the size of the JPG, for example `4000 × 3000 px · 0.04 m per pixel · about 4.5 MB`. A raster larger than the budget is reduced by a whole factor: each output pixel is the average of a square block of source pixels.
3. Leave **Presentation copy (scale bar, north arrow, title and letterhead; web resolution)** ticked to get a second JPG for people, or untick it for the georeferenced files alone.
4. Check the **Title**. It starts as the orthomosaic's name without its extension and names the files: spaces and punctuation become `_`, so `Smith quarry, May` gives `Smith_quarry_May.jpg`. An empty title gives `Orthomosaic`.
5. Pick a **Client** for the presentation copy, or leave **None**. The box is greyed out while the presentation copy is unticked: the georeferenced JPG carries no text.
6. Click **Export…** and choose the folder. The dialog reads `Writing <name>.jpg… (large orthomosaics take a minute)`, then `Composing the presentation copy…`.
7. If files of this export already exist in the folder, the dialog says, for example, `3 files will be replaced, 1 removed`, and lists them; a file marked "(an earlier export's file, removed)" is a sidecar this export would not write again, such as a `.wld` written by another program, or the `.crs.txt` of a different orthomosaic exported under the same title. Click **Replace all** or **Cancel**. There is no "skip": a JPG and its world file are replaced together or not at all.
8. Read the result: `Exported to <folder>`, then one line per file written with its size (and, when the raster was reduced, how many source pixels were averaged), a line for each sidecar, and any warning. A line naming a leftover part file or recovery copy from an earlier export points at a file the app did not remove; delete it yourself once the export is fine. Click **Done**.

The folder then holds:

| File | Holds | Read by |
|---|---|---|
| `<title>.jpg` | the picture, clean (no text, no arrow) | everything; placed on the map only with its world file |
| `<title>.jgw` | the world file: pixel size and the map position of the top-left pixel's centre | QGIS, ArcGIS Pro, AutoCAD Map 3D, Civil 3D |
| `<title>.prj` | the coordinate system as ESRI WKT | ArcGIS Pro |
| `<title>.jpg.aux.xml` | the coordinate system for GDAL | QGIS and other GDAL programs |
| `<title>.crs.txt` | instead of the two above, for any other coordinate system: `EPSG:<code> (<name>): set it in your GIS when loading` | you: set the CRS by hand when loading |
| `<title>_presentation.jpg` | the presentation copy | any picture viewer, a report, an email |

The `.prj` and `.jpg.aux.xml` are written for WGS 84 / UTM zones and for WGS 84 latitude/longitude. An orthomosaic without georeferencing (no tiepoint or pixel size, or a rotated GeoTIFF) is written as the JPG alone, with the line `No georeferencing in this file: no world file`.

If the presentation copy's name belongs to a georeferenced JPG already in the folder (there is a `<title>_presentation.jgw` beside it), nothing is written and the dialog says `A georeferenced JPG is already called <title>_presentation.jpg: choose another title`. Any other failure reads `Could not export the orthomosaic: …` and says whether the earlier files were left unchanged.

<a id="mapping-deliverables-the-white-collar"></a>

#### The white collar

A Metashape orthomosaic is a rotated patch of ground inside a rectangle; the corners outside the survey have no data. JPG has no transparency, so the export paints them white (255, 255, 255). An output pixel at the edge of the patch is the average of the source pixels that have data, so the edge is not darkened.

To hide the collar in QGIS, open the layer's *Properties*, go to *Transparency*, and under *Custom transparency options* add a row to the transparent pixel list with red 255, green 255 and blue 255 at 100 % transparency. JPEG compression leaves a few near-white pixels along the edge; they show as a thin fringe. In ArcGIS Pro, set the layer's background value to 255, 255, 255 in its symbology.

<a id="mapping-deliverables-the-presentation-copy"></a>

#### The presentation copy

The presentation copy is the web-size picture with a white band below it: your logo, company and operator line on the left; the title, the client and the date in the middle; the coordinate system and pixel size along the bottom, for example `CRS WGS 84 / UTM zone 16N · 0.04 m per pixel (source 0.02 m) · 4000 × 3000 px`; the scale bar and the north arrow on the right. It has no world file and is not for a GIS: it is the picture for a report or an email.

- The scale bar is a round length (1, 2 or 5 × a power of ten, in metres or kilometres, or feet or miles under imperial units) of about a fifth of the picture's width, in black and white halves, measured at the picture's centre.
- The north arrow labelled `True north` points to true north as it runs through the raster at the picture's centre. On a UTM orthomosaic it leans off vertical by the grid convergence: east of the zone's central meridian in the northern hemisphere it turns to the left (counter-clockwise), by about the longitude difference × sin(latitude), so 1.3° at 2° from the meridian and 41° N.
- The arrow labelled `Grid north` points straight up. It appears when the coordinate system cannot be turned into latitude and longitude (a projected system other than WGS 84 / UTM, such as a state plane or NAD83 / UTM). Up is then the grid's north, not true north.
- A picture without georeferencing has no arrow, and a scale bar only when the orthomosaic states a pixel size.

<a id="mapping-deliverables-exporting-linework"></a>

### Exporting linework

1. Select the picture (an orthomosaic or a photo) and click **📐 Export linework…**. The dialog **📐 Export linework** opens with the picture's name.
2. Under **Formats** tick **DXF (AutoCAD R12)**, **GeoJSON (WGS 84)** and **ODL XML**, any of them. GeoJSON is greyed out with the reason `needs a WGS 84 position (a WGS 84 UTM or geographic orthomosaic, GCPs with latitude/longitude, or a camera position)` when the picture has none.
3. Under **Coordinates** choose the frame for the DXF and XML (see "Coordinate frames" below). The choices name their axes, for example `Map coordinates (metres, x east, y grid north)`, `Reference plane (x right, y forward)` or `Pixels (the orthomosaic's own pixels)`. A frame the picture cannot give is greyed out with its reason.
4. Tick **Heights from the elevation model** to write elevations. It is greyed out with `Needs an elevation model paired with the orthomosaic` otherwise.
5. Click **Export…**. With one format ticked, a save dialog proposes `<picture>.dxf`, `.geojson` or `.odl.xml`; with several, choose a folder and the files get those names.
6. If files of those names exist in the folder, the dialog says, for example, `2 files exist`, and offers **Replace all**, **Skip existing** or **Cancel**.
7. Read the result: `Wrote 3 files to <folder>: …` with each file's size, then a line for anything the files could not hold, for example `A3 is above the horizon and was left out` or a self-intersecting outline in the GeoJSON. Click **Done**.

Every measurement and drawing goes in: measure lines, references, slopes, angles, areas of any shape, positions, GCPs, lines, arrows, curves, freehand strokes, rectangles, circles and texts. The scale override and the material take-offs do not. Each annotation is one feature on a layer by its kind: `MEASURE`, `REFERENCE`, `SLOPE`, `ANGLE`, `AREA`, `POSITION`, `GCP`, `DRAWING` (the sketches) and `TEXT`. Measured features carry the numbers of their labels: length and bearing, area and perimeter, pitch, cut, fill and net, each with its ±.

| Format | What it is | Open it in |
|---|---|---|
| DXF | AutoCAD R12 drawing: polylines, points and texts on the layers above, the measure labels as text with their unit, the units, frame, CRS and vertical reference as comments | AutoCAD, Civil 3D, AutoCAD Map 3D, BricsCAD, QGIS |
| GeoJSON | the features in WGS 84 longitude and latitude, the measures as properties | QGIS, ArcGIS Pro, geojson.io |
| ODL XML | Open DroneLog's own documented file: every vertex in the chosen frame and in the picture's pixels, every measure with its unit and ± | your own scripts or a program that reads XML |

Google Earth reads KML and KMZ: it places neither the orthomosaic JPG nor these files. Plain AutoCAD (without Map 3D or Civil 3D) ignores world files: the JPG comes in at the origin at one unit per pixel, so place it by hand or use the DXF alone.

<a id="mapping-deliverables-coordinate-frames"></a>

#### Coordinate frames

| Frame | Origin and axes | Unit |
|---|---|---|
| **Map coordinates** | the orthomosaic's coordinate system, or the grid of easting/northing GCPs: x east, y grid north | metres, or the CRS's feet |
| **Reference plane** | the picture's own measuring plane. A tilted photo: the point under the camera, x right, y forward. An orthomosaic: its centre, x east, y grid north. A flat picture: its centre, x right, y up | metres |
| **Pixels** | the picture's top-left corner, x right, y down; for an orthomosaic its own raster pixels, which match the Full JPG (divide by the factor for a Web JPG) | pixels |

- Map coordinates are offered with a projected orthomosaic (UTM or another projected system) or with easting/northing GCPs. A latitude/longitude orthomosaic or GCP fit has none: `Map coordinates need a projected CRS; this picture's positions are latitude/longitude`. Use GeoJSON, or the reference plane, instead.
- The reference plane needs a scale (`The picture has no scale yet`). A point drawn above the horizon of a tilted photo has no place on it: its feature is left out and the result says so.
- Pixels is always offered. The DXF writes the rows upwards, so the drawing is upright; the XML keeps y down, as its frame says. GeoJSON is always in longitude and latitude, whatever frame you choose.

<a id="mapping-deliverables-heights-and-the-vertical-reference"></a>

#### Heights and the vertical reference

With **Heights from the elevation model** ticked, every vertex of every feature gets the elevation model's height under it. A feature is written in 3D only when **every** vertex has a height; if one falls on a cell without data, the whole feature is written flat and marked `zMissing`. A missing height is never written as 0.

- Heights are in the frame's unit (metres, or the CRS's feet) and in the elevation model's vertical reference, which the file names: the DXF comment `vertical: EPSG:5703 (metre)`, the XML's `verticalEpsg`, the GeoJSON's `verticalEpsg` property. Metashape's heights are usually above the geoid (orthometric), not above the ellipsoid.
- The GeoJSON never has a third coordinate (RFC 7946 heights would be ellipsoidal); the heights are in each feature's `zM` property, in metres.
- In the Pixels frame the geometry stays flat in the DXF and the XML; the XML then lists the heights in the feature's `zM` attribute, in metres.

<a id="mapping-deliverables-printing-a-volume-ticket"></a>

### Printing a volume ticket

1. Select the picture in the Photogrammetry library and click **🧾 Volume ticket…**. The dialog **🧾 Volume ticket** opens.
2. Under **Outline**, pick the area. Each line shows its name, its volume as the take-offs read it and the method (`elevation model` or `solid`); `no volume` means the area has none yet.
3. Check the **Ticket number**. It is prefilled with the next automatic number, `VT-<yyyymmdd>-<n>` (see "Ticket numbering" below).
4. Type the **Site / project**. It starts with the site of your last ticket.
5. Pick a **Client**, or **No client**.
6. For tonnage, pick a **Material** with a density from your catalogue, or **Other…** and type the density in kg/m³ (lb/ft³ under imperial units). When the area already has a volume take-off with a density, its material and part are preselected. The dialog then shows `Mass before waste: …`.
7. For an elevation-model volume, pick the **Part**: **Cut (above the base)**, **Fill (below the base)** or **Net |cut − fill|**. The default is the larger of cut and fill, as in the take-offs. A solid has one volume and no part.
8. Add **Notes** (at most 10 lines; longer notes are cut), keep or untick **Signature lines**, and pick the **Format**: PDF, Word (.docx) or RTF.
9. Click **Build…**. The number is reserved first, the ticket is rendered, and a save dialog proposes `<ticket number>.pdf`.
10. Read the line under the form: `Volume ticket VT-… saved: <path>`, or `Not saved: number 4 is used up (a gap); nothing was written` when you dismissed the save dialog. **Build…** stays greyed out while the area has no volume (`The outline has no volume: pair an elevation model or set a solid height`) or the number is empty.

The ticket is one page, two at most. It prints your letterhead, the title `Volume ticket <number>` with the site, client and date, then:

- **Measurement**: the outline, the method and base, the outline and sampled areas, cut, fill and net with their ±, the base elevation and tilt, the cell size, the missing data share, the elevation range and the warnings; for a solid the area, the typed height and the volume. The note `± is 1σ, conservative (the elevation model's error taken as one shift over the area)` explains the ±.
- **Sources**: the orthomosaic and elevation model with their coordinate system, pixel size, vertical reference and accuracy, the scale source, the stored files' hashes and the calculation time.
- The figure: the picture with the chosen outline and its label only.
- **Material**, when chosen: the material, the density, the part and the mass (part × density), in t or short tons. No waste is added: a ticket states what was measured, a take-off what to order.
- **Notes**, then the signature block `Measured by` and `Verified by`, each with a date line.

<a id="mapping-deliverables-ticket-numbering"></a>

### Ticket numbering

- The automatic number is `VT-<date>-<n>`: the build date and a counter kept in your profile, which counts up by one for every ticket and never starts again at 1 on a new day. The first ticket of a profile, built today, is `VT-20261109-1`.
- The number is reserved when you press **Build…**, before the document is rendered. If you then dismiss the save dialog or the write fails, the number is used up: the next ticket gets the next one, and the numbers have a gap. A gap is harmless; it shows a ticket was started.
- If another ticket took the number meanwhile, the ticket uses the reserved one and says so: `Volume ticket VT-20261109-8 saved; 7 was taken meanwhile`.
- A number you type yourself is used as typed and never touches the counter. If it has the form `VT-…-<n>` and n is not below the next automatic number, the dialog warns, for example `Number 9 is not below the next automatic number (5): this number will collide with a later ticket.`
- The counter lives in the profile's database. Restoring a database backup brings back the counter as it was then, so the next automatic number can repeat a ticket you already issued. After a restore, open **Settings**, find **Volume tickets**, type a **Next number** above the last ticket you issued and click **Set next number**.
- If the stored counter cannot be read, **Build…** refuses with `The ticket counter could not be read; set the next number in Settings → Volume tickets`; the **Volume tickets** section says the stored value is kept as a backup, and **Set next number** replaces it.

<a id="mapping-deliverables-limits"></a>

### Limits

- NAD83 / UTM orthomosaics (EPSG 269xx), common in US work, get a `.crs.txt` instead of a `.prj`, a `Grid north` arrow and no GeoJSON. The exports stay in the orthomosaic's own system; nothing is reprojected.
- Rotated GeoTIFFs (with a model transformation) are not georeferenced in the app: the export writes the JPG without a world file.
- One-band rasters (grey, thermal, elevation) and float rasters have no colours to export; the button stays greyed out.
- The linework is the app's own measurements; it cannot be read back in, and the ODL XML has no schema file.

<a id="mapping-deliverables-example-a-stockpile-yard"></a>

### Example: a stockpile yard

`yard_ortho.tif` is a WGS 84 / UTM zone 16N orthomosaic of 8000 × 6000 px at 2 cm per pixel, with `yard_DSM.tif` paired. The DSM holds a pit like the one in [the elevation example](#measure-elevation-example-a-stockpile-and-a-pit): fill 120 m³.

1. **🗺 Export orthomosaic…** with **Full** reads `8000 × 6000 px · 0.02 m per pixel · about 18 MB`. With **Web** it reads `4000 × 3000 px · 0.04 m per pixel · about 4.5 MB`: 48 megapixels is over the 24 MP budget, so the factor is 2 and each output pixel averages 2 × 2 source pixels. 4000 × 3000 × 3 bits ÷ 8 is 4.5 MB.
2. You choose **Web**, keep the presentation copy and the title `yard_ortho`, and export. The folder holds `yard_ortho.jpg`, `yard_ortho.jgw`, `yard_ortho.prj`, `yard_ortho.jpg.aux.xml` and `yard_ortho_presentation.jpg`. The `.jgw`'s first line is `0.04`, the pixel size in metres.
3. The presentation copy is 4000 px wide and covers 160 m of ground, so a fifth of it is 32 m. No round length falls between 15 and 25 % of the width (24 to 40 m), so the nearest one, `50 m`, is drawn, 1250 px long. The band is 210 px high (7 % of 3000 px).
4. **📐 Export linework…** with all three formats, **Map coordinates** (metres, x east, y grid north) and heights writes `yard_ortho.dxf`, `yard_ortho.geojson` and `yard_ortho.odl.xml` into the folder you pick. In QGIS the GeoJSON and the JPG line up.
5. **🧾 Volume ticket…** on the pit, part **Fill (below the base)**, material crushed stone at 1,600 kg/m³: the dialog shows `Mass before waste: 192 t` (120 m³ × 1.6 t/m³), or `Mass before waste: 212 short tons` under imperial units. The take-off on the same pit orders 233 tons, because it adds 10 % waste and rounds up.
6. Built today as the profile's first ticket, it is saved as `VT-20261109-1.pdf`.

<a id="mapping-deliverables-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Send the JPG with all its sidecars: without the `.jgw` it is only a picture, and without the `.prj` or `.aux.xml` the GIS asks for the coordinate system.
- Rename the title, not the files: a JPG renamed in Explorer loses its world file, which must carry the same name.
- Do not open the presentation copy in a GIS: it has a band of text and no world file.
- For CAD, export the linework in **Map coordinates**: the DXF and the world file then share one coordinate system. **Pixels** suits a drawing traced over the picture itself.
- A ticket for a pile: use the cut or the net. The fill ± around a pile can exceed the fill itself.

> **Under the hood**
>
> The world file is six lines: the pixel width, two zero rotation terms, the negative pixel height, and the map position of the centre of the output's top-left pixel, all for the export's factor. Coordinates have 6 decimals in a projected system and 12 in degrees. The Full JPG keeps the raster as stored within 120 megapixels and 65,535 px a side; the Web JPG and the presentation copy within 24 megapixels (the presentation copy also within 6,000 px a side). A reduced pixel is the mean of the non-empty pixels of its f × f block; an empty one is white. Both JPGs are written at quality 90.
>
> The true-north arrow is found by moving 100 m north along the meridian from the picture's centre and mapping that point back into the raster, so unequal pixel sizes are honoured. The linework's numbers are the labels' numbers. GeoJSON polygons follow the right-hand rule after projection, and nothing crossing the antimeridian is split. A ticket's mass ± is the part's ± × the density.

<a id="mapping-deliverables-see-also"></a>

### See also

- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Positions, ground control points and georeferenced orthomosaics](#measure-geo)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Measuring lengths, angles and areas](#measure-tools)
- [Branding your reports: logo, company and Part 107 number](#settings-branding)
- [Saving clients and claim details for reuse](#clients)

<sub>[Back to contents](#contents)</sub>


---

# 360 Panorama Studio

<a id="panorama-start"></a>

## 360 Panorama Studio: getting started, importing, sets and marking up photos


The 360 Pano tab turns the photos of one drone hover into one 360-degree photo. You import the photos, the studio groups them into sets, and you can draw on each photo. Then you stitch a set into a 360 (see [Stitching a 360](#panorama-stitch)) and look around it or export it (see [Looking around a 360 and exporting it](#panorama-export)). This topic covers setting up, importing, the library and the mark-up tools.

<a id="panorama-start-what-this-studio-does"></a>

### What this studio does

Each row names a feature, where you find it, and the walkthrough that explains it.

| Feature | Where | Walkthrough |
|---|---|---|
| Import photos | **+ Import photos** or **📂 Import folder…** in the top bar, or drop files on the window | [Steps](#panorama-start-steps) |
| Sets and the library | The left column, with the tabs `Photos (N)` and `360s (N)` | [The library](#panorama-start-the-library) |
| Draw on a photo | The toolbar above an open photo | [Mark up a photo](#panorama-start-mark-up-a-photo) |
| Leave a photo out of a stitch | **Leave out of 360** in the same toolbar | [Leave photos out](#panorama-start-leave-photos-out) |
| Stitch a set | The right column, headed `Stitch 360` | [Stitching a 360](#panorama-stitch-steps) |
| Look around a 360, starting view, exports | Above an open 360 | [Looking around a 360](#panorama-export-steps) |

<a id="panorama-start-before-you-start"></a>

### Before you start

- Use the desktop app. The library keeps the photos in your local profile, so the tab is not available in the web version.
- Install the add-on: open **Settings** (the gear at the top of the sidebar) and click **Open Add-ons**. Click **Download installer…** for the 360 Panorama Studio, run the installer, then click **↻ Refresh**. The 360 Pano tab appears in the sidebar.
- The add-on needs a license. Until it has one, the tab shows a lock panel instead of the studio. See [Buying, activating and renewing an add-on license](#addon-license).
- Have the photos of a 360 capture at hand: the jpg or png files the drone took while it hovered in one place and turned. The studio needs the camera angles the drone writes into each photo. DJI photos have them.

<a id="panorama-start-steps"></a>

### Steps

1. Open the 360 Pano tab. The top bar shows the 🌐 360 Panorama Studio title. The library is on the left, the photo or the 360 in the middle and the Stitch panel on the right.
2. Click **+ Import photos** and pick the photos. Or drag them onto the window: the overlay reads `Drop jpg or png photos to import`.
3. Wait while the button reads `Importing 3 of 24…`. The photos appear in the library, grouped into sets, and the first new photo opens. A line at the top reads `Imported 24, skipped 0 already in the library, 0 failed.`
4. Click a photo in the library. It opens in the middle with the mark-up toolbar above it.
5. Draw on it if you want to point something out (see "Mark up a photo" below). What you draw is saved with the photo.
6. Look at the Stitch panel on the right. It works on the set of the photo you opened. Continue with [Stitching a 360](#panorama-stitch).

To import a whole camera folder, click **📂 Import folder…** and pick the folder. The studio looks at the photos (jpg, jpeg and png) and the videos in the folder and in its subfolders, up to three levels deep, and asks `Import 120 files? …` first. Only the photos are imported. When it is done, a line reads `Imported 100, skipped 2 already in the library, 0 failed.` and, when the folder held videos, `18 other files ignored.` under it. The count is for videos only: other kinds of files are not looked at and not counted. A folder with more than 5,000 files is refused: pick a subfolder instead.

The studio imports jpg and png photos only. A file of another type that you pick or drop is refused with a line such as `DJI_0001.MP4: the 360 studio imports jpg and png photos`.

A photo that is already in the program's library cannot be imported again. This includes a photo you imported into the Thermal or Photogrammetry tab: it stays there and does not show in the 360 Pano tab. The line after the import counts such photos, for example `Imported 22, skipped 2 already in the library, 0 failed.`

<a id="panorama-start-the-library"></a>

### The library

The library has two tabs: `Photos (N)` lists the photos, grouped into sets, and `360s (N)` lists the finished 360s.

1. Read the set headers. Each one reads like `24 photos · 3 Oct 2026, 14:22:01`: the number of photos and the time of the first photo.
2. Click a header to fold the set (▶) or open it again (▼). The set of the open photo always stays open.
3. Read the rows. A photo shows 📷 and its name. A photo you left out of the stitch is dimmed and has the tag `left out`.
4. Click the `360s (N)` tab to see the finished 360s, newest first. A row shows 🌐, the name and the size, for example `16384 × 8192`.
5. Read the line under the photo or the 360: its name, **✏️** to rename it, **🗑 Delete**, `Photo` or `360`, the size, the camera, the position (📍) and the capture time.
6. To rename, click **✏️**, type the name and press Enter. Esc cancels.
7. To delete one photo, click **🗑 Delete** under it and confirm. The photo file and its mark-ups are removed. A 360 stitched from it keeps its picture and loses the mark-ups of this photo.
8. To delete several photos, tick their checkboxes in the `Photos (N)` tab, or tick **Select all**. Then click **Delete selected…** and confirm. The question says how many of them are photos of a finished 360, for example `Delete 3 photos from the library? Their files and mark-ups are removed. 1 is a source of a finished 360: its mark-ups from it will disappear.`
9. To delete a 360, click **🗑 Delete** on its row in the `360s (N)` tab and confirm. The 360 file is removed; its photos stay.

A set is the photos of one hover. The studio sorts the photos by capture time. A new set starts when a photo was taken more than 60 seconds after the one before it, or more than 8 metres from the first photo of the set. You do not make sets yourself.

Nothing can be deleted while an import or a stitch is running. The line then reads `Nothing was deleted: an import or a stitch is running.`

<a id="panorama-start-mark-up-a-photo"></a>

### Mark up a photo

1. Open a photo. The toolbar shows the tools **Select**, **Zoom**, **Arrow**, **Line**, **Curve**, **Circle**, **Box**, **Draw**, **Text**, **Outline** and **Erase**.
2. Pick a colour from the swatches, and press **Dashed** if you want dashed lines.
3. Draw. **Outline** draws a closed shape: click the corners, then click the first corner, double-click or press Enter to finish. Backspace removes the last corner.
4. Read the counter at the right end of the toolbar, for example `3 annotations · saved with the photo and shown on the 360`.
5. Press **↩ Undo** to remove the last mark-up, or **✕ Clear** to remove them all (the app asks `Remove all annotations on this photo?` first).

Zooming, panning and the other tools work as in the other studios. See [Viewing and annotating pictures](#annotate).

Your mark-ups stay editable after you stitch. A finished 360 shows the mark-ups of its photos as they are now, so you do not need to stitch again after a change.

You cannot draw on the 360 itself. Draw on its photos.

The measuring tools and notes of the other studios are not offered here. A 360 joins many photos taken in different directions, so it has no single scale for lengths and areas.

<a id="panorama-start-leave-photos-out"></a>

### Leave photos out

Sometimes one photo spoils a stitch, for example a photo with a bird in it, or one taken while the drone was still moving.

1. Open the photo.
2. Press **Leave out of 360** in the toolbar. The button stays lit, and the photo's row is dimmed with the tag `left out`.
3. Read the Stitch panel. It now reads `1 photo left out by you.` and stitches without that photo.
4. To take the photo back, press **Leave out of 360** again. Or click **Put back** in the Stitch panel: it puts back every left-out photo of the set.

The choice is kept until you close the program. It is not saved with the photo. While a stitch runs, **Leave out of 360** is greyed out.

<a id="panorama-start-example-a-360-over-a-farm"></a>

### Example: a 360 over a farm

You flew a DJI drone to 60 m over a farm, let it hover and took 26 photos while it turned: three rows around and some straight down.

1. Click **📂 Import folder…** and pick the card's photo folder. Confirm the question. The line reads `Imported 26, skipped 0 already in the library, 0 failed.`
2. The `Photos (26)` tab shows one set, `26 photos · 3 Oct 2026, 14:22:01`.
3. Open the photo that shows the barn. Pick red and draw a **Box** around a damaged roof panel. Pick **Text**, click beside it, type `roof panel`, press Enter.
4. One photo shows the drone's landing gear. Open it and press **Leave out of 360**. The Stitch panel reads `1 photo left out by you.`
5. Stitch the set (see [Stitching a 360](#panorama-stitch)). The box and the label appear on the 360 where the barn is.

<a id="panorama-start-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Import the photos of one capture together. A set is made from capture time and position, so photos of two hovers less than a minute apart can land in one set if the drone did not move more than 8 m.
- A photo that was already imported in another tab does not come into the 360 library. A photo is kept in one tab only, so import the photos of a 360 capture here first.
- Mark a spot on one photo only. The 360 shows the mark-ups of every photo, so a spot you mark on two overlapping photos shows twice.
- A left-out photo is back in the stitch after you restart the program. Check the Stitch panel before you stitch again.

> **Under the hood**
>
> Imported photos are copied into the profile's data folder and kept in the program's one picture library; the 360 Pano tab lists only the photos imported here and the 360s stitched here. A photo is recognised by its content, so the same file is never stored twice, whatever tab imported it. Sets are rebuilt from capture time and position every time the library is read: a gap of more than 60 s, or more than 8 m from the first photo of the set that has a position, starts a new set. Mark-ups are stored per photo in the photo's own pixels.

<a id="panorama-start-see-also"></a>

### See also

- [Stitching a 360: the Stitch panel, camera angles, size, warnings](#panorama-stitch)
- [Looking around a 360, the starting view and the exports](#panorama-export)
- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Buying, activating and renewing an add-on license, and updating add-ons](#addon-license)

<sub>[Back to contents](#contents)</sub>

<a id="panorama-stitch"></a>

## Stitching a 360: the Stitch panel, camera angles, size, warnings


The Stitch panel on the right of the 360 Pano tab joins the photos of one set into one 360-degree photo. Before you stitch, it shows how much of the sphere the photos cover and which photos it cannot use. While it stitches, it shows the progress. Afterwards it reports how well the photos fitted together.

<a id="panorama-stitch-before-you-start"></a>

### Before you start

- The photos of a 360 capture are imported. See [360 Panorama Studio: getting started](#panorama-start).
- Open a photo of the set you want to stitch, or a 360 made from that set. Without one, the panel reads `Select a photo to stitch its set.`
- Each photo must carry the camera angles the drone writes into it (where the camera pointed). DJI photos have them.

<a id="panorama-stitch-steps"></a>

### Steps

1. Open a photo of the set. The panel, headed `Stitch 360`, reads `Reading the set…` for a moment.
2. Look at the coverage map. The box is the whole sphere laid flat: left to right is all the way around, top is straight up, bottom is straight down, and the dashed line is the horizon. Each blue shape is one photo, placed by its camera angles. Under the box, a line such as `Covers 78.4 % of the sphere` gives the share the photos cover.
3. Read the lines under the map: the number of photos (`26 photos`, or `26 photos, 24 usable`), `Camera angles: from the photos`, and one line for each photo the studio cannot use, for example `DJI_0412.JPG: no camera angles`. The table below says what each reason means.
4. Pick the **Output size**, for example `8192 × 4096`. The list offers only the sizes your photos have enough detail for; `4096 × 2048` is always there. The panel starts at `8192 × 4096` when it is offered.
5. Leave **Fill uncovered sky** ticked to fill the parts of the sphere that no photo covers, or untick it to leave them black.
6. Click **Stitch 360**. A bar fills and a line names the step, for example `Matching overlaps: 40 of 120`. The steps are `Reading photos`, `Matching overlaps`, `Solving camera angles`, `Blending`, `Filling gaps` (only when the fill is ticked) and `Saving`.
7. Wait until a line at the top reads `360 ready: 360_20261003-142201.jpg`. The new 360 is listed in the `360s (N)` tab and under `360s of this set` in the panel. It opens by itself if you did not open or change anything while it was stitching.
8. Read the result under `Last stitch` (see the next section).

To stop a stitch, click **Cancel**. The line `Stitch cancelled.` appears and nothing is saved.

The first usable photo of the set, by capture time, gives the 360 its name and its centre: the name is `360_<date>-<time>.jpg` with the capture time of that photo, and the centre faces the way that photo faced. A photo you left out does not count. When that photo carries no capture time, the time of the stitch is used in the name. Every stitch makes a new 360; the earlier ones stay in the library.

<a id="panorama-stitch-why-a-photo-is-not-used"></a>

### Why a photo is not used

| Line | What it means |
|---|---|
| `no camera angles` | The photo carries no record of where the camera pointed, or the record is incomplete. |
| `no focal length` | The photo does not say which lens focal length it was taken with. |
| `rotated photo` | The photo is marked as turned (portrait or upside down). |
| `digital zoom` | The photo was taken with digital zoom. |
| `different size` | The photo has another picture size than most photos of the set. |
| `different focal length` | The photo was taken with another lens or zoom than the others. |
| `unreadable picture` | The file could not be read. |

Such a photo stays in the library. The other photos are stitched without it.

The photos of a 360 must all come from one camera at one setting. When a set mixes two lenses, for example wide and zoom pictures, the studio keeps the most common picture size. Of those photos it takes the middle value of the focal lengths and leaves out every photo whose focal length differs from it by more than 1 %, for example photos taken with zoom.

A line such as `2 photo(s) cannot be used.` counts the photos of this table. The photos you left out yourself are counted in their own line, `1 photo left out by you.`

<a id="panorama-stitch-when-stitch-360-is-greyed-out"></a>

### When Stitch 360 is greyed out

Point at **Stitch 360** to see why.

- `Fewer than 2 photos can be used.` A 360 needs at least 2 usable photos. The panel also reads `At least 2 usable photos are needed to stitch a 360.`
- `Fewer than 2 photos are included.` The set has only one photo, or you left out all but one. Click **Put back** to take the left-out photos back.
- `This set has 230 photos; a 360 takes at most 200. Leave 30 out.` A 360 is made from at most 200 photos. Leave photos out with **Leave out of 360** until 200 or fewer are included. See [Leave photos out](#panorama-start-leave-photos-out).
- `The set could not be read.` The reason is shown in red above. Click **Retry**.
- `An import or another stitch is running.` Only one stitch runs at a time, and not while photos are being imported.

While photos are being deleted, **Stitch 360** can still be clicked. The panel then answers `An import, a delete or another stitch is running.`

When you open a photo of another set while a stitch runs, the panel reads `A stitch of another set is running.` with its progress and **Cancel**. Imports and deletes are refused until the stitch is done.

<a id="panorama-stitch-reading-the-result"></a>

### Reading the result

Under `Last stitch` the panel shows three lines and any warnings, for example:

- `41.3 s, match error 0.8 px`: how long the stitch took, and how far apart, on average in pixels, the same points of two overlapping photos still lie after the stitch. A smaller number means the photos fit together better.
- `24 photos matched, 0 unmatched`: a photo is matched when the studio found the same details in it and a neighbouring photo. An unmatched photo is placed by its camera angles alone, so it fits less well.
- `Covers 78.4 % of the sphere`: the share of the sphere that photos cover, before any fill.

| Warning | What it means | What to do |
|---|---|---|
| `3 photo(s) could not be matched to a neighbour and are placed by their recorded camera angles.` | Those photos share too little detail with their neighbours, for example plain sky or water. | Look at the seams around them in the 360. Leave a badly placed photo out and stitch again. |
| `No overlapping photos could be matched: every photo is placed by its recorded camera angles alone.` | No pair of photos could be matched. | Look at the seams in the 360. Switch on **Photo outlines** to see where each photo lies. |
| `2 photo(s) cannot be used.` | Photos of the table above were not used. | See the table above. |

The same warnings are listed under the 360 when you open it.

<a id="panorama-stitch-example-a-360-over-a-farm"></a>

### Example: a 360 over a farm

You stitch the 26 photos of a hover at 60 m, taken with a 24 mm-equivalent camera at 4000 × 3000 pixels. You left out one photo.

1. The panel reads `1 photo left out by you.` and `25 photos`. The coverage map shows the three rows and the straight-down photos, with a gap at the top.
2. **Output size** offers all four sizes, up to `16384 × 8192`. You keep `8192 × 4096`.
3. You keep **Fill uncovered sky** ticked and click **Stitch 360**.
4. The bar runs through `Reading photos`, `Matching overlaps`, `Solving camera angles`, `Blending`, `Filling gaps` and `Saving`.
5. The line reads `360 ready: 360_20261003-142201.jpg` and the 360 opens.

<a id="panorama-stitch-tips-and-common-mistakes"></a>

### Tips and common mistakes

- The sky above the top row of photos is not a photograph. With **Fill uncovered sky** it is a smooth extension of the colours nearby.
- Seams can show where the drone drifted between photos, most of all on objects close to the drone. Moving objects (cars, people, animals, clouds) and plain areas such as water or clear sky can also show seams.
- A bigger **Output size** needs more memory. If the stitch stops with `There is not enough memory for a canvas this wide; choose a smaller size.`, pick a smaller size.
- Do not switch to another profile while a stitch runs. The stitch then ends with `Nothing was stored: the profile was switched while the 360 was stitched.`
- You can switch to another tab while a stitch runs; it goes on.

> **Under the hood**
>
> The studio starts from each photo's recorded gimbal angles, finds the same details in overlapping photos, and then adjusts every photo's direction, the focal length and the lens distortion so that matching points meet. The match error is the root mean square of what remains, in photo pixels. Photos are blended across their overlaps so that brightness steps fade out. The sizes offered depend on the focal length: a size is offered when its width is at most 1.1 times the photos' resolution all the way around (4096 is always offered). A 360 is made from 2 to 200 photos of one size and one focal length (within 1 %).

<a id="panorama-stitch-see-also"></a>

### See also

- [360 Panorama Studio: getting started, importing, sets and marking up photos](#panorama-start)
- [Looking around a 360, the starting view and the exports](#panorama-export)

<sub>[Back to contents](#contents)</sub>

<a id="panorama-export"></a>

## Looking around a 360, the starting view and the exports


A finished 360 opens in a viewer in the middle of the 360 Pano tab. You look around it, show or hide the mark-ups and the outlines of its photos, and choose the view it opens at. You can save it as a 360 JPEG, as an HTML viewer file that opens in any web browser, or save one view as a picture in the Photogrammetry library.

<a id="panorama-export-before-you-start"></a>

### Before you start

- A set is stitched. See [Stitching a 360](#panorama-stitch).
- Open the 360: click it in the `360s (N)` tab of the library, or under `360s of this set` in the Stitch panel. The viewer reads `Loading the 360…` for a moment.

<a id="panorama-export-steps"></a>

### Steps

1. Drag in the picture to look around: left and right, up and down.
2. Turn the mouse wheel to zoom in or out. On a touch screen, pinch.
3. Or click the picture once and use the arrow keys.
4. Double-click, or click **Reset view**, to go back to the view the 360 opens at.
5. Press **Mark-ups** to show or hide the mark-ups of the photos. They are shown at first.
6. Press **Photo outlines** to show or hide the border of each photo. They are hidden at first.
7. Read the line under the picture, for example `8192 × 4096 · 25 photos · coverage 78 % · match error 0.80 px`, and the warnings of the stitch under it.

The mark-ups come from the photos as they are now. When you change a mark-up on a photo, the 360 shows the change; you do not stitch again. When a photo of the 360 is deleted, its mark-ups and its outline disappear from the 360. If the mark-ups of a photo cannot be read, a line reads `Mark-ups of 1 photo(s) could not be read.`

If the computer cannot show the 360 view, the viewer reads `This view needs WebGL2, which is not available here; the flat picture is shown instead.` **Set starting view** is not offered then.

<a id="panorama-export-the-starting-view"></a>

### The starting view

A 360 opens facing the centre of the picture, level, at a medium zoom. The centre is the direction the first usable photo of the set faced. You can choose another starting view.

1. Turn and zoom the view until it shows what a viewer should see first.
2. Click **Set starting view**. The line `Starting view saved.` appears.
3. From now on the 360 opens at this view, and **Reset view** and a double-click go back to it.
4. To go back to the centre, click **Clear starting view** (it is there only while a starting view is set). The line reads `Starting view cleared.`

This program's viewer and the HTML viewer file always start at the starting view, with its zoom. The exported 360 JPEG carries the direction of the starting view, in whole degrees, but not the zoom. Whether another program opens the JPEG at that direction is that program's choice.

<a id="panorama-export-export-a-360-jpeg"></a>

### Export a 360 JPEG

1. Click **Export 360 JPEG…**. A window headed `Export 360 JPEG` names the 360 and its size.
2. Tick **Include mark-ups** to draw the mark-ups into the picture. Untick it for the clean picture. When the photos have no mark-ups, the box is greyed out and the window reads `There are no mark-ups on the source photos.`
3. Tick **Include location** to write the 360's position into the file (see below). The box is ticked at first, and it is shown only when the 360 has a valid position.
4. Click **Export…** and choose the folder and the name. The name ends in `.jpg`.
5. Wait while the button reads `Exporting…`. A line at the top reads `360 exported:` and the path.

The file is the full-size 360 as one 2:1 picture. It carries the information that tells 360-photo viewers to show it as a 360.

With **Include location**, the file carries the latitude and the longitude of the 360 and the compass direction of the centre of the picture, as a drone photo carries them. The position is the one of the first usable photo of the set. No height is written. The 360 in the library is not changed; only the exported file carries the location. The HTML viewer file and the saved view never carry a location.

<a id="panorama-export-export-an-html-viewer-file"></a>

### Export an HTML viewer file

1. Click **Export HTML viewer…**. A window headed `Export HTML viewer` opens.
2. Tick or untick **Include mark-ups** and **Include photo outlines**.
3. Type a **Title** for the page, up to 120 characters. It starts as the 360's name.
4. Tick **Rotate slowly** if the page should turn the view by itself.
5. Click **Export…** and choose the folder and the name. The name ends in `.html`. A line at the top reads `HTML viewer exported:` and the path.

The file is one web page with the 360 inside it. Send it or copy it; it opens in a web browser without an internet connection. The page shows:

- the title at the top;
- two switches, **Mark-ups** and **Photo outlines**. A switch is greyed out when the file holds none: without **Include photo outlines**, **Photo outlines** is greyed out. With it, the outlines are in the file and start hidden; the visitor switches them on;
- a **Full screen** button, where the browser offers full screen (it then reads `Exit full screen`);
- the 360, which opens at the starting view and is moved like the viewer in the program;
- a line at the bottom: `Generated by`, your company name from the branding settings, and `· 360 Panorama Studio`. Without a company name it names Airwulf, LLC. See [Branding your reports](#settings-branding).

A browser without WebGL2 shows the flat picture with a line that says so, and no switches.

With **Rotate slowly** the view turns by itself while nobody touches it. A drag, a click, the wheel, a key or a touch stops it, and it starts again 8 seconds after the last one. A visitor whose computer or phone is set to reduce motion sees no rotation.

<a id="panorama-export-save-a-view-to-the-photogrammetry-library"></a>

### Save a view to the Photogrammetry library

**Save view to Photogrammetry** is there only while the Photogrammetry add-on is installed, switched on and licensed.

1. Turn the view to what you want to keep, with the mark-ups and outlines you want switched on.
2. Click **Save view to Photogrammetry**. The view is saved as a flat 2400 × 1600 picture.
3. A line reads, for example, `View saved to the Photogrammetry library: 360_20261003-142201_view_1.jpg`. The picture is in the Photogrammetry tab, where you can annotate it and add it to a report.

Each saved view gets the next free number: `_view_1`, `_view_2` and so on. If the Photogrammetry library is busy, the line reads `The Photogrammetry library is busy; try again.` If the same view was saved before, it reads `This view is already in the Photogrammetry library.` and nothing new is saved.

<a id="panorama-export-example-sending-a-360-of-a-farm-to-a-client"></a>

### Example: sending a 360 of a farm to a client

1. Open `360_20261003-142201.jpg` and turn the view to the barn. Click **Set starting view**.
2. Click **Export HTML viewer…**, type the title `North barn, 3 Oct 2026`, tick **Rotate slowly** and click **Export…**. Save it as `North barn.html`.
3. Click **Export 360 JPEG…**, keep **Include mark-ups** and **Include location** ticked, and click **Export…**.
4. With the Photogrammetry add-on, click **Save view to Photogrammetry** to keep the barn view for a survey report.

The client opens `North barn.html` in a browser. The page starts at the barn and turns slowly until they drag the view.

<a id="panorama-export-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Set the starting view before you export. A file exported earlier keeps the view it was exported with.
- If a mark-up is missing from the export, check that its photo is still in the library: a deleted photo takes its mark-ups with it.
- When the mark-ups of a photo could not be read, **Include mark-ups** is greyed out and the window reads `Mark-ups of 1 photo could not be read: export without them, or close and try again.`
- Mark-ups you changed a moment ago may not be saved yet. The window then reads `Mark-ups of 1 photo are not saved yet; they are exported as they stand.`
- If the export window reads `A file with this name exists; choose another name.`, export again with another name.
- A saved view has the sharpness of the viewer, not of the full-size 360.
- A 360 that shows `This 360's record cannot be read by this version.` has no viewer and no exports. You can still rename or delete it.

> **Under the hood**
>
> The viewer shows a copy of the 360 at most 8192 pixels wide; the 360 JPEG export is the stored full-size picture. With mark-ups, each photo's mark-ups are drawn on that photo first and then laid over the 360 the way the photo itself was, so they sit exactly where they were drawn. The HTML viewer file holds the 360 copy, the mark-ups and the viewer in one page that loads nothing from the internet. The starting view is stored as a turn from the picture's centre, a tilt and a zoom; the JPEG gets the turn as a compass heading and the tilt, both rounded to whole degrees.

<a id="panorama-export-see-also"></a>

### See also

- [Stitching a 360: the Stitch panel, camera angles, size, warnings](#panorama-stitch)
- [360 Panorama Studio: getting started, importing, sets and marking up photos](#panorama-start)
- [Branding your reports: logo, company and Part 107 number](#settings-branding)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)

<sub>[Back to contents](#contents)</sub>


---

# Pictures: annotating and measuring

<a id="annotate"></a>

## Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames


The viewer in the Thermal Studio and in the Photogrammetry tab shows the picture you select in the library, with a toolbar above it. You can zoom and pan, mark up the picture with arrows, shapes and text, write a note for the report, and turn a video frame into a picture you can measure. Everything you draw is saved with the picture and drawn into the report figures.

<a id="annotate-before-you-start"></a>

### Before you start

- The Thermal, Photogrammetry or 360 Panorama Studio add-on is installed, and its tab is open (the 360 studio's tab is **360 Pano**). The 360 studio offers only the drawing tools, colours, **┄ Dashed**, **↩ Undo** and **✕ Clear**: no measuring tools and no **📝 Note**. See [360 Panorama Studio](#panorama-start-mark-up-a-photo).
- At least one photo, radiometric picture, orthomosaic or video is in the library. See [Thermal Studio: getting started](#thermal-start) or [Photogrammetry: getting started](#photo-start).
- Click the picture in the library. The toolbar, the viewer and an info strip appear.

<a id="annotate-zoom-and-pan"></a>

### Zoom and pan

1. Turn the mouse wheel over the picture. It zooms in or out about the cursor, whatever tool is active, up to 10×.
2. Use the strip in the top-left corner of the picture: **−** zooms out, **+** zooms in, the percentage (for example `250%`) fits the picture to the window, and **Fit** does the same (it is greyed out at 100 %).
3. Once you are zoomed in, drag with the right or the middle mouse button to pan. This works with every tool, so you can keep drawing.
4. Or pick **🔍 Zoom**: a click zooms in, Shift+click zooms out (the cursor changes while you hold Shift), and a left drag pans.
5. Read the bottom-left corner while you move the mouse. On a radiometric picture, or one with a position source, it shows the pixel with its temperature and/or position (latitude and longitude, or grid easting and northing). Other pictures show no readout.

In the Thermal Studio, on a radiometric picture, a red **+** marks the hottest pixel and a blue **+** the coldest, each with its temperature. Boxes from the anomaly detection are drawn dashed, orange for hot and cyan for cold.

<a id="annotate-draw-annotations"></a>

### Draw annotations

1. Pick a tool in the toolbar:
   - **↖ Select** moves an annotation; Delete or Backspace removes the selected one.
   - **→ Arrow**, **╲ Line**, **◯ Circle** (an ellipse) and **▭ Box** (a rectangle): drag from start to end.
   - **〰 Curve**: drag from start to end, then drag the round handle at the middle to bend it. The new curve stays selected, so you can bend it straight away, or later with **↖ Select**.
   - **✎ Draw**: freehand.
   - **T Text**: click, type the label in the box (`Type, then Enter`), press Enter.
   - **⌫ Erase**: drag over annotations. Shapes and labels under the eraser are removed whole; freehand strokes are cut where it passes.
2. Pick a colour from the swatches next to the tools before you draw. The rainbow swatch (tooltip **Custom color…**) opens the system colour dialog; colours you pick there are kept as extra swatches.
3. Press **┄ Dashed** to make new lines, arrows, curves and freehand strokes dashed. Press it again to go back to solid strokes. Colour and dash apply to what you draw next, not to what is already there.
4. Press **↩ Undo** to take back the last annotation, or **✕ Clear** to remove them all (the app asks first).

In the Thermal Studio the toolbar also has **⬤ Node** and **⌁ Link**, which build a heat-flow network on the picture. The eraser removes nodes and links too. See [Heat flow network: nodes, conductors, solving](#thermal-network).

In the Thermal Studio the **Measure** group ends with **🌡 Spot** and **± ΔT**, after **🧭 Scale**:

1. Pick **🌡 Spot** and click a point. A label such as `S1 34.2 °C` appears at the point.
2. Pick **± ΔT** and click two points, or drag from one to the other. The label, such as `ΔT1 +6.2 °C`, is the second point's temperature minus the first's, so dragging the other way reads `ΔT1 -6.2 °C`.
3. Read them in the **Spot readings** section of the **Analysis** panel, one line each with the pixel coordinates: `S1 34.2 °C · (12, 48)` and `ΔT1 +6.2 °C · (12, 48) → (40, 51)`.

Spots are numbered S1, S2… and differences ΔT1, ΔT2… in the order you placed them, so removing S1 makes the next spot S1. The values are in your temperature unit (index values on a vegetation index), follow the picture's measurement parameters, and read "…" while the temperatures load. Both are annotations: **↖ Select** moves them and **⌫ Erase** removes them. The two tools are greyed out until a still picture with temperatures (or a vegetation index) has loaded. See [Spot readings](#thermal-deliverables-spot-readings).

The tools in the **Measure** group, from **📐 Reference** to **⟋ Slope**, and the **🧭 Scale** button are covered in [Giving a picture a scale](#measure-scale) and [Measuring lengths, angles and areas](#measure-tools).

<a id="annotate-write-a-note"></a>

### Write a note

1. Press **📝 Note**. A text box opens under the toolbar.
2. Type what you saw, for example the condition, the context and the follow-up. The placeholder reads `Observed condition, context, measurements, follow-up…`.
3. Close it with **📝 Note** again. The button shows a dot (**📝 Note ●**) while the picture has a note.

The note is printed under the picture's figure in the report.

<a id="annotate-keyboard-shortcuts"></a>

### Keyboard shortcuts

The keys work when the cursor is not in a text box.

| Key | What it does |
|---|---|
| Esc | Deselects, and drops a line or outline you have started but not finished |
| Delete or Backspace | Removes the selected annotation (in the Thermal Studio also a selected node or link) |
| Enter | Finishes a polygon area while you draw it |
| Backspace while drawing a polygon | Removes its last corner |
| Shift with **🔍 Zoom** | Click zooms out instead of in |
| Shift with **⬤ Node** | Starts a new chain instead of linking to the last node |

<a id="annotate-videos"></a>

### Videos

1. Click a video in the library. It plays in the viewer with the player's own controls. With **↖ Select**, clicks on empty parts of the picture reach the controls.
2. Pause at the moment you want.
3. Press **Capture frame** (top right of the video). The frame is saved as a new picture in the library, which you can annotate and measure like any other.
4. In the Photogrammetry tab you can also press **+ Add frame m:ss.s to report** (the button shows the current time, for example `+ Add frame 1:23.0 to report`). The frame at that moment is queued as a figure without making a new picture.

The measurement tools are greyed out on a video, because annotations belong to the whole file, not to one frame. Capture the frame first.

<a id="annotate-example-marking-a-damaged-roof-edge"></a>

### Example: marking a damaged roof edge

You inspect a warehouse roof from a DJI photo in the Photogrammetry tab.

1. Click the photo, turn the wheel to zoom to about `300%` on the gutter, and right-drag until the damaged section is centred.
2. Pick red and draw a **▭ Box** around the sagging gutter.
3. Press **┄ Dashed**, pick yellow and draw a **→ Arrow** pointing to a missing fastener.
4. Pick **T Text**, click beside the arrow, type `missing fastener` and press Enter.
5. Press **📝 Note** and type `Gutter sag over about 3 bays; fasteners missing at the second bracket. Re-fix before winter.`
6. Press **Fit** to see the whole picture again. The toolbar now reads `3 annotations · saved with the image and drawn into the report`.

When you add the photo to the report, the figure shows the box, the arrow and the label, with the note under it.

<a id="annotate-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Annotations are drawn in picture pixels, not screen pixels. Zoom in before you place small marks: they stay where you put them at every zoom and in the export.
- Colour and **┄ Dashed** change only new strokes. To change an existing one, undo it and draw it again.
- **✕ Clear** removes every annotation on the picture, measurements included. **↩ Undo** is safer when you only want the last one gone.
- Nothing can be measured on a video. Use **Capture frame**, then measure the new picture.
- A note is per picture, not per figure. A video queued at several frames, or a picture used in several thermal imaging pairs, carries the same note under every figure.

> **Under the hood**
>
> Annotations are kept per picture in the profile database, in the picture's own pixel coordinates, and drawn as an overlay. That is why they line up at any zoom (1× to 10×) and are baked into report exports exactly as you see them, and carried as data in inspection bundles. The dashed setting is stored with each annotation. A captured frame becomes a PNG named after the video with `_frame_` and a number (in the Photogrammetry tab, the frame's time); a DJI thermal video frame carries no temperatures. The picture's scale settings are kept among the annotations too, but **↩ Undo** and **✕ Clear** leave them alone.

<a id="annotate-see-also"></a>

### See also

- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)
- [Heat flow network: nodes, conductors, solving](#thermal-network)
- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Photogrammetry survey reports](#photo-report) and [Thermal inspection reports](#thermal-report)
- [Side-by-side documents and temperature exports](#thermal-deliverables)

<sub>[Back to contents](#contents)</sub>

<a id="measure-scale"></a>

## Giving a picture a scale: references, altitude and pitch, the Scale window, units


A measurement is only as good as the picture's scale: how much ground one pixel covers. This topic shows where the app finds a scale, how to give a picture one with a reference of known length, how to correct the altitude and pitch, and how to read the **🧭 Scale** window that lists every source and its limits.

<a id="measure-scale-before-you-start"></a>

### Before you start

- A still picture is selected in the Thermal Studio or the Photogrammetry tab (for a video, capture a frame first: see [Viewing and annotating pictures](#annotate)).
- For a reference: something in the picture whose real length you know, such as a door, a parking bay, a roof panel or a tape laid on the ground.
- For a camera scale: a drone photo whose file records the 35 mm equivalent focal length and the altitude (most DJI photos do).

<a id="measure-scale-where-the-scale-comes-from"></a>

### Where the scale comes from

The app uses the first source that applies:

1. An orthomosaic's georeferencing: a Metashape GeoTIFF knows its pixel size. References drawn on it only cross-check it.
2. References and ground control points: lines over things of known length, or two GCPs with coordinates. With the focal length known they fix the camera's height above the surface, so the camera's tilt is accounted for across the picture; without it they give one flat scale.
3. The camera's altitude and lens: the focal length, the altitude above the surface and the pitch from the file. The window calls this metadata only.
4. No scale: measurements read `no scale`, and the window says what is missing.

GCPs are covered in [Positions, ground control points and georeferenced orthomosaics](#measure-geo).

<a id="measure-scale-steps"></a>

### Steps

1. Press **📐 Reference** in the toolbar's **Measure** group.
2. Zoom in, then click both ends of the object of known length, or drag between them. A box opens at the middle of the line, with the placeholder `length, e.g. 2.5 m, 250 cm, 8 ft 2 in [± 0.02]` (imperial: `length, e.g. 8 ft 2 in, 8.5 ft, 250 cm [± 1 in]`).
3. Type the length and press Enter: `2.5 m`, `250 cm` or `8 ft 2 in`. A bare number is metres, or feet under imperial units. Add a tolerance after `±`: `2.5 ± 0.02` (a bare tolerance takes the length's unit). The tool switches to **📏 Measure**.
4. If the box shows `Not understood. …`, correct the text and press Enter. Esc, or an empty box, discards the reference.
5. Press **🧭 Scale**. A window opens over the picture, near its top-left corner, a little below the zoom buttons. Drag it by its title bar, resize it at its bottom-right corner, and close it with its **✕** or the toolbar button. Once you have moved or resized it, it opens at that place and size again, in both studios; a window you never moved opens at that default place each time. While the focus is in a window, the picture's keyboard shortcuts do nothing; click the picture to get them back.
6. Read the **Scale** line: where the scale comes from, for example `1 reference + camera geometry (focal 3000 px, pitch −45.0°): 42.43 m ± 0.30 m above the reference plane`. Warnings follow in red (error), amber (caution) or blue (note).
7. Read **Ground sample distance at the centre**, for example `2.00 × 2.83 cm/px (across × along)` on a tilted picture, and **Camera focal length**.
8. If the file's altitude is wrong for this surface, type the camera's height above it in **Altitude above the surface (m)**, and its uncertainty after **±**. The note says `used only without references`: a reference always wins.
9. If the pitch is missing or wrong, type it in **Pitch (°)**: `−90` is straight down. A blank box uses the flight data in the file.
10. Check the **References** list: a name box (placeholder `Reference 1`), the length, `tolerance not given (exact)` when you typed none, the length in pixels and, with two or more, the deviation from the fit (for example `+1.7 % from the fit`). **✕** removes one.
11. Read the footer: what no ± includes (lens distortion, ground slope and relief, camera roll, pitch error for positions, DEM correlation and interpolation across ridges).

With a single reference the window adds `Single sample, no cross-check: a second reference or two GCPs would show how well they agree.`

<a id="measure-scale-example-a-tilted-inspection-photo"></a>

### Example: a tilted inspection photo

A 4000 × 3000 px photo is taken at −45° pitch, focal length 3000 px, 50 m above the yard by the file (the scale specification's vectors).

1. From the camera data the window reads `Camera metadata (…): focal 3000 px, pitch −45.0°, 50.0 m ± 1.0 m above the surface`, with the note `Scale from the camera metadata only (focal length and altitude); add a reference to check it.` The ground sample distance is `2.36 × 3.33 cm/px (across × along)`: 50 m ÷ (3000 px × sin 45°) = 2.36 cm across, 50 m ÷ (3000 px × sin² 45°) = 3.33 cm along.
2. You draw a **📐 Reference** 200 px long over a 3 m trailer bed near the bottom of the picture and type `3 m`.
3. The scale line becomes `1 reference + camera geometry (focal 3000 px, pitch −45.0°): 42.43 m ± 0.30 m above the reference plane`. A blue note says the references put the camera at 42.4 m, the flight data at 50.0 m. DJI's altitude counts from the take-off point: if the reference is right, the yard lies about 7.6 m above the take-off point.
4. A 200 px **📏 Measure** line near the top now reads `6.00 m ± 0.06 m`, with a note that it is far from the references: on a tilted picture the far ground looks smaller.

<a id="measure-scale-settings-units"></a>

### Settings → Units

In Settings, open **Units**. Pick **All Metric** or **All Imperial**, or set **Distance** and **Altitude** separately.

- Lengths, areas, volumes and material quantities follow **Distance**: m, m², m³ or ft, ft², yd³. Areas switch to ha or ac from one hectare or one acre; imperial volumes read ft³ below one cubic yard.
- Heights, elevations, the camera altitude and the elevation model's accuracy follow **Altitude**.
- Typed values are read in the unit shown; you can always write `m`, `cm`, `ft` or `in` after a number.

Values are stored in metres.

<a id="measure-scale-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Draw the reference across the area you will measure, not along the picture's edge. On a tilted picture the scale changes from bottom to top, and a line far from every reference gets the note `This line is far from the references; the scale may differ there (slope, relief, lens distortion).`
- The altitude is the camera's height above the surface you measure. DJI's relative altitude is barometric and counts from take-off: on a roof 8 m above the launch point, subtract 8 m, or better, draw a reference.
- Keep references longer than 20 px; a shorter one brings a warning.
- One reference has no cross-check. A mistyped length, or a reference not flat on the surface, goes unnoticed until you add a second.
- When references disagree beyond their tolerances, a warning says so and the ± widens. Check the lengths and that both lie on the same flat surface.
- After switching units, a bare number is read in the new unit. Write the unit to be sure.

> **Under the hood**
>
> Every scale has one parameter: the camera height H above the reference plane (perspective), metres per pixel (no focal length), or the GeoTIFF's pixel size per axis. The focal length in pixels comes from the 35 mm equivalent focal length, else (FLIR) the field of view, multiplied by the digital zoom when one is recorded; the EXIF focal length in millimetres is not used. Straight down, the ground sample distance is altitude ÷ focal length in pixels: 60 m ÷ 3000 px = 2.0 cm/px.
>
> Each reference gives an estimate of H; several combine by weighted least squares, and the ± is the larger of the propagated value and the samples' scatter (the Birge rule). A set of n GCPs counts as n − 1 independent baselines.
>
> Each ± is one standard uncertainty (about 68 %), combining the marking (±1 px per coordinate), the scale (reference tolerances, GCP accuracies, or the altitude's ±, 1.0 m by default) and the focal length when known. Not included: lens distortion (1–3 % at the corners), ground slope and relief, camera roll, pitch error.

<a id="measure-scale-see-also"></a>

### See also

- [Measuring lengths, angles and areas](#measure-tools)
- [Positions, ground control points and georeferenced orthomosaics](#measure-geo)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Viewing and annotating pictures](#annotate)
- [Thermal Studio: getting started](#thermal-start) and [Photogrammetry: getting started](#photo-start)

<sub>[Back to contents](#contents)</sub>

<a id="measure-tools"></a>

## Measuring lengths, angles and areas


Once a picture has a scale, three tools measure on it: **📏 Measure** for distances, **∠ Angle** for angles and roof pitches, and **⬠ Area** for plan areas and perimeters. Each value is labelled with its uncertainty, listed in the **🧭 Scale** window and copied into the report in one click.

<a id="measure-tools-before-you-start"></a>

### Before you start

- A still picture is selected (the tools are greyed out on a video).
- The picture has a scale: an orthomosaic, a reference or two GCPs, or the camera's focal length and altitude. Without one, labels read `no scale` (**∠ Angle** works without a scale). See [Giving a picture a scale](#measure-scale).
- Zoom in to place each click exactly: the ± assumes each click is within one picture pixel, so a feature spanning more pixels gets a smaller ±.

<a id="measure-tools-measure"></a>

### Measure

1. Press **📏 Measure** in the **Measure** group.
2. Click the start and the end, or drag between them.
3. Read the label: the tag and the value with its ±, for example `M1: 10.00 m ± 0.06 m`.

<a id="measure-tools-angle"></a>

### Angle

1. Press **∠ Angle**.
2. Click the end of the first ray, then the vertex, then the end of the second ray.
3. Read the label: the angle as drawn in the picture, for example `∠1: 153.4°`.
4. For a roof pitch, draw one ray along a level eave (within 5° of the picture's horizontal) and the other along the rafter. The **🧭 Scale** window adds, for example, `roof pitch 6.0:12 ± 0.1`.

<a id="measure-tools-area"></a>

### Area

1. Press **⬠ Area**. Three icons appear after it: polygon (⬠), rectangle (▭) and circle (◯). Pick one.
2. Draw the outline:
   - Polygon: click each corner; finish on the first corner, with a double-click or with Enter. Backspace removes the last corner.
   - Rectangle: click two opposite corners, or drag. Its sides run along the picture's edges.
   - Circle: click the centre, then a point on the rim, or drag from the centre.
3. Read the label: the plan area with its ±, for example `A1: 4.00 m² ± 0.05 m²`. From one hectare (or one acre) it reads in ha or ac.

<a id="measure-tools-the-scale-window-rows"></a>

### The Scale window rows

Press **🧭 Scale**: a window opens over the picture (see [Giving a picture a scale](#measure-scale-steps)). While you hold the mouse button down on the picture (a drag or a pan), the windows let the pointer through, so a line or an outline can end under a window. A click, such as a polygon corner or a two-click measure, lands on the window: move the window first. Each tool has its list: **Measurements** (M1, M2…), **Angles** (∠1…) and **Areas** (A1…).

- Name: type one in the row's first box (placeholder `name`). It replaces the tag on the picture (`ridge: 10.00 m ± 0.06 m`); in the report the tag stays and the name is added, for example `M1 10.00 m ± 0.06 m (ridge)`.
- Value: a length with ± (or `no scale`, or `n/a`), an angle `in the picture`, or an area with `perimeter …` and, for those shapes, `rectangle 14.00 m × 10.00 m` or `circle, diameter 48.00 m ± 0.28 m` (on a camera picture `rectangle in the picture (a trapezoid on the ground)` or `circle in the picture (an oval on the ground)`).
- **height above the reference plane (m)**: type how far a feature lies above the surface the scale was set on (negative below). It needs a camera picture with a focal length; on an orthomosaic a note says it is ignored, and on a flat scale an amber notice reads `A height above the reference plane needs the camera focal length; it is not used.`
- **⇉ others…** after the height (shown when the picture has another area) copies it to other areas; **Cancel** closes the panel without copying: tick them (**All**, **None**) and click **Apply**. A line reads, for example, `Height applied: changed A2 and A3; A4 already had it.` and the focus goes back to **⇉ others…**. When nothing changes, nothing is saved and the line says so, for example `Height applied: A2 and A3 already had it.` The button is off while the area has no height: there is nothing to copy. There is no undo, so check the ticks first.
- Detail lines: the ± broken down, for example `± 0.062 m = marking 0.007 m · scale 0.061 m` (plus `focal …` when known). An angle adds the angle `on the ground` and the roof pitch; a measurement adds its bearing and height difference when a position source or elevation model gives them.
- **✕** removes the row and its drawing.

Below the areas a note reads `Plan area on the reference plane. …` An area is always seen from straight above; materials with a roof pitch multiply it by √(1 + (x/12)²) in the **🧮 Material Takeoff** window (see [Material take-offs](#materials-takeoff)). Volumes are covered in [Elevation models](#measure-elevation).

Under the note the picture total adds up the areas that have a value, for example `Picture total: 1 area 4.00 m² ± 0.05 m²`. Solids and elevation-model volumes follow as groups of their own, and `(1 without a value)` or `(1 still being read)` says what is not yet in the sum. Areas that overlap are counted twice. The same line shows under the picture and in the **🧮 Material Takeoff** window, and it changes when you finish an area. Under the picture it appears when the first area gets a value, so the picture shifts by one line (and back when the last one goes).

<a id="measure-tools-example-a-flat-roof-survey-picture"></a>

### Example: a flat-roof survey picture

A picture looking straight down on a flat roof, with no focal length in its file, has one reference typed as `2 m ± 0.01`: a roof hatch 400 px long. The scale line reads `1 reference: 0.00500 m/px (flat picture, no camera geometry)`.

1. **📏 Measure** across a parapet, 2000 px long: `M1: 10.00 m ± 0.06 m` (imperial `32 ft 10 in ± 2 in`), detail `± 0.062 m = marking 0.007 m · scale 0.061 m`: the reference's own ±, scaled up five times with the length.
2. **⬠ Area**, polygon, around a skylight curb of 400 × 400 px: `A1: 4.00 m² ± 0.05 m²` (`43.1 ft² ± 0.5 ft²`), perimeter `8.00 m ± 0.05 m`.
3. On a second photo, square-on to the gable end of the stair housing, **∠ Angle** with one ray along the eave reads `∠1: 153.4°`, and the window `roof pitch 6.0:12 ± 0.1`: the acute angle is 180° − 153.4° = 26.6°, and 12 × tan 26.6° = 6.0.

<a id="measure-tools-in-the-report"></a>

### In the report

The Photogrammetry report builder copies what you drew into its **Advanced Analysis & Measurements** section. The Thermal report prints, under each imaging pair, one measurements line per picture of the pair. With two or more areas that have a value the line adds their sum, for example `total area 1000 m² ± 9 m² (2 areas)`, or `(2 of 3 areas)` when one has none; perimeters are in it only with **Include perimeters** ticked in section 5.

1. Queue the pictures as figures in the Photogrammetry tab (**+ Add to report**).
2. Open **📄 Report ▼** → **Open report builder…** and go to **Advanced Analysis & Measurements**.
3. Press **📏 Add measurements from pictures**. One row appears per distance, angle, area, position and slope on the queued pictures, plus height-difference and elevation rows when an elevation model is paired, and a volume row per solid or cut, fill and net rows per elevation-model volume. Tick **Include perimeters** first to get a row for each area's perimeter too; the box is off by default, also in reports made before this version.
4. Check each row:
   - **Type**: `Length / distance`, `Area`, `Angle`, `Volume`, `Slope / pitch`, `Position`, `Height / elevation` or `Other`.
   - **Feature**: your name, or `Measurement 1`, `Area 1`…; with **Include perimeters** ticked, a perimeter has its own row, such as `Area 1 perimeter`. Perimeter rows already in the table stay when you clear the box: remove them with **✕**.
   - **Value** and **Unit**: in Settings → Units, rounded to two decimals.
   - **Method / tolerance / remarks**: most rows start with `In-image:` (a position row starts with the position itself), name the scale source and end with the ±, for example `± 0.062 m (1 sigma)`.
   - **Shown in figure**: the figure it is drawn on.
5. Read the notice: how many rows were added and what was skipped, for example `2 measurement(s) have no scale yet and were skipped.` Rows already there (same figure, type and feature) are not added again: press the button after adding measurements; to refresh a changed value, delete its row first.
6. Read the line above the table, for example `Total area 1000 m² over 2 area rows`. It adds the **Area** rows that have a value and an area unit, converted to your units and added up before the sum is rounded once; others are counted as `1 area row without a value or an area unit (not in the total)`. Overlapping areas are counted twice. The export prints it as `Total area` under the table.
7. Rows made under the other unit system show **Convert rows to ft** (or **Convert rows to m**). It converts the value, the unit and the ± in the method text.
8. **+ Add measurement** adds a row by hand, for a tape measurement on site.

<a id="measure-tools-tips-and-common-mistakes"></a>

### Tips and common mistakes

- An area is a plan area. A pitched roof's surface is larger by √(1 + (x/12)²), the same as 1 ÷ cos(pitch): a 6:12 roof is 1.118 × its plan area. Material take-offs apply it for you.
- The pitch from **∠ Angle** is true only when the camera faces the gable end square-on. Seen at an angle it reads too steep or too flat; a slope on an elevation model is better.
- A polygon whose edges cross is flagged: redraw it.
- Measure on the surface the scale was set on, or type the height above it: a ridge measured with a ground reference reads too long.

> **Under the hood**
>
> A length is the scale parameter times the unit ground distance between the ends. An area projects every corner the same way and uses the shoelace formula. The ± is one standard uncertainty combining the marking (±1 px per coordinate, by numerical partial derivatives), the scale (twice its relative σ for an area) and the focal length when its uncertainty is known. A rectangle or circle takes its marking from its two clicks; a circle is stored as a 256-corner polygon.
>
> A picture total's ± combines the areas' marking parts by root-sum-square (each click is independent) and adds their scale parts and their focal parts (one scale for the whole picture). The focal part's sum is an upper bound, so the total's ± can be a little too large. When an area's ± is unknown, the total reads `≈`.
>
> The picture angle uses the six click coordinates only; the ground angle is scale-free. The roof pitch is x = 12 × tan β, β being the acute angle between the rays. Not included: lens distortion, ground slope and relief, camera roll, a consistent click bias.

<a id="measure-tools-see-also"></a>

### See also

- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Positions, ground control points and georeferenced orthomosaics](#measure-geo)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Photogrammetry survey reports](#photo-report) and [Thermal inspection reports](#thermal-report)
- [Photogrammetry: getting started](#photo-start) and [Thermal Studio: getting started](#thermal-start)

<sub>[Back to contents](#contents)</sub>

<a id="measure-geo"></a>

## Positions, ground control points and georeferenced orthomosaics


The **⌖ Position** tool reads the latitude and longitude (or easting and northing) of any point you click, with its ±. It comes from a georeferenced Metashape orthomosaic, from ground control points (GCPs) you type in, or from the drone's GPS and camera heading. GCPs also give a picture its scale.

<a id="measure-geo-before-you-start"></a>

### Before you start

- A still picture is selected in the Thermal Studio or the Photogrammetry tab.
- One of these sources:
  - a Metashape orthomosaic GeoTIFF in WGS 84 / UTM or in latitude/longitude (other projected systems give easting/northing only);
  - two or more GCPs with coordinates of one kind (all latitude/longitude, or all easting/northing);
  - a drone photo with a GPS position and a heading in its file, plus a camera scale (see [Giving a picture a scale](#measure-scale)).
- For GCPs: surveyed coordinates of visible points (painted targets, manhole covers).

<a id="measure-geo-gcp"></a>

### GCP

1. Press **🎯 GCP** in the toolbar's **Measure** group.
2. Zoom in and click the centre of the target. A box opens with the placeholder `name  ·  name, lat, lon  ·  name, E, N  [± 0.05]`.
3. Type one of these and press Enter:
   - a name alone, `GCP3`, to type the position later;
   - `name, lat, lon`, for example `A, 41.1103, -85.211`;
   - `name, E, N` in metres as surveyed, for example `G2, 10, 0`. Write `E 10, N 0` (or `lat 41.1, lon -85.2`) when small numbers could be read either way. Under imperial units, add `ft` or `usft` to both coordinates when they are in feet.
4. Add the accuracy after `±` when it is not survey grade: `A, 41.1103, -85.211 ± 4` for a phone GPS. A bare accuracy is metres (feet under imperial units). Without one the GCP counts as ±0.05 m.
5. If the box shows `Not understood. …`, correct the text and press Enter.
6. Repeat for every GCP. Two of the same kind give the picture a scale and a position source.

<a id="measure-geo-position"></a>

### Position

1. Press **⌖ Position**.
2. Click the point. The label reads, for example, `P1: 41.110246, −85.211000`, or `P1: no position` when no source applies.
3. Press **🧭 Scale** and read the **Positions** list: the tag, a name box, the position in decimal degrees, in degrees-minutes-seconds and, with a grid, as easting and northing, with the ±.
4. For a point above the ground (a roof corner), type its **height above the reference plane**.
5. The detail line breaks the ± down and, with an elevation model, adds the elevation.

<a id="measure-geo-the-scale-window-s-position-block"></a>

### The Scale window's Position block

The block starts with **Position:** and the source, for example `Fit to 2 GCPs with latitude/longitude (similarity, rotation and scale; no check)`, `Orthomosaic georeferencing: WGS 84 / UTM zone 16N (EPSG:32616), pixel 0.025 m` or `Camera GPS position and heading (…)`.

- With the camera as source: **Heading (°)**, clockwise from true north, shows the file's value as its placeholder and a note on where it came from (for example `gimbal yaw in the file`); the box after **±** is its uncertainty (blank = 2°). **GPS accuracy (m)** is horizontal and radial (blank = 3 m, a consumer receiver; with an RTK fix the file's own value).
- With an orthomosaic: **Georeferencing accuracy (m)**, placeholder `not included`. Type the check-point error from Metashape's processing report; until then the ± covers only your click.
- With a GCP fit: a line lists each GCP's residual and, once the GCPs can check each other, the Birge factor, for example `Birge factor 1.00 (1 = the GCPs agree with their stated accuracy)`.

<a id="measure-geo-the-ground-control-points-list"></a>

### The Ground control points list

Each row has the GCP's name and the position box, placeholder `lat, lon  ·  E, N  [± 0.05]`.

- Type or correct the position there. Enter applies it, Esc puts back the stored one, an empty box clears it. Text that is not understood gets a red border and changes nothing.
- `position not set` (amber) means the GCP has a name only.
- `accuracy 0.05 m (default)` shows the accuracy in use.
- When the GCPs are the position source, `fit residual …` shows how far the fit misses each one, with `(exact fit, no check)` when there are just enough of them.
- **✕** removes the GCP.

While a GCP uses the default accuracy a hint reads `The default accuracy is survey grade. For a phone or handheld GPS (3–5 m) type, for example, “name, lat, lon ± 4” when placing the point.`

<a id="measure-geo-example-two-gcps-on-a-site-picture"></a>

### Example: two GCPs on a site picture

A 4000 × 3000 px picture without a focal length in its file shows two surveyed targets (the geo specification's vectors).

1. With **🎯 GCP**, click the first target and type `A, 41.1103, -85.211`; click the second, 1500 px away, and type `B, 41.1104, -85.2109`.
2. The Scale line reads `1 GCP pair: 0.00928 m/px (flat picture, no camera geometry)`: the targets are 13.92 m apart, and 13.92 m ÷ 1500 px = 0.00928 m/px.
3. The Position block reads `Fit to 2 GCPs with latitude/longitude (similarity, rotation and scale; no check)`, and a note says two GCPs fit exactly, so nothing checks them.
4. With **⌖ Position**, click halfway between the targets. The row reads `41.110350, −85.210950 (41° 06′ 37.260″ N, 85° 12′ 39.420″ W) ± 0.05 m`, the detail line `± 0.053 m = GCP fit 0.051 m · marking 0.013 m`.
5. More GCPs add residuals and a Birge factor. In the specification's four-GCP case each misses the fit by 3.5 cm against a stated ±0.02 m: the factor reads 2.23 and a warning asks you to check the coordinates and where they are marked.

By comparison, on a DJI photo looking straight down from 60 m, with no GCPs, a point 6 m from the centre reads `41.110246, −85.211000 (41° 06′ 36.9″ N, 85° 12′ 39.6″ W) ± 3 m` from the camera: 3 m is the default GPS accuracy.

<a id="measure-geo-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Phone and handheld GPS points are good to 3–5 m, not 5 cm. Type `± 4` when you place them, or the fit trusts them too much and warns that the GCPs disagree.
- Two GCPs fit exactly and check nothing; three in an affine fit do not either. Use four or more to see residuals and the Birge factor.
- Keep the GCPs of one picture in one kind. Mixing latitude/longitude with easting/northing brings a warning: positions use only one kind, and for the scale GCPs are paired only within their own kind.
- Camera positions are a few metres off at best. On a picture taken at −45° from 50 m, a 1° gimbal pitch error moves the centre point by about 1.75 m, an error the ± does not include. Use them to find features, not to stake out.
- Easting/northing GCPs give positions as easting and northing in their own grid (`E …, N …`, bearings marked `(grid)`), not latitude and longitude.
- Exports follow the same sources. **📐 Export linework…** offers **Map coordinates** with a projected orthomosaic (WGS 84 / UTM or another projected system) or with easting/northing GCPs; a latitude/longitude orthomosaic or GCP fit has none. GeoJSON needs a WGS 84 position: a WGS 84 / UTM or WGS 84 latitude/longitude orthomosaic, GCPs with latitude/longitude, or a camera position. An orthomosaic in another system (NAD83 / UTM, a state plane) gives no GeoJSON, even with latitude/longitude GCPs, because it comes first. See [Exporting linework](#mapping-deliverables-exporting-linework).

> **Under the hood**
>
> Precedence: the orthomosaic's georeferencing, then a GCP fit (two or more GCPs of one kind), then the camera. A GCP fit is a weighted least-squares similarity for two GCPs (or collinear ones) and an affine for three or more, from the picture's reference plane to the map: a local transverse Mercator plane at the GCPs for latitude/longitude GCPs, their own grid for easting/northing GCPs. Each GCP is weighted by its accuracy combined with its marking. The Birge factor is √(χ² ÷ degrees of freedom), at least 1, and scales the fit's ± when the residuals exceed the stated accuracies.
>
> A camera position rotates the ground point by the heading (gimbal yaw, else the aircraft's heading, else the EXIF direction) about the GPS position. Its ± combines GPS (3 m by default), heading (2° by default, times the distance), scale or altitude, marking and focal length.
>
> Every position ± is horizontal and radial: about 63 % of positions fall within it. Not included: gimbal pitch error, lens distortion, relief (unless a height is typed), the antenna-to-camera offset, magnetic declination, datum differences such as NAD83 against WGS 84 (about 1 m).

<a id="measure-geo-see-also"></a>

### See also

- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Thermal Studio: getting started](#thermal-start)
- [Orthomosaic export, linework files and volume tickets](#mapping-deliverables)

<sub>[Back to contents](#contents)</sub>

<a id="measure-elevation"></a>

## Elevation models: pairing a DEM, slopes, cut and fill volumes, solids


A Metashape elevation model (DEM or DSM) adds the third dimension to an orthomosaic. Once it is paired, **⟋ Slope** reads the pitch of a roof or bank, points get elevations, and an area reports its cut, fill and net volume. Without one, an area can still give a volume as a solid of a height you type.

<a id="measure-elevation-before-you-start"></a>

### Before you start

- A georeferenced orthomosaic GeoTIFF from Metashape is in the library, in any coordinate system (WGS 84 / UTM or latitude/longitude for positions in degrees). See [Positions, ground control points and georeferenced orthomosaics](#measure-geo).
- The matching elevation model is exported from Metashape as a one-band GeoTIFF in the same coordinate system, covering the same ground.
- Its file name contains `DEM`, `DSM`, `DTM`, `elev`, `elevation`, `height` or `heights` as a word, for example `site_DSM.tif`. Otherwise it is not paired automatically (you can still pick it).
- A solid volume needs only a picture with a scale (see [Giving a picture a scale](#measure-scale)) and the solid's height.

<a id="measure-elevation-pair-the-elevation-model"></a>

### Pair the elevation model

1. Press **+ Import photos / videos** in the Photogrammetry tab or the Thermal Studio, or drop the file on the window. Both tabs share Metashape rasters.
2. In the library its subtitle reads `Elevation model (DEM, GeoTIFF)`.
3. Select the orthomosaic and press **🧭 Scale**. The **Elevation:** line names the paired file, for example `site_DSM.tif (automatic)`, or `no DEM`.
4. To choose another file, or none, use the **Elevation model** select: `Automatic (by name)`, one entry per matching file, or `None`.
5. Type its accuracy in **DEM accuracy per sample (m)** if you know it (blank = 0.05 m; the note suggests `about 1–2 × the DEM pixel for a controlled survey; worse on vegetation and edges`).
6. The line below gives the vertical unit, the vertical datum and the DEM pixel size.

When a one-band raster matches but its name says nothing, a blue note reads, for example, `1 one-band raster matches this orthomosaic; pick the elevation model (DEM) in the 🧭 Scale window.`

<a id="measure-elevation-slope"></a>

### Slope

1. Press **⟋ Slope** (greyed out until an elevation model is paired).
2. Click the low end, then the high end (eave to ridge, toe to crest), or drag between them.
3. Read the label: the pitch in degrees and as x:12, for example `S1: 26.6° (6.0:12)`.
4. Read the **Slopes** row: pitch, x:12, `grade` (%), `run` (horizontal), `rise` (end minus start) and `slope length`, each with its ±; the detail line adds both elevations and the bearing.

<a id="measure-elevation-volume-inside-an-area"></a>

### Volume inside an area

1. Draw an outline with **⬠ Area** around the pile, the pit or the slab (see [Measuring lengths, angles and areas](#measure-tools)). Trace it on bare ground at the toe of a pile.
2. In the **🧭 Scale** window, under the area's row, open the **Volume** select:
   - `None`: no volume (the default);
   - `Automatic`: from the elevation model when the picture has one, else a solid (once that is known it reads `Automatic: from the elevation model` or `Automatic: a solid`);
   - `From the elevation model`: cut and fill against a base surface;
   - `A solid`: area × height × a shape factor.
3. For the elevation model, pick the **base**:
   - `Plane through the outline` (the default): fitted to the ground along the outline; best on sloping ground.
   - `Lowest point of the outline`: a level base at the lowest outline point.
   - `Mean elevation of the outline`: a level base at the outline's mean height.
   - `An elevation I type`: a level base at your elevation, in the elevation model's vertical datum (the placeholder is the plane's elevation).
4. The result reads `cut … · fill … · net …`. Cut is the volume above the base, fill the volume below it, net their difference (negative for a pit). The label on the picture ends with the net.
5. For a solid, pick one in **solid** (it starts at `Choose a solid…`), then type its **height**:
   - `Prism or box: area × height`;
   - `Cone or pyramid: 1/3 × area × height`;
   - `Dome (half-ellipsoid): 2/3 × area × height`.

The result is one volume with its ±; the detail line repeats the factor, the height `(typed, exact)` and the ± breakdown.

To give other areas the same volume setting, click **⇉ others…** on the area's volume line, tick the areas (**All**, **None**) and click **Apply**. Each ticked area gets the whole setting: the method, the base, a typed base elevation, the solid and its height. The button is off while the area has no volume setting (`None`): there is nothing to copy. A line reads, for example, `Volume applied: changed A2 and A3.` There is no undo, so check the ticks first. A typed base elevation is copied as it is, so check that it suits each area.

The picture total, under the picture and in both windows, sums the volumes after the areas. Solids are one group; elevation-model volumes add cut, fill and net, each on its own, so a pit does not cancel a pile in the cut. An area whose volume is still being read shows as `(1 still being read)`, one without a value as `(1 without a value)`. Areas that overlap are counted twice.

To hand a volume over, print it with **🧾 Volume ticket…** in the Photogrammetry library: a numbered PDF, Word or RTF ticket with cut, fill and net and their ±, the base, the sources, a figure of the outline and, with a material, the tonnage. See [Printing a volume ticket](#mapping-deliverables-printing-a-volume-ticket).

<a id="measure-elevation-example-a-stockpile-and-a-pit"></a>

### Example: a stockpile and a pit

The synthetic test pair `pile_ortho.tif` and `pile_DSM.tif` (0.1 m and 0.2 m pixels) has a mound of exactly 1000π ≈ 3,142 m³ and a pit of 10 m × 6 m × 2 m = 120 m³.

1. Draw a circle **⬠ Area** around the mound, 24 m in radius. Set **Volume** to `From the elevation model` with the plane base.
2. The window reads `cut 3142 m³ ± 63 m³ · fill 0 m³ · net 3142 m³ ± 90 m³`, and the label `A1: 1809 m² ± 21 m² · 3142 m³ ± 90 m³` (imperial `A1: 19476 ft² ± 230 ft² · 4109 yd³ ± 118 yd³`). The area is π × 24² ≈ 1,810 m².
3. The net ± is the area times the DEM accuracy: 1,809 m² × 0.05 m ≈ 90 m³. The cut ± uses only the 1,257 m² that lie above the base: 1,257 × 0.05 ≈ 63 m³.
4. With only the mound drawn, the picture total reads `Picture total: 1 area 1809 m² ± 21 m² · 1 elevation-model volume: cut 3142 m³ ± 63 m³ · fill 0 m³ · net 3142 m³ ± 90 m³`.
5. Switch the base to `Mean elevation of the outline`. Net stays 3142 m³, but the ± grows to 677 m³ and a warning says the outline is not level: on sloping ground use the plane.
6. Draw a rectangle over the pit. With the plane base its label reads `A2: 140 m² ± 2 m² · −120 m³ ± 7 m³`.
7. On a picture with no elevation model, a small gravel heap outlined as 4.00 m² and set to a cone 3 m high reads `4.00 m³ ± 0.05 m³`: ⅓ × 4 m² × 3 m = 4 m³.

A slope on the matching ramp test pair, 10 m of run and 5 m of rise, reads `26.6° ± 0.3° · 6.0:12 ± 0.1 · grade 50.0 % · run 10.00 m ± 0.14 m · rise +5.00 m ± 0.10 m · slope length 11.18 m ± 0.16 m`: atan(5 ÷ 10) = 26.6°, 12 × 5 ÷ 10 = 6.0, √(10² + 5²) = 11.18 m.

<a id="measure-elevation-which-volume-a-material-uses"></a>

### Which volume a material uses

When you add a volume material (gravel, fill dirt, concrete) to an area with an elevation-model volume, its line gets one more select, the *Which volume* choice:

- `The larger of cut and fill` (the default);
- `Cut (above the base)`: material hauled away;
- `Fill (below the base)`: material brought in;
- `Net (cut minus fill)`.

For the 120 m³ pit, pick `Fill (below the base)`. See [Material take-offs](#materials-takeoff).

<a id="measure-elevation-tips-and-common-mistakes"></a>

### Tips and common mistakes

- The elevation model must cover the whole outline. Cells without data count as level with the base, so the volume comes out low, and a warning gives the share missing.
- A candidate must be a one-band numeric Metashape raster in the orthomosaic's coordinate system that overlaps it; automatic pairing then also needs the name rule (or a file imported as an elevation model), and the largest overlap wins, then the finest pixel. The name matters because a thermal orthomosaic is also a one-band raster: pairing by tags alone would read temperatures as elevations.
- Trace a pile on bare ground just outside its toe; an outline crossing a fence or vegetation makes the base rough, and a warning says so.
- For a pile, quote the net or the cut. The fill ± can be larger than the fill itself, because flat ground around the pile dips below the base by noise.
- Elevations, rises, heights and the DEM accuracy follow **Altitude** in Settings → Units; volumes follow **Distance** (m³, or ft³ below one cubic yard and yd³ above).
- **📐 Export linework…** can write the elevation model's heights into the DXF and XML (tick **Heights from the elevation model**). A feature gets heights only when every vertex has one, and they are in the elevation model's vertical reference, which the file names; the GeoJSON keeps them in a `zM` property. See [Heights and the vertical reference](#mapping-deliverables-heights-and-the-vertical-reference).
- A solid assumes its shape: a cone holds a third of a box of the same plan area and height, a dome two thirds. When the shape is uncertain, use the elevation model.

> **Under the hood**
>
> A slope's rise comes from the elevation model at both ends (bilinear between pixel centres), its run from the orthomosaic's scale. Pitch = atan(rise ÷ run), x:12 = 12 × rise ÷ run, grade = 100 × rise ÷ run. The ± combines the marking (±1 px, with the elevation model re-sampled) and √2 × the DEM accuracy.
>
> An elevation-model volume sums, cell by cell, the DEM's height above or below the base over every cell whose centre lies inside the outline (the midpoint rule; the mound test agrees with 1000π to 0.003 m³). One read of the raster returns all four bases, so switching the base needs no new read.
>
> The ± takes the DEM's accuracy as one shift shared by the whole area, plus a base term: σ_net = area × √(σ_DEM² + σ_base²), where σ_base is the outline's scatter for a plane or mean base, σ_DEM for the lowest point, and 0 for a typed elevation. That is conservative, an upper bound. Not included: the outline's marking, DEM errors other than one shift, the horizontal misregistration between orthomosaic and DEM, compaction and swell.
>
> A solid is factor × plan area × height: prism 1, cone or pyramid ⅓, dome ⅔. The height is exact, so its ± is the area's ± times the same factor and height.

<a id="measure-elevation-see-also"></a>

### See also

- [Measuring lengths, angles and areas](#measure-tools)
- [Positions, ground control points and georeferenced orthomosaics](#measure-geo)
- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Thermal Studio: getting started](#thermal-start)
- [Orthomosaic export, linework files and volume tickets](#mapping-deliverables)

<sub>[Back to contents](#contents)</sub>

<a id="materials-takeoff"></a>

## Material take-offs: from a measurement to an order, waste, prices


A take-off turns a measurement on a picture into an order: how many bundles of shingles, fascia boards or tons of stone to buy. You pick a material under a measurement or an area in the **🧮 Material Takeoff** window; the app adds the waste allowance, rounds up to whole units and, with a price, works out the cost. The same rows go into the report.

<a id="materials-takeoff-before-you-start"></a>

### Before you start

- A picture with a scale. Without one the row reads `no scale`. See [Giving a picture a scale](#measure-scale).
- A **📏 Measure** line (materials sold by length) or an **⬠ Area** (by area, roof surface, perimeter or volume). See [Measuring lengths, angles and areas](#measure-tools).
- For a volume material: an area with a volume, a solid or a cut and fill. See [Elevation models](#measure-elevation).
- For roofing: a pitch from a **⟋ Slope** or an **∠ Angle** with a level ray, or one you type, or the default 6:12.

<a id="materials-takeoff-steps"></a>

### Steps

1. Click **🧮 Material Takeoff** in the toolbar, right after **🧭 Scale**. A window opens over the picture, near its top-left corner, a little below the zoom buttons and a little lower and to the right of the 🧭 Scale window. Drag it by its title bar, resize it at its bottom-right corner, and close it with its **✕** or the toolbar button. Once you have moved or resized it, it opens at that place and size again, in both studios; a window you never moved opens at that default place each time. In the window every measurement (`M1`…) and area (`A1`…) has a **Materials** line. While the picture is being read the window says `Reading the picture…`; a picture without a scale and without measurements or areas says `This picture has no scale yet: set it in 🧭 Scale.` (with measurements or areas, each row reads `no scale`); a scaled picture without measurements or areas says `Draw a 📏 Measure line or an ⬠ Area, then add its materials here.`
2. Open **+ Material…** on that row. Materials are grouped by category: `Roofing`, `Exterior walls, fencing and decking`, `Concrete`, `Masonry`, `Pavement`, `Landscape and drainage`, `Bulk materials`, `Other`.
3. Pick a material, for example `Asphalt shingles — by roof surface`. The list offers only what the row can give (see the table below). A line appears with the material's fields and, under them, the take-off sentence.
4. Change **waste** if the job needs another allowance. Blank means the preset's percentage, shown greyed in the box.
5. For roofing, choose the **pitch**: a slope such as `S1: 6.0:12 (elevation model)`, an angle such as `∠1: 6.0:12 (in the picture)`, or `Typed`. With `Typed`, enter the rise in **x** (`6` for 6:12). A blank **x** (it shows a greyed `6`) uses the default 6:12: the sentence reads `(pitch 6.0:12, default)` and a blue note reads, for example, `Asphalt shingles: No pitch chosen: worked out at the default 6.0:12. Choose a slope or an angle, or type x.` The default is a guess, so the roof surface reads with `≈` and the count of units has no ± (the plan area keeps its ±).
6. For a volume material on an elevation-model volume, choose `The larger of cut and fill` (the default), `Cut (above the base)`, `Fill (below the base)` or `Net (cut minus fill)`.
7. Type a **price** per order unit (per bundle, per ton). Blank means the preset's price; the shipped presets have none. The sentence then ends with the cost, such as `× $38.50 = $2,849.00`.
8. Read the block's footer once a take-off is priced. It reads like `Projected cost: $4,120.50 for 3 materials (of which waste $269.50; 1 without a price)` (illustrative figures; the worked example below gives real ones). Once a take-off is priced, a line above the window's notes adds up every take-off of the picture, for example `Projected cost for this picture: $4,120.50 for 3 materials (of which waste $269.50; 1 without a price)`.
9. Read the picture total, above that line: the sum of the picture's areas and volumes, for example `Picture total: 2 areas 1240 m² ± 12 m²` (illustrative figures). It shows also before anything is priced, and it is the same line as under the picture and in the 🧭 Scale window. Areas that overlap are counted twice. See [Measuring lengths, angles and areas](#measure-tools-the-scale-window-rows).
10. To copy a take-off of an area to other areas, click **⇉ others…** on its line (it shows only on an area's line, when the picture has another area; **Cancel** closes the panel without copying). Tick the areas (**All**, **None**), tick the fields to copy (`waste`, `pitch` for roofing, `volume part` for a volume material on an elevation-model volume, `price`), and click **Apply** (the focus goes back to **⇉ others…**). An area without the material gets a new line with only the ticked fields: an unticked waste or price uses the material's own value, and an unticked pitch stays blank, so that roof reads at the default 6:12 with its note until you choose its pitch. On an area that has the material, every line of that material keeps its place and takes the ticked fields. A line reads, for example, `Crushed stone applied: added to A2 and A3; skipped A4: it has no volume.` When nothing changes, nothing is saved and the line says so. There is no undo, so check the ticks first.
11. If **↻ use the catalogue's values** appears, the catalogue's preset has changed since you added the material. Click it to take the new values; the waste, pitch and price you typed stay.
12. Remove a take-off with **✕** at the end of its line.

| Row | A material can be taken from |
|---|---|
| Measure line | `length` |
| Area | `plan area`, `roof surface`, `perimeter` |
| Area with a volume | the above, plus `volume` |

<a id="materials-takeoff-in-the-report"></a>

### In the report

Both report builders have a **Materials and Projected Cost** section. The photogrammetry report reads the queued pictures; the thermal report reads the pictures of its imaging pairs.

1. Open **📄 Report ▼** → **Open report builder…** and scroll to **Materials and Projected Cost**.
2. Click **📦 Add materials from pictures**. A row appears for each take-off, with its price. Rows already in the report are not added again. Take-offs without a quantity are skipped, and the notice names each one with its reason (five at most), for example `1 material take-off(s) have no quantity yet and were skipped: Figure 1 A1 Asphalt shingles: No roof pitch: S1 has no elevation. Finish them in 🧮 Material Takeoff on those pictures.` Rows worked out at the default pitch add `N take-off(s) use the default pitch 6:12 (not measured): type the real pitch in 🧮 Material Takeoff, then remove the row here (✕) and add materials again.`, and their **Basis** reads `(pitch 6.0:12, default)`. An import never changes the order, the basis or the price of a row already in the report (it only fills in a missing waste figure or area): after you type the real pitch, remove the row with **✕** and click **📦 Add materials from pictures** again. Until you do, each import reminds you with `N row(s) added earlier still use the default pitch 6:12, and their take-off now has a pitch: remove those rows (✕) and add materials again.`
3. Check each row: **Material**, **From**, **Order**, **Unit**, **Waste %**, **Waste units**, the unit price, the **Basis** sentence and a **Note** (supplier, quote number). **Cost** shows under it `of which waste $…` whenever the row has a cost and its waste units are known, even when that is $0.00.
4. Set the **Currency** (`USD`, `EUR`, `CAD`…). While no row has a price, the report takes the catalogue's currency.
5. Read the total line, for example `Projected total $2,849.00 for 1 priced row · of which waste $231.00`. Rows without a price or an order count are counted after it (`· N row(s) without a price or an order count (not in the total)`) and left out of the total.
6. When a row came from an area, read the area line under it, for example `Total plan area 600 m² of 1 measured area (plan area, not roof surface)`. It prints whole units from 100 up, at most one decimal below 100 and two in ha or ac (`12.0` prints as `12`). Each area counts once, however many rows it gives; when its rows disagree (the outline was redrawn between two imports) the first row's value is kept. Overlapping areas are counted twice. Rows added before this line existed show no area: press **📦 Add materials from pictures** again to fill them in (only what is missing is filled; nothing else of the row changes).
7. Add a row by hand with **+ Add material**, or remove one with **✕**.
8. Click **Preview & edit**. The table has the columns Material, From, Basis, Order, Unit price, Cost and Waste. From starts with `Figure 2` (photogrammetry) or `Pair 2 (thermal)` (thermal). Below the rows come `Projected total` and, when waste costs something, `Waste allowance (in the total)`, then a note that prices were entered by the inspector and the total is a projection. When the rows carry areas, `Total plan area` follows, for example `600 m² (1 measured area)`, with a note that a pitched roof's surface is larger and is in the Basis of its rows.

<a id="materials-takeoff-example-a-6-12-shingle-roof"></a>

### Example: a 6:12 shingle roof

Area `A1` is a 2,000 ft² plan area. You add `Asphalt shingles — by roof surface`, keep 10 % waste, choose `Typed` and enter `6`:

```
2000 ft² plan area × 1.118 (pitch 6.0:12, typed) = 2236.07 ft² roof surface + 10 % waste = 2460 ft²; 24.6 squares of 100 ft²; order 74 bundles (3 bundles per square)
```

The pitch factor is √(1 + (6/12)²) = 1.118, so the roof is 2,236.07 ft². Plus 10 % it is 2,460 ft², or 24.6 squares. At 3 bundles per square that is 73.8, rounded up to 74 bundles. At 0 % waste it would be 22.36 × 3 = 67.1, so 68: the allowance adds 6 bundles.

You type `38.50` as the price: 74 × $38.50 = $2,849.00, of which waste 6 × $38.50 = $231.00. With an unpriced drip edge also on `A1`, the footer reads `Projected cost: $2,849.00 for 1 material (of which waste $231.00; 1 without a price)`. In the report the row's Waste cell reads `10 % · 6 of 74 bundles` over `$231.00`.

| Take-off | Order | At 0 % | Waste |
|---|---|---|---|
| Fascia boards, 16 ft, 160 ft perimeter, 10 % | 11 boards | 10 | 1 board |
| Concrete, ready-mix, 4.94 yd³ slab, 10 %, $165 per yd³ | 6 yd³ | 5 | $165.00 |
| Crushed stone, 120 m³ fill, 10 %, $32 per ton | 233 tons | 212 | 21 tons, $672.00 |
| Sod, 1,500 ft², 5 % | 4 pallets | 4 | none |

Stone is sold by weight: 132 m³ (with waste) × 1,600 kg/m³ = 211,200 kg, ÷ 907.18 kg per ton = 232.8, so 233 tons.

<a id="materials-takeoff-tips-and-common-mistakes"></a>

### Tips and common mistakes

- A plan area is not a roof surface. Use the `roof surface` option for roofing and check its pitch.
- A blank price means not priced: the take-off stays out of the total. Type `0` for a free material.
- Catalogue edits do not change take-offs already on pictures. Use **↻ use the catalogue's values** line by line.
- The currency relabels prices; it never converts them.
- Re-running **📦 Add materials from pictures** is safe: rows already added are skipped.
- A roof line without a pitch is not skipped: it is worked out at the default 6:12 with the note `Asphalt shingles: No pitch chosen: worked out at the default 6.0:12. Choose a slope or an angle, or type x.` The default is a guess: choose the real pitch. A notice such as `Asphalt shingles: No roof pitch: S1 has no elevation.` means the slope or angle it names needs fixing.
- A volume ticket (**🧾 Volume ticket…**) prints the tonnage of one volume from a material's density: the measured part × the density, with its ±, and no waste. It preselects the material and part of the area's volume take-off, so its mass is the take-off's before waste: the 120 m³ fill at 1,600 kg/m³ is 192 t on the ticket, while the take-off orders 233 tons with 10 % waste. See [Printing a volume ticket](#mapping-deliverables-printing-a-volume-ticket).

> **Under the hood**
>
> The count is the quantity (× √(1 + (x/12)²) for roofing), plus the waste percentage, divided by what one unit covers, rounded up. With a package the rounding is done in packages from the exact count: 24.6 × 3 = 73.8, so 74 bundles, not 25 squares × 3 = 75. By weight: volume × density, then weight ÷ the weight of one unit. Waste units are the order minus the order at 0 %. Prices are per order unit, and each cost is rounded to the cent as printed, so the window, the builder and the export agree.
>
> Presets are rules of thumb: check them against the product. Values are stored in metric and shown in your units. Each take-off keeps a copy of its preset, so a picture reads the same anywhere.

<a id="materials-takeoff-see-also"></a>

### See also

- [Editing the material catalogue: presets, units, packages, waste, prices](#settings-material-presets)
- [Measuring lengths, angles and areas](#measure-tools)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Orthomosaic export, linework files and volume tickets](#mapping-deliverables)

<sub>[Back to contents](#contents)</sub>


---

# Settings

<a id="settings-material-presets"></a>

## Editing the material catalogue: presets, units, packages, waste, prices


The material catalogue is the list the **+ Material…** chooser offers in the **🧮 Material Takeoff** window. Each preset says how a material is measured, what it is sold as, what one unit covers, how it is packed, the usual waste and, if you want, a price. You edit it in Settings, so the take-offs match your suppliers and your prices.

<a id="settings-material-presets-before-you-start"></a>

### Before you start

- The desktop app, with the Thermal or the Photogrammetry add-on enabled. The section shows only then.
- Set Settings → Units first. The form shows numbers in your distance system (ft, ft², yd³ or m, m², m³), and changing the system closes an open form.
- Wait for the list to load. While `Reading the stored presets…` shows, every control is disabled.

<a id="settings-material-presets-steps"></a>

### Steps

The table lists the presets under category headings; the shipped catalogue has 54 US presets. Its columns:

| Column | What it shows |
|---|---|
| Material | The name; hover it for the note |
| Measured by | `Length`, `Area`, `Roof surface` or `Volume` |
| Sold as | The unit, such as `square / squares` |
| One unit covers | Such as `100 ft²`; for weighed materials the weight at a density, such as `2000 lb at 99.9 lb/ft³` |
| Package | Such as `3 bundles per square`, or `—` |
| Waste | Such as `10 %` |
| Price per order unit | Such as `$38.50 / bundle`, or `—` |

1. Open **Settings**, find **Material take-off presets** in the right column and click **Material take-off presets…**. The catalogue opens in its own window.
2. Set **Currency** above the table: three letters, such as `USD`, `EUR` or `CAD`. Press Enter or leave the box to apply it; Esc puts it back.
3. Narrow the table with the **Category** dropdown at the top of the window or by typing part of a name in **Search materials**. The filter only changes what the table shows: **+ Add a material**, **Edit**, **Delete** and **Reset to the shipped presets** still work on the whole catalogue, and a line under the table says how many presets show.
4. Click **+ Add a material** for a new preset, or **Edit** on a row to change one. A form opens above the table and the row is highlighted.
5. Type the **Material** name and choose its **Category**: `Roofing`, `Exterior walls, fencing and decking`, `Concrete`, `Masonry`, `Pavement`, `Landscape and drainage`, `Bulk materials` or `Other`.
6. Choose **Measured by**: `Length or perimeter`, `Area`, `Roof surface (area × pitch factor)` or `Volume`. Switching between length, area and volume resets **One unit covers** to 1.
7. Choose **Sold as**. The list fits the basis: `ft`, `m`, `ft²`, `m²`, `square / squares`, `sheet / sheets`, `bundle / bundles`, `ft³`, `yd³`, `m³`, `gallon / gallons`, `ton / tons`, `tonne / tonnes`, `lb`, `kg`, then counts such as `piece / pieces`, `board / boards`, `roll / rolls`, `bag / bags`, `pallet / pallets`. For your own word pick `Other…` and fill **Sold as (one)** and **Sold as (many)**.
8. Check **One unit covers**. Picking a unit fills it when the size is known: a square is 100 ft², a sheet 32 ft² (4 × 8 ft), a bundle 33⅓ ft². Change its unit in the list next to it (`ft`, `in`, `m`, `cm`; `ft²`, `square (100 ft²)`, `m²`; `ft³`, `yd³`, `gal (US)`, `m³`); the number is converted.
9. For a volume material, picking `ton / tons`, `tonne / tonnes`, `lb` or `kg` ticks **Sold by weight**, fills **Weight per unit** (its unit: `lb`, `ton (2,000 lb)`, `kg`, `tonne (1,000 kg)`) and, when **Density** is blank, fills it with 100 lb/ft³ or 1,600 kg/m³. Check both against the product. Without that tick the field reads **Density (optional, shows the weight)**.
10. Choose **Waste**: `0 % — exact count (panels, posts, fixtures)`, `5 % — simple gable roof, straight runs`, `10 % — standard`, `15 % — hips and valleys, many cuts`, `20 % — complex roof, patterns, diagonal layouts`, or `Other…`, which adds a small box followed by `%` (named `Waste (custom)` for screen readers) for your own figure.
11. Under **Package (optional)**, pick `No package` or a package: `bundle / bundles`, `box / boxes`, `carton / cartons`, `case / cases`, `bag / bags`, `roll / rolls`, `pallet / pallets`, `pail / pails`, or `Other…`, which adds two boxes showing `bundle` and `bundles` as placeholders (`Package (one)` and `Package (many)`) for your own words. Next to the package a count box (placeholder `3`, followed by `per unit`; named `Packages per unit`) fills from the convention: 3 bundles or 0.5 box per square. Otherwise it stays blank and the form asks for it.
12. Type the price in **Price per** (the order unit and currency follow, such as `Price per bundle (USD)`). Leave it blank for `not priced`.
13. Add a **Note (shown on hover in the 🧮 Material Takeoff window)**, then click **Save**. `Material presets saved.` confirms it. **Cancel** closes the form. Esc closes the form first, and a second Esc closes the window.
14. Click **Delete** on a row to remove a preset. It goes at once, with no question.
15. Click **Reset to the shipped presets** to start over. The app asks first; your own presets and edits are removed, the currency stays.

<a id="settings-material-presets-example-four-bundles-to-the-square"></a>

### Example: four bundles to the square

Your supplier's architectural shingles come 4 bundles to the square, at $42.00 a bundle, and your roofs have hips and valleys.

1. Click **+ Add a material**, name it `Architectural shingles, 4 bundles`, category `Roofing`.
2. **Measured by** `Roof surface (area × pitch factor)`, **Sold as** `square / squares`: **One unit covers** shows `100` ft².
3. **Waste** `15 % — hips and valleys, many cuts`.
4. **Package** `bundle / bundles`: the count box before `per unit` shows `3`. Change it to `4`.
5. Type `42` in the price field, which now reads `Price per bundle (USD)`, then click **Save**.

On the 2,000 ft² plan area at 6:12 (2,236.07 ft² of roof): + 15 % = 2,571.48 ft², 25.71 squares × 4 = 102.9, so 103 bundles. At 0 % it is 22.36 × 4 = 89.4, so 90: the waste adds 13 bundles. The cost is 103 × $42.00 = $4,326.00, of which waste 13 × $42.00 = $546.00.

<a id="settings-material-presets-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Prices are per order unit: per bundle when there is a package, not per square.
- Changing **Sold as** or **Package** re-derives the packages-per-unit count. A package with the same name as the new unit is dropped (sold by the bundle, nothing comes inside it).
- Editing a preset changes only new take-offs. Old ones keep their copy until you click **↻ use the catalogue's values** in the 🧮 Material Takeoff window.
- Changing the currency relabels the prices; it does not convert them.
- If the red notice says the stored presets could not be read, click **Try again**. Until then the shipped list shows and nothing can be saved.

> **Under the hood**
>
> **Save** stays disabled while the form shows a problem: `Give the material a name.`, `Give the unit a name, for one and for many.`, `One unit must cover more than zero.`, `Waste must be between 0 % and 100 %.`, `A material sold by weight needs its weight per unit and its density, both above zero.`, `A package needs a name and how many come in one unit (above zero).` or `The price must be zero or more.`
>
> Values are stored in metric (m, m², m³, kg, kg/m³) and shown in your units; a number you leave alone keeps its exact stored value. The dropdowns only fill fields in: a stored preset holds plain words and numbers. A weighed material is worked out as volume × density, then weight ÷ weight per unit. The shipped presets are rules of thumb, with no prices because prices are regional. Each take-off keeps a copy of the preset it was made with.

<a id="settings-material-presets-see-also"></a>

### See also

- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Giving a picture a scale: references, altitude and pitch, the Scale window, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)

<sub>[Back to contents](#contents)</sub>

<a id="settings-branding"></a>

## Branding your reports: logo, company and Part 107 number


Branding puts your company on every report the Thermal and Photogrammetry add-ons produce: your logo and company name at the top of the first page, your name and FAA Part 107 certificate number, your contact details, and your company as the publisher under the title. You enter it once in Settings. New reports also start with your name, certificate and contact already filled in. The company name also appears in the footer of the 360 Panorama Studio's HTML viewer file.

<a id="settings-branding-before-you-start"></a>

### Before you start

- The desktop app, with the Thermal or the Photogrammetry add-on enabled. The section shows only then.
- Open **Settings** and find **Branding**. It comes first among the add-on sections.
- Have your logo as a PNG or JPEG file of 8 MB at most.
- Wait for the form to load. Until the stored branding has been read, every field is disabled.

<a id="settings-branding-steps"></a>

### Steps

1. Type your **Company name**. This is the one field the branding needs: as soon as it is saved, it replaces "Airwulf, LLC" as the publisher of your reports.
2. Type the **Operator (pilot / inspector)**: the person who flies and signs the reports.
3. Type your **FAA Part 107 certificate no.** exactly as it is printed on your remote pilot certificate.
4. Fill in **Phone**, **E-mail** and **Website**. An e-mail address must contain `@`. The website prints as text, not as a link.
5. Type the **Address**. The box has two rows; press Enter for a second line.
6. Click **Choose logo…** and pick your PNG or JPEG file. The logo is resized so that its longest edge is at most 512 px, and a small preview of it appears in the form.
7. To take the logo off again, click **Remove logo**, then **Save branding**.
8. Click **Save branding**. `Branding saved.` confirms it.
9. Open a studio and click **📄 Report ▼** → **Open report builder…**. The menu item reads `Opening…` while your branding and the details of your last report are read (at most 5 seconds), then the builder opens.
10. Look at the person fields of section 1. In the Photogrammetry Survey Report they are **Pilot / Operator**, **Pilot credentials** and **Pilot contact**; in the Thermal Inspection Report **Inspector Name**, **Credentials** and **Contact details**. They are filled from your branding (see the Example).
11. Click **Preview & edit**. The report opens with your logo and company at the top, a thin rule under them, then the title with "Generated by" and your company under it.
12. To stop branding your reports, click **Clear branding** in Settings. The app asks `Remove the branding? Reports go back to 'Generated by Airwulf, LLC'.`; confirm, and `Branding cleared.` shows.

When **Save branding** cannot save, the notice says why:

| Notice | What to do |
|---|---|
| `Enter the company name: it is the publisher printed on every report.` | You filled other fields or chose a logo but left the company blank. Type it. |
| `Nothing to save. Fill in the company name, or use Clear branding.` | Every field is blank and there is no logo. |
| `The e-mail address needs an @.` | Correct the **E-mail** or leave it blank. |
| `The logo file is too large (8 MB at most).` | Choose a smaller file. |
| `That file is not a PNG or JPEG image.` | Export the logo as PNG or JPEG first. |
| `The logo is too large even after resizing; use a simpler image.` | A very detailed picture; use a simpler version of the logo. |

<a id="settings-branding-example-harness-aerial-llc"></a>

### Example: Harness Aerial LLC

1. In **Branding**, type `Harness Aerial LLC` as **Company name**, `A. Pilot` as **Operator (pilot / inspector)**, `1234567` as **FAA Part 107 certificate no.**, `555-0100` as **Phone** and `ops@example.com` as **E-mail**.
2. Click **Choose logo…** and pick a 1600 × 400 px PNG. It is stored at 512 × 128 px.
3. Click **Save branding**.
4. In the Photogrammetry tab, open the report builder. In section 1 you find:
   - **Pilot / Operator**: `A. Pilot`
   - **Pilot credentials**: `FAA Part 107 remote pilot certificate no. 1234567`
   - **Pilot contact**: `Harness Aerial LLC · 555-0100 · ops@example.com`
5. Export the report as PDF. The first page opens with the logo and `Harness Aerial LLC`, the title is followed by `Generated by Harness Aerial LLC · Photogrammetry survey workflow`, and every page carries `Powered by Open DroneLog add-ons · Airwulf, LLC` centred under the footer line.

<a id="settings-branding-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Until a company name is saved, reports look exactly as before: no letterhead, `Generated by Airwulf, LLC` under the title, and no credit line.
- The credit line `Powered by Open DroneLog add-ons · Airwulf, LLC` stays on every branded report. It is printed small, centred under the page footer.
- Each time you save or export a report, its person, credentials and contact values become the start of your next new report of the same kind, except a value that equals what your branding fills in. A value you typed therefore keeps winning over your branding, even after a rebrand, until a saved report holds something else in that field. If a new report still shows an old name or number after a rebrand, change that field to the value you want and save the report; the next new report starts with it.
- A field you leave as the branding filled it is not remembered, so a change of branding reaches your next new report.
- The client and the claim details are never filled from the branding. Save your clients for reuse instead; see [Saving clients and claim details for reuse](#clients).
- If the notice `The stored branding could not be read.` shows, click **Retry**. The form stays disabled until the read succeeds.
- If the notice says `The stored branding could not be read; saving replaces it (a copy of the old value is kept).`, fill the form again and click **Save branding**; **Clear branding** is unavailable until then.
- If a save or export ends with `Its details could not be remembered for the next report.`, the report itself was saved or exported; only the next new report will not start from its person fields.

> **Under the hood**
>
> The branding is stored with your profile in the app's settings, so it is part of your backups. The logo is kept as an image inside the setting, at most 512 px on its longest edge (never enlarged), as PNG; a logo that would still be too large is stored as JPEG over a white background. On the page it prints at most 18 mm high and 50 mm wide, its proportions kept, with the text block to its right.
>
> A new report is filled in this order: the empty report, then your branding over the person, credentials and contact fields (when a company name is saved), then the values you typed into your last saved or exported report over everything they hold. A field that still equals what the branding would fill in is not remembered, which is why a typed value wins over a later rebrand and an untouched one does not.
>
> The letterhead, the publisher and the credit line are taken from the branding when you preview or export, so an older report exported today carries today's branding, and a bundle opened on another machine prints that machine's branding. The person fields, by contrast, are part of the report and keep what it was saved with. AI drafts name your company as the publisher.

<a id="settings-branding-see-also"></a>

### See also

- [Saving clients and claim details for reuse](#clients)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)

<sub>[Back to contents](#contents)</sub>

<a id="ai-usage"></a>

## AI usage: the usage bar, customers and projects, and the AI cost in reports


Every time the app asks an AI provider to write something (the AI narrative in the Thermal Studio, the AI drafts in the report builders and each answer in the **Chat** tab) it records the run. The AI usage bar shows what those runs used and what they cost, for the customer and project you are working on. A setting can add that cost to the report you send your client.

<a id="ai-usage-before-you-start"></a>

### Before you start

- The desktop app with the Chat connection set or at least one own AI provider key saved; see [AI provider keys](#thermal-anomalies-ai-provider-keys). Without either there is no bar.
- Save your customers under **Clients**; see [Saving clients and claim details for reuse](#clients). The bar lists them.

<a id="ai-usage-the-ai-usage-bar"></a>

### The AI usage bar

The bar shows only while the Chat connection is set or at least one provider has a key. You find it:

- under the Thermal Studio and under the Photogrammetry Studio;
- at the bottom of the report builder, where it is read-only (it shows the report's own customer and project).

It reads like this: the customer, the project, the figures of this job (`runs`, `tokens` and an estimated cost in US dollars) and the figures of the calendar month. It updates after every AI run, after you save or remove a key, and when you come back to the window.

<a id="ai-usage-picking-a-customer-and-a-project"></a>

### Picking a customer and a project

1. In the bar, open the customer list and pick a saved client. **No customer** is the choice when you have not picked one; the bar is amber then, as a reminder.
2. Type the project name in the project box. Names you already used with that customer are offered.
3. Run an AI narrative. The run is recorded for the customer and project that were picked at that moment.

While a report is open, the report's own **Client** and **Project name** are used instead, and you cannot change them in the bar.

<a id="ai-usage-what-is-counted"></a>

### What is counted

- Only the AI runs this app made on this computer, in this profile. Anything you did in a provider's own website or another program is not in it.
- The cost is an estimate: the tokens each answer reported, priced from a price list built into the app. The list has a date, shown in the bar's tooltip. A run through the Chat connection is priced the way the **Chat** tab prices it (the cost the provider reported, the rates you entered in **Connection**, or the Chat's own OpenAI list) and keeps that price. The provider's own bill is the authority; compare them now and then.
- Each answer in the **Chat** tab counts in the month, under **No customer**: a chat is never added to a customer's report. An answer you stop after its text began to appear counts as a run of unknown cost; one stopped before any text appeared is not counted.
- A run **not priced** is one whose model is not in the price list. A run **of unknown cost** is one whose answer never came back whole. Both are counted and named, never guessed into the money figure.
- Customer and project names are compared ignoring capitals, accents and extra spaces: `Müller  Bau` and `muller bau` are one customer.
- A run counts for what was picked when it ran. Changing the pick later does not move it.
- The calendar month is counted in UTC, so a run made late on the last evening of a month in your time zone can fall into the next month.
- The usage history belongs to this computer and profile. It is not part of backups or bundles.

<a id="ai-usage-adding-the-ai-cost-to-a-report"></a>

### Adding the AI cost to a report

1. Open Settings, find **AI providers** and tick **Add the AI cost to the report's projected cost**. It is off until you tick it.
2. Open a report and fill in its **Client** and, if you want it counted separately, its **Project name**.
3. Click **Preview & edit** or export the report. In **Materials and Projected Cost** you now see a row `AI analysis (N runs, T tokens)` with its cost. In a report with prices in US dollars, a row **Projected total incl. AI analysis** follows.

Good to know:

- The figure is read at the moment you preview or export, so it is always current. It is not saved in the report or in a bundle.
- A report with no client gets no AI line: it would otherwise collect every run made with **No customer**.
- A report with a blank project name counts every run of that customer that was made without a project, also the runs of other jobs. Give each job a project name to keep them apart.
- The AI cost is always in US dollars. In a report with another currency the line is printed in dollars and there is no combined total; a note says so.
- If some runs have no known cost, a note says how many; they are not in the figure.
- If the figure cannot be read, the preview or export still works and a notice says the AI cost is not in it.
- The **Projected total** row itself does not change, and the AI drafts quote that figure.

<a id="ai-usage-limits-of-this-version"></a>

### Limits of this version

- There is no budget, and no percent or amount left.
- There is no table of all customers at once; pick a customer to see its figures.
- Recorded runs cannot be moved to another customer. Pick the right customer before you run.
- Renaming a customer or a project starts the new name at zero; the runs already recorded keep the name they were made under.

> **Under the hood**
>
> Each AI run is one row in a table of the profile's database, with the provider's token counts, the model, the time, and the customer and project names as picked. The cost is worked out from the built-in price list each time a figure is shown. The report's figure is the total of the rows whose customer and project match the report's, over all time. It is added to a copy of the report handed to the preview and the export writers, never to the saved document.

<a id="ai-usage-see-also"></a>

### See also

- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Saving clients and claim details for reuse](#clients)

<sub>[Back to contents](#contents)</sub>

<a id="ai-tools"></a>

## AI tools: letting Chat and external agents read and change add-on data


The add-on tools let the **Chat** tab and, if you turn it on, an external agent such as Codex or Claude Code work with your add-on data. **What leaves your computer:** with Chat, everything a tool returns is sent to the AI provider you connected; with an external agent it goes to that agent and to the model provider behind it. On top of the flight tools, the add-on tools add picture names, notes, labels, report text, thermal figures and picture positions. Turn nothing on, and connect nothing, that you would not want those services to see.

<a id="ai-tools-before-you-start"></a>

### Before you start

- The desktop app, with at least one add-on license that is valid (Thermal, Photogrammetry or 360 Pano). Without a license no add-on tool is offered.
- For Chat: the Chat connection set up in the **Chat** tab.
- For an external agent: the local MCP server turned on in Settings, under **External agents**.

<a id="ai-tools-what-the-tools-can-do"></a>

### What the tools can do

**Reading** needs only a license. The tools you can ask about are:

- the shared library and one library item;
- thermal figures of a picture;
- a picture's annotations and its heat flow network;
- the saved reports, as a list and one at a time;
- the AI usage of a month.

Some things are never given to a tool: file paths, picture bytes, temperature matrices, your keys and licenses, your saved client contact details and the claim details of a report. A client name is given only while customer data encryption is off, or on and unlocked. Measured lengths, areas and volumes are not available: only the drawn shapes and the values you typed are. Thermal figures are computed at the moment you ask, from the file and from the boundary that is saved; temperatures you typed into the studio but did not save are not seen.

**Changing** is off until you switch it on:

- for Chat, with the **AI tools** checkbox in Settings;
- for an external agent, with the scope you give its connection when you make it.

With that, a tool can *propose* renaming a picture or changing its notes, annotation text, geometry, new annotations, take-off waste and price, report text (including photogrammetry figure captions), a 360's starting view, capture tags, heat flow network edits, and pairing, and it can propose removing annotations and take-offs. A tool proposes at most 25 changes per call.

<a id="ai-tools-steps"></a>

### Steps

1. Open **Settings** and find **AI tools**. Tick **Let Chat propose changes to add-on data (you confirm each change)** if you want Chat to be able to propose changes. It is off until you tick it.
2. For an external agent, open **External agents**, turn the server on, and tick **Allow this connection to propose changes to add-on data** before you press **Generate token**. A connection's scope cannot be changed later; revoke it and make a new one. A connection that has the scope shows a badge in the list.
3. Ask Chat, or your agent, for the change in your own words.
4. A dialog opens in Open DroneLog. It names who is asking and shows every change with the full value before and after. For drawings, it also shows the picture with the old and the new shapes.
5. Press **Apply** to store the changes, or **Don't apply** to refuse them. Focus starts on **Don't apply**; Escape counts as refusing. If you do nothing, the request expires and nothing changes.
6. After **Apply**, the studios show the new values. In Chat a **Changes applied** table lists what was stored.

<a id="ai-tools-example-renaming-a-picture"></a>

### Example: renaming a picture

You ask Chat to rename `DJI_0042.JPG` to `North wall 1`. The dialog shows one row: the picture, the field **name**, the old name and the new one. You press **Apply**, the library shows `North wall 1`, and Chat reports that the change was applied.

<a id="ai-tools-what-the-dialog-checks"></a>

### What the dialog checks

- Nothing is written before you press **Apply**, and only the changes shown are written.
- If the data changed since the request was made (you edited it in the meantime), the whole request is refused and nothing is stored. Ask again.
- If you have an unsaved edit, an unfinished drawing or a running AI draft in the picture or report concerned, the request is refused, nothing is stored, and the dialog says why. Finish or save that first, then ask again.
- A removal shows what else it affects and says **Removing cannot be fully undone here.** The dialog states what a record of the change can bring back.

<a id="ai-tools-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Chat can always read your add-on data while an add-on is licensed. The checkbox only decides whether it may *propose* changes.
- A tool never changes anything on its own: if no dialog appeared, nothing was changed.
- Only one dialog shows at a time; the others wait. A request that waits too long expires.
- To stop an agent, revoke its connection under **External agents**.
- Text in your pictures, notes and reports is data for the AI, never instructions; still, read each dialog before you press **Apply**.

> **Under the hood**
>
> Every proposal is checked against your license when the tool is listed and again when it runs. The dialog is the only way a change is stored: the model and the agent can only ask, and they cannot press **Apply**. The change is written in one step and is refused whole if any value differs from what the dialog showed.

<a id="ai-tools-see-also"></a>

### See also

- [AI usage: the usage bar, customers and projects, and the AI cost in reports](#ai-usage)
- [Encrypting customer data with a password](#customer-encryption)
- [Buying, activating and renewing an add-on license, and updating add-ons](#addon-license)

<sub>[Back to contents](#contents)</sub>

<a id="clients"></a>

## Saving clients and claim details for reuse


Enter a client once and pick it by its first letters in every later report, thermal or photogrammetry. Each report also carries its own claim details for insurance work: claim number, policy number, date of loss and adjuster. The Clients screen keeps the list: search, edit, delete, and import or export it as a CSV file.

<a id="clients-before-you-start"></a>

### Before you start

- The desktop app, with the Thermal or the Photogrammetry add-on enabled, and its studio open.
- A report builder open: **📄 Report ▼** → **Open report builder…**. The client fields are in section 1, just before the **Property Address** (Thermal) or **Site / Project Address** (Photogrammetry).

<a id="clients-picking-a-client"></a>

### Picking a client

1. Click into the **Client** field. While it has focus, a list of saved clients opens under it: with the field empty, your most recently updated clients.
2. Type the first letters of a name. The list shows up to 8 matches, each with the name and, smaller, the contact person and phone.
3. Move through the list with the Down and Up arrow keys and press Enter, or click a row. The name, **Contact person**, **Phone**, **E-mail** and **Client address** are filled from the saved client.
4. Press Esc to close the list without choosing; the field keeps what you typed.
5. For a new client, type the name and fill **Contact person**, **Phone**, **E-mail** and **Client address** yourself.
6. Click **Save client** at the right of the field. The button reads **Saving…** for a moment, then `Saved <name> to your clients.` shows. The button is greyed out while the name is blank or the saved clients cannot be read.
7. Below the person fields, fill the claim details if the job has them: **Claim number**, **Policy number**, **Date of loss** (a date picker) and **Adjuster**. All are optional.
8. Save and export the report as usual. In the exported report the client and claim rows print in Header Data, before the address row.

<a id="clients-the-clients-screen"></a>

### The Clients screen

1. Open it with **📄 Report ▼** → **Manage clients…** in either studio, or with **Manage…** beside the **Client** field of a report. The **👥 Clients** window opens over the studio or the builder, with the cursor in the `Search clients…` box.
2. Type in the search box to filter the list. Each row shows the name in bold, the contact person, phone, e-mail and the date it was last updated.
3. Click **+ New client**, or **Edit** on a row. A form opens above the list with **Name (required)**, **Contact person**, **Phone**, **E-mail**, **Address**, **Billing address**, **Tax / account no.** and **Notes (never printed)**.
4. Change what you need and click **Save**, or **Cancel** to close the form. Here a field you empty is saved empty.
5. Click **Delete** on a row to remove a client. The app asks `Delete <name>? Reports that already name this client keep their copy.`
6. Close the window with **✕** or Esc. With a changed form open, Esc first asks `Discard the unsaved client?`; with an unchanged form, Esc closes the form, then a second Esc closes the window.

With no clients yet the list reads `No saved clients yet. Save one from a report's Client field, add one here, or import a CSV file.`

<a id="clients-importing-and-exporting-a-csv-file"></a>

### Importing and exporting a CSV file

1. Click **Export CSV** and choose where to save `clients.csv`. Cancelling the dialog saves nothing.
2. Click **Import CSV…** and pick a file. The notice reads `Imported N new client(s), updated M, skipped K row(s) without a name.`

The first row of the file names the columns. Case, spaces, dashes and underscores are ignored, so `Billing address`, `billing_address` and `BillingAddress` are the same column:

| Column | Holds |
|---|---|
| `Name` | The client: company or person. Required |
| `Contact` | The person to reach |
| `Phone`, `Email`, `Address` | As in the report |
| `Billing address` | Kept in the record only |
| `Tax ID` (or `Account number`) | Kept in the record only |
| `Notes` | Kept in the record only |

Other columns are ignored. A row whose name matches a saved client updates it with its non-blank cells; other rows are added. A row without a name is skipped and counted. If the file has no `Name` column, names a column twice, has a broken quote, or a cell longer than 2,000 characters, nothing is imported and the notice reads `The file could not be read as a client list: <reason>.`

A value that starts with `=`, `+`, `-`, `@`, an apostrophe, a tab or a line break is exported with an apostrophe in front, so a spreadsheet does not read it as a formula: `+1 555 0100` is written as `'+1 555 0100`. The import removes that one apostrophe again, so an exported file imports unchanged.

<a id="clients-example-a-roof-claim-for-riverside-holdings"></a>

### Example: a roof claim for Riverside Holdings

1. Last month you saved `Riverside Holdings LLC` with its contact, phone, e-mail and address.
2. Open the Photogrammetry report builder and type `riv` in **Client**. `Riverside Holdings LLC` is first in the list.
3. Press Enter. **Contact person**, **Phone**, **E-mail** and **Client address** fill in.
4. Type `CLM-2026-0417` in **Claim number** and pick the date in **Date of loss**.
5. Export the PDF. Header Data shows the rows Client, Client Contact (contact, phone and e-mail joined by ` · `), Client Address (its lines joined by commas), Claim Number and Date of Loss. Rows left blank, here Policy Number and Adjuster, are not printed.

<a id="clients-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Choosing a client copies it into the report. Changing the phone in the report changes only that report; click **Save client** to update the saved client too.
- Typing over the name in the report detaches it from the saved client. **Save client** then saves it as the client of that name (a new one, unless that name is already saved) and leaves the old client as it was.
- Names count as the same when only case, accents or spacing differ: `Riverside Holdings LLC` and `riverside  holdings llc` are one client. The form refuses a second one with `A client with this name already exists: <name>.`
- In the preview you can edit the client's name, and the claim number, policy number and adjuster once they are filled in; the contact, address and date of loss rows are edited in the builder.
- If the screen shows `Saved clients could not be read.`, click **Retry**. If the list stays unreadable, **Replace the unreadable data** starts an empty list; the app asks first, and keeps a copy of the old value.

> **Under the hood**
>
> A report keeps its own copy of the client: name, contact person, phone, e-mail and address. Editing or deleting a saved client never changes an existing report, nor a saved report or an `.odlbundle` file. **Save client** updates the saved client with the non-blank fields of the report's copy: blank fields leave the saved values alone, and the billing address, tax / account number and notes are never touched. To empty a saved field, use the Clients screen.
>
> The billing address, tax / account number and notes stay in the saved record and never print in a report. The claim details belong to the report only. Neither the client nor the claim is filled from your branding or from your last report.
>
> The list is stored with your profile in the app's settings, so it is part of your backups. Search ranks a client whose name equals what you typed first, then names that start with it, then names with a word that starts with it, then names that contain it, then clients whose contact, e-mail, phone or address contains it. With an empty search box the screen lists every saved client by name; a search shows the 50 best matches. Every field holds at most 2,000 characters and the boxes stop there; a longer name typed into the preview is refused by **Save client** with `Name is longer than 2000 characters.`

<a id="clients-see-also"></a>

### See also

- [Branding your reports: logo, company and Part 107 number](#settings-branding)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)

<sub>[Back to contents](#contents)</sub>

<a id="customer-encryption"></a>

## Encrypting customer data with a password


Lock the saved client list, and the customer you picked in the AI usage bar, behind a password. Once it is on, nobody who opens the program or copies the profile's database file can read them without the password. You enter it once each time the program starts.

<a id="customer-encryption-before-you-start"></a>

### Before you start

- The desktop app, with the Thermal, Photogrammetry or 360 Pano add-on enabled. The switch is in **Settings**, in the section **Customer data encryption**, and it covers all of them: they share one client list. The 360 Pano studio uses no clients, so it shows no lock bar.
- Choose a password you will not lose. **Nobody can reset it or recover the data, Airwulf included.**

<a id="customer-encryption-what-is-and-is-not-encrypted"></a>

### What is and is not encrypted

| Encrypted | Not encrypted |
|---|---|
| The saved client list | Client details inside saved reports |
| The customer picked in the AI usage bar | The AI usage log (it keeps the customer name of every AI run) |
| Both, in this profile's database and in backups made from now on | Pictures, and everything you export: reports, claim packages, bundles and the clients CSV |

Earlier backups and the database file may still hold older unencrypted copies of the client list.

<a id="customer-encryption-switching-it-on"></a>

### Switching it on

1. Open **Settings** and find **Customer data encryption**.
2. Type the password in **Password** and again in **Repeat the password**. It needs at least 8 characters; a line under the fields says `Use at least 8 characters.` or `The passwords do not match.` until they are right.
3. Tick `I understand that a forgotten password means this data is lost`.
4. Click **Encrypt customer data**. The message `Customer data is now encrypted.` shows, and the section now reads `Encrypted. Unlocked until you close the app, log out or switch profiles.`

<a id="customer-encryption-unlocking-at-each-start"></a>

### Unlocking at each start

1. After the program starts, the client list is locked. Above the Thermal and Photogrammetry studios an amber bar says `Customer data is encrypted and locked: saved clients are not available.` Type the password there and click **Unlock**, or press Enter.
2. The Clients screen shows `Saved clients are encrypted and locked.` with the same password field. The client pickers in the report builder and in the side-by-side, volume ticket and orthomosaic dialogs say `Saved clients are locked. Enter the password to pick one.` and carry their own password field, so you do not have to close the dialog. You can unlock from any of these, or from the section in Settings.
3. A wrong password shows `That password is not correct.` and nothing changes.
4. The data stays unlocked until you close the program, switch profiles, or log out of the profile and back in: it then locks again.

<a id="customer-encryption-switching-it-off"></a>

### Switching it off

1. Unlock the data first. In **Customer data encryption** click **Turn off encryption**.
2. Type the password in the field that appears and click **Turn off**, then confirm. The message `Encryption is off. The customer data is stored unencrypted.` shows. Click **Cancel** instead to close the field without turning anything off.

<a id="customer-encryption-a-forgotten-password"></a>

### A forgotten password

There is no way back to the data. What you can do is start again:

1. Open **Customer data encryption** while the data is locked. Under `Forgot the password?` click **Erase the encrypted customer data** and confirm.
2. The encrypted client list and the encrypted picked customer are deleted for good, and the encryption is off. You can switch it on again with a new password.

<a id="customer-encryption-a-value-that-cannot-be-decrypted"></a>

### A value that cannot be decrypted

If the list or the picked customer was encrypted with a password other than the current one (for example after you restored a backup), unlock the data first: the section then lists it, for example `The saved client list cannot be decrypted with the current password.` The Clients screen says the same and points here. Click **Discard** beside the line and confirm to remove that value. It cannot be undone, and it never removes data the current password opens.

While such a value is stored, **Turn off encryption** and **Encrypt customer data** are refused with a message that asks you to discard it first.

<a id="customer-encryption-a-damaged-encryption-record"></a>

### A damaged encryption record

If the encryption record of the profile is damaged, the section says `The encryption record of this profile is damaged, so the encrypted customer data cannot be opened.` with **Retry** and **Erase the encrypted customer data**. Erasing works as in the forgotten-password case above: the encrypted client list and the picked customer are deleted for good.

<a id="customer-encryption-backups"></a>

### Backups

A backup made while encryption is on holds the data encrypted. A restored backup needs the password that was in force when it was made. Backups made before you switched it on stay unencrypted; restoring one brings its unencrypted client list back. If the data is unlocked, the program encrypts it again straight after the restore (if that fails, the restore message says `The restored saved clients could not be encrypted yet; unlock the customer data again to encrypt them`); if it is locked, at the next unlock.

A backup encrypted with another password than the current one leaves your saved clients as they are: they are not replaced by the backup's, so no list is lost, and the restore message ends with `Saved clients were kept as they were: the backup's were encrypted with another password`. To get the backup's list, turn encryption off and restore again (if a value that cannot be decrypted is listed, discard it first, or turning encryption off is refused); the backup's list then needs the backup's password.

<a id="customer-encryption-ai-runs-made-while-locked"></a>

### AI runs made while locked

While the data is locked the AI usage bar reads `Customer data is locked: AI runs are recorded without a customer`. Runs still work; each is recorded with no customer, so it does not count toward any customer's figures. Unlock first if a run belongs to a customer.

If the picked customer was encrypted with another password, the bar instead reads `The picked customer cannot be decrypted with the current password: AI runs are recorded without a customer. Discard it in Settings, Customer data encryption.` Use **Discard** there, as described above.

<a id="customer-encryption-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Keep the password in a password manager or somewhere safe. The program never stores it.
- An older version of the program reports an encrypted client list as unreadable. Do not click its **Replace the unreadable data** button: install the current version instead.
- Changing the password means turning encryption off and on again.

> **Under the hood**
>
> The values are encrypted with AES-256-GCM. The key is derived from the password with Argon2id (64 MiB of memory, 3 passes), separately for each profile, and is kept in memory only while the data is unlocked. The password itself is never stored.

<a id="customer-encryption-see-also"></a>

### See also

- [Saving clients and claim details for reuse](#clients)
- [AI usage: the usage bar, customers and projects, and the AI cost in reports](#ai-usage)

<sub>[Back to contents](#contents)</sub>


---

# Add-ons

<a id="addon-license"></a>

## Buying, activating and renewing an add-on license, and updating add-ons


The Thermal Analysis Studio, the Photogrammetry add-on and the 360 Panorama Studio each run on a license: a subscription per add-on, which you can cancel at any time. Thermal and Photogrammetry cost $7.99 a month or $75 a year each; the 360 Panorama Studio costs $4.99 a month or $50 a year (in this version its Buy buttons still read $7.99 and $75; the purchase page shows the real price before you pay). The add-on itself is free to download and install; the license switches its functions on.

<a id="addon-license-before-you-start"></a>

### Before you start

- You need the desktop app for Windows, installed per user from Open DroneLog's own GitHub setup (`.exe`). The all-users (MSI) install is not supported by the add-on installers.
- Install the add-on first: open **Settings** (the gear at the top of the sidebar) and click **Open Add-ons**, then **Download installer…** for the add-on, run it, and click **↻ Refresh**. Until it has a license, the add-on's tab shows a lock panel headed "… needs a license" instead of the studio.
- Activating a key needs an internet connection once. A computer that never goes online uses a license file instead (see [Offline computers](#addon-license-offline-computers)).

<a id="addon-license-buying-a-license"></a>

### Buying a license

1. On the lock panel, or in the add-on's row of the **🧩 Add-ons** window, click **Buy monthly ($7.99)** or **Buy yearly ($75)**. The purchase page opens in your browser.
2. If you already have a key for another add-on, paste it into the "Already a customer?" field. All your subscriptions then stay on one account and one customer portal. The field is optional.
3. Click "Continue to payment" and pay by card.
4. The thank-you page shows your license key with a "Copy" button, and a "Download license file" button. Copy the key, and bookmark the page: it is the way back to your key if you lose it.

<a id="addon-license-activating-a-key"></a>

### Activating a key

1. Open the add-on's tab. The lock panel shows the state line, for example `No license`.
2. Click **Enter license key…**. A box appears.
3. Paste the key and click **Activate** (or press Enter). The key is checked online.
4. When it is accepted, the lock panel disappears and the studio opens. The add-on's row in the **🧩 Add-ons** window reads `Licensed until <date>`.
5. If it is not accepted, a red line under the buttons says why, for example `This key is not known.` or `Could not reach the licensing server (…). Check the internet connection, or import a license file.`

The other route is the add-on installer: its License key page asks you to paste the key from the purchase page. Leave it empty to enter the key later. A key entered there is activated the next time Open DroneLog starts. If the licensing service refuses it, the lock panel and the **🧩 Add-ons** window show `Rejected: <code>` with the key partly hidden; click **Retry** to try it again once the problem is fixed.

<a id="addon-license-offline-computers"></a>

### Offline computers

1. On any computer with internet, open the license-file page of the licensing site (the thank-you page links it, and the renewal bar names its address), paste your key and download the `.lic` file.
2. Carry the file over, for example on a USB stick.
3. On the offline computer, click **Import license file…** on the lock panel or in the **🧩 Add-ons** window and pick the file. The studio opens.

A license file lasts at most 90 days, and never more than three days past the paid period. Before it runs out, the renewal bar tells you to fetch a new one. When a file has run out, the state line reads `License file expired on <date>: refresh or import a new file`.

<a id="addon-license-licenses-tied-to-this-computer"></a>

### Licenses tied to this computer

Some licenses are tied to the computer they were activated on. After you activate one, the lock panel and the add-on's row in the **🧩 Add-ons** window work as usual. If the same license is used on another computer, or the licensing service no longer lists this computer for it, the state line reads `Not active on this computer: …` followed by the reason, for example that the limit of computers is reached. The add-on stays locked until that is fixed.

- A copied license file does not carry the license to a second computer. Copying the `.lic` file (and its key) to another PC works until that PC first refreshes the license, at the latest about 30 days later; then the licensing service refuses it there if the limit is already used.
- A computer's place is freed in one of two ways: click **Deactivate this PC** on the old computer (see below), or ask the issuer of the license to free it in the licensing dashboard. This is also the way to move a license when a computer is lost.
- Computers cloned from one disk image without preparing Windows for cloning (sysprep) look like one computer to the licensing service and share a single place.

Click **Refresh** after the place is freed; the state line updates and the studio opens.

<a id="addon-license-deactivating-this-computer"></a>

### Deactivating this computer

Use this to move a license to another computer, or before you sell or wipe this one.

1. Open the add-on's tab (the lock panel) or the **🧩 Add-ons** window. The button **Deactivate this PC** appears only for a license that is registered to this computer.
2. Click **Deactivate this PC**. A confirmation names the add-ons the license covers and shows the full key.
3. Click **Copy** to keep the key: you need it to activate again.
4. Click **Deactivate** to go ahead, or **Cancel** to leave everything as it is.
5. The add-ons the license covers lock at once and this computer's place is freed. To use the license here again, click **Enter license key…** and paste the key, or **Import license file…**.

If the licensing service cannot be reached, the message says so and nothing is removed yet. The add-ons the license covers stay locked and the state line reads `Deactivating this computer… Click Refresh when the computer is online to finish.`; when you are online again, click **Refresh** (or restart Open DroneLog) to finish the deactivation. If the key file was already missing from this computer, the license files are still removed, and the message says that the licensing service still lists this computer, so the issuer has to free it.

<a id="addon-license-renewing"></a>

### Renewing

Subscriptions renew by themselves. On a computer that goes online, the app refreshes its license in the background about once a day and simply picks up the new paid period; no warning appears.

A warning bar appears above the studio, and as a line in the add-on's row, only when a license is going to lapse: 5 days, 3 days and on the last day before the deadline. Close it with **✕**; it comes back at the next of those three points.

| Bar | Why | What to do |
|---|---|---|
| `Your <add-on> license expires in N days.` (or `today`) | The subscription was cancelled or a payment failed | **Manage subscription** to fix the payment or resume, or **Buy again** |
| `This computer could not refresh the <add-on> license file; …` | The computer has not refreshed for more than a day and a half | Go online and click **Refresh**, or get a new file and click **Import license file…** |

**Manage subscription** opens the customer portal page in the browser. Paste your key there to see your subscription, update the card, view invoices or cancel. A cancellation takes effect at the end of the paid period.

When a license has lapsed, the lock panel returns and reads `Expired on <date>`. Your pictures, annotations, measurements and reports stay in Open DroneLog and open again as soon as the license is valid; only the add-on's own functions (importing, analysing, saving reports) are locked. The rest of Open DroneLog keeps working.

<a id="addon-license-updating-add-ons"></a>

### Updating add-ons

1. Open the **🧩 Add-ons** window and click **Check for updates** (it reads **Checking…** while it looks). The window also shows the last check result when you open it, and the app checks by itself about once a day.
2. When a newer version exists, the add-on's row shows a button `Update to v<version> (<size> MB)`. Click it.
3. A progress bar fills while the installer downloads and is checked.
4. The row reads `Restarting to apply…`. Open DroneLog closes, the update installs without questions, and Open DroneLog starts again.

If the row reads `Update v<version> cannot be installed on this computer yet`, the update was built for a different Open DroneLog than the one running; the line names the versions involved. A failed check shows `Update check failed: …` in the row. For a computer without internet, download the installer by hand from the public releases page, https://github.com/AirwulfLLC/open-dronelog-addons/releases, and run it there.

<a id="addon-license-after-an-open-dronelog-upgrade"></a>

### After an Open DroneLog upgrade

The add-ons run inside an Airwulf build of Open DroneLog that their installer puts in place. If you later install a newer Open DroneLog from GitHub, its installer puts the original program back: Open DroneLog starts without the add-ons and without the **Add-ons** section in Settings.

1. Download the current add-on installer from the releases page above (an older one refuses to install over a newer Open DroneLog and says so).
2. Run it. You do not need to enter the key again.
3. Start Open DroneLog. The add-on tabs are back.

Nothing is lost: your licenses, pictures, reports and settings stay in place across the upgrade.

<a id="addon-license-removing-an-add-on"></a>

### Removing an add-on

1. In the **🧩 Add-ons** window, click **Remove** on the add-on's row and confirm. Your imported data is kept.
2. If it is the last add-on installed, Open DroneLog restarts to restore the original program. You are back on the plain Open DroneLog you first installed. If another add-on remains, the Airwulf build stays.
3. If the restore could not finish, the row reads `Removing <add-on> failed: <reason>`. Click **Retry** to try again, or **Keep add-on** to cancel the removal and keep using it.

Your licenses stay on the computer, so a reinstall later finds them.

<a id="addon-license-example-one-office-pc-online-one-field-laptop-offline"></a>

### Example: one office PC online, one field laptop offline

A roofing inspector buys a yearly Thermal Analysis Studio license for $75 and copies the key from the thank-you page.

- *Office PC:* runs `OpenDroneLog-Thermal-Addon_<version>_x64-setup.exe` and pastes the key on the License key page. At the next start the row reads `Licensed until <date>`, a year ahead plus three days. The PC refreshes daily, so the renewal next year needs nothing.
- *Field laptop, never online:* on the office PC the inspector downloads the `.lic` file from the license-file page, carries it over on a USB stick and clicks **Import license file…**. The file covers 90 days. About 85 days later a bar reads `This computer could not refresh the Thermal Analysis Studio license file; …`, so they download a fresh file and import it again.
- A year later the inspector adds Photogrammetry and pastes the first key into "Already a customer?", so **Manage subscription** shows both subscriptions together.

<a id="addon-license-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Keep the key. It is the only thing you need to activate again, download a license file or open the portal. A lost key can be recovered through the licensing site's recovery page with your payment receipt.
- `Clock problem: the computer's clock moved back; connect once to refresh` means the date was set back by more than a day. Correct the date, go online and click **Refresh**.
- `License no longer valid (<code>)` means the licensing service no longer accepts the key (a suspended or withdrawn license). Contact support if you did not expect it.
- A license is per add-on: a Thermal key does not open Photogrammetry.
- Disabling an add-on (untick **Enabled**) only hides its tab; it does not cancel the subscription. Cancel with **Manage subscription**.

> **Under the hood**
> A license file is a certificate signed by the licensing service with an Ed25519 key. Open DroneLog checks the signature and both dates on this computer at every licensed action, without internet; the key proves the purchase and lets the app fetch a fresh file (online refreshes give 30-day files, the license-file page up to 90 days). A clock guard remembers the latest time the app has seen and refuses licenses when the clock is more than 24 h behind it, until an online refresh succeeds. Licenses live in `%APPDATA%\com.drone-logbook\licenses`. The add-on installer saves a copy of the original `open-dronelog.exe`, swaps the Airwulf build in through a step-by-step sequence that a crash or power cut can always recover from, and removing the last add-on puts the copy back.

<a id="addon-license-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [360 Panorama Studio: getting started, importing, sets and marking up photos](#panorama-start)

<sub>[Back to contents](#contents)</sub>
