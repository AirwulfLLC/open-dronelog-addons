# Open DroneLog Add-ons: Help Guide

This file collects every help guide built into the Open DroneLog add-ons (the **Thermal Analysis Studio** and **Photogrammetry**) in one place. Inside the program, the same guides open from the **?** buttons and the Help panel.

New to the add-ons? Install them first with the step-by-step guide in the [README](README.md), then start with [Thermal Studio: getting started](#thermal-start) or [Photogrammetry: getting started](#photo-start).

> **Version:** written for add-ons 1.0.0 on Open DroneLog 3.3.2. Two guides, [Branding your reports](#settings-branding) and [Saving clients](#clients), describe features coming in the next add-on update; they are marked where they appear.

> **Source and license:** these guides are copied word for word from the in-app help of the Airwulf build of Open DroneLog (`src/help/content`), with only the links between guides changed so they work in one file. The Airwulf build is based on [Open DroneLog](https://github.com/arpanghosh8453/open-dronelog) by Arpan Ghosh, which is licensed under the [GNU Affero General Public License v3.0](https://github.com/arpanghosh8453/open-dronelog/blob/main/LICENSE) (AGPL-3.0), and this help text is distributed under the same license. The complete source of the program, help included, is attached to every [add-on release](https://github.com/AirwulfLLC/open-dronelog-addons/releases).

For the main Open DroneLog program (flight logs, maps, charts, batteries), see the original project's [user manual](https://github.com/arpanghosh8453/open-dronelog/blob/main/docs/manual.md).

## Contents


**Thermal Studio**

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Heat flow network: nodes, conductors, solving](#thermal-network)
- [Vegetation indices from multispectral orthomosaics](#thermal-vegetation)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)

**Photogrammetry**

- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)

**Pictures: annotating and measuring**

- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Giving a picture a scale: references, altitude and pitch, the Scale strip, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)
- [Positions, ground control points and georeferenced orthomosaics](#measure-geo)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)

**Settings**

- [Editing the material catalogue: presets, units, packages, waste, prices](#settings-material-presets)
- [Branding your reports: logo, company and Part 107 number](#settings-branding) *(next update)*
- [Saving clients and claim details for reuse](#clients) *(next update)*

**Add-ons**

- [Buying, activating and renewing an add-on license, and updating add-ons](#addon-license)


---

# Thermal Studio

<a id="thermal-start"></a>

## Thermal Studio: getting started, importing, the library


The Thermal Studio turns radiometric drone pictures into a temperature for every pixel. You read the temperatures, isolate a range, find hot and cold spots, model heat flow, and put the findings into an inspection report. This topic covers switching the studio on, bringing pictures in, and managing the library.

<a id="thermal-start-before-you-start"></a>

### Before you start

- You need the desktop app for Windows. The web and Android versions have no add-ons, so they have no Thermal tab; their Add-ons window reads "Add-ons are available in the desktop app only."
- You need the Thermal add-on installed and enabled. Steps 1 to 4 below do that once.
- For temperatures you need radiometric files: a DJI or FLIR-format R-JPEG (`.jpg`), an Autel 640T radiometric TIFF, or a per-pixel temperature CSV. Ordinary photos and videos can be imported too, but they carry no temperatures.

<a id="thermal-start-steps"></a>

### Steps

1. Click **Add-ons** in the sidebar. The **🧩 Add-ons** window lists the **Thermal Analysis Studio**.
2. If it reads **Not installed**, click **Download installer…**, run `OpenDroneLog-Thermal-Addon_<version>_x64-setup.exe`, then click **↻ Refresh** in the window.
3. Make sure **Enabled** is ticked. A **Thermal** tab appears in the sidebar.
4. Open the **Thermal** tab. The top bar shows **🌡️ Thermal Studio** and two badges:
  - **DJI Thermal SDK ready** (green): DJI R-JPEGs can be measured. **DJI SDK unavailable** (red) means the SDK runtime from the add-on is missing; hover the badge to read why. Run the add-on installer again.
  - **FLIR · Skydio · Autel built in** (blue): FLIR-format R-JPEGs (Teledyne FLIR, Skydio X10, Autel 640R), Autel 640T TIFFs and temperature CSVs are read without any SDK.
5. Look at the layout:
  - Left: the library, headed **Assets (N)**.
  - Centre, top: the toolbar with the annotation tools, **📝 Note**, the **Measure** group and **🧭 Scale**. Under it the Scale strip opens when you click **🧭 Scale**.
  - Centre: the viewer with the picture, the zoom strip (**Fit**), the cursor readout and the min and max markers. Under it the info strip.
  - Right: the **Analysis** panel with its sections (statistics, palette, isotherm, measurement parameters, variance analysis, heat flow).
  - Top right: **+ Import photos / videos**, **🌡 Radiometric file…** and **📄 Report**.

<a id="thermal-start-importing"></a>

### Importing

1. Click **+ Import photos / videos** (or **Import photos / videos** in the empty viewer). The file dialog opens.
2. Pick one or more files and confirm. While they are imported the button reads **Importing…**. Accepted: pictures `.jpg`, `.jpeg`, `.png`; videos `.mp4`, `.mov`, `.avi`; Metashape exports `.tif`, `.tiff`, `.pdf`, `.xml`, `.csv`, `.las`, `.laz`, `.ply`, `.obj`, `.kml`, `.kmz`.
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
2. Rename a picture: double-click its name, or click **✏️**. Type the new name and press Enter (Esc cancels). The extension is kept and shown beside the box; the name is the one printed in reports, the stored file keeps its own name.
3. Delete a picture: click **🗑** on the row, or **🗑 Delete** in the info strip. Confirm `Delete "<name>" from the thermal library? The file, its annotations and measurements are removed.`
4. Read the info strip under the picture: the file name, the camera model, for FLIR files `S/N …` and `lens …`, how a TIFF or CSV was read, the format in green (or `Not radiometric`), `📍` with the GPS position, and the capture time.
5. Add a note: click **📝 Note** in the toolbar. Type the observed condition, context or follow-up into the box. The note is saved with the picture, printed under it in reports, and the button shows ` ●` while a note exists.

The row icons tell you the kind: 🌡️ radiometric, 🖼️ plain picture, 🎬 video, 🗺️ Metashape raster, 📄 Metashape document.

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
- Deleting removes the annotations, measurements, note and heat-flow network of that picture as well. There is no undo.

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
6. Open **Palette & Scale** and click a palette: **Iron Red**, **White Hot**, **Black Hot**, **Rainbow**, **Arctic** or **Medical**. The colour bar under the buttons shows the palette with its low and high end.
7. Set the scale. **Auto** spreads the palette from the picture's min to its max. To fix it, type a low and a high value into the two boxes beside **Auto** (the greyed placeholders show the auto values). Pixels below the low end take the coldest colour, pixels above the high end the hottest. Click **Auto** to go back.
8. Change the unit if you need it: open Settings, then **Units**, and set **Temperature** to °C or °F. Every temperature in the panel, the readout, the markers and the reports follows; typed scale values are read in the unit shown.

<a id="thermal-analysis-measurement-parameters"></a>

### Measurement parameters

These are the inputs of the camera's temperature model. Change them when the camera's defaults do not match the surface you inspect.

1. Check that the picture is a DJI or FLIR-format R-JPEG. Autel TIFFs, temperature CSVs and vegetation indices hold final values, so the section is absent for them.
2. Click **Measurement Parameters** to open it (it starts closed).
3. Type the **Emissivity** of the surface, between 0.1 and 1 in steps of 0.01. The box starts with the value stored in the file, or the value you last typed in this session.
4. Type the camera-to-object **Distance (m)**, or **Distance (ft)** when your distance unit is imperial. You can write `12`, `12 m` or `40 ft`.
5. Read **Humidity:** and **Reflection:** under the boxes. They are the values stored in the file and cannot be changed here.
6. Click **Re-measure**. The temperatures are computed again; the statistics, histogram, markers and readout update, and any anomaly results are cleared because they belonged to the old temperatures.

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
- **Auto** stretches the palette over the whole picture. A hot chimney or the sun on a skylight then squeezes the wall into a few colours and hides small differences. Set the scale by hand around the temperatures of the surface you inspect.
- Emissivity and distance typed here stay in force for the next pictures you open in this session; they are not saved with the picture. They also apply to the anomaly detection and to every picture pair of an exported thermal report. Check the box values when you change to a different surface.
- **Std Dev** and **Δ (max−min)** are differences. In °F they are multiplied by 9/5 without the 32 offset, so do not convert them like temperatures.

> **Under the hood**
> DJI R-JPEGs are measured by the DJI Thermal SDK (`dirp_measure_ex`), which applies the emissivity, distance, humidity and reflected temperature; FLIR-format files go through a native Planck model of the raw counts with the camera's calibration constants, plus the same object parameters and the atmosphere between camera and object. The values are refused outside the model's range (emissivity 0.1 to 1). TIFF and CSV imports are stored as final °C values. The statistics are computed over every valid pixel: the mean and the standard deviation over all of them, the median from every n-th pixel with n = ⌊pixels ÷ 65,536⌋ (65,536 to 131,071 samples; pictures smaller than that use every pixel), the histogram in 96 equal bins from min to max. The temperatures are kept in °C and metres internally; only what is shown or typed follows Settings → Units. For the accuracy see the camera's data sheet (and expect worse when the emissivity or the reflected temperature are wrong).

<a id="thermal-analysis-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Isolating a temperature range (isotherm)](#thermal-isotherm)
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
- Highlight and Solo change only the display. The statistics boxes above still describe the whole picture.
- The limits follow Settings → Units → Temperature. In °F the slider steps are still 0.1 of the shown unit.

> **Under the hood**
> A pixel is in range when Low ≤ T ≤ High (both ends included). The count, the min, the max and the mean are computed over those pixels only; the share is count ÷ (width × height) × 100. In Highlight mode an out-of-range pixel gets a grey level of 30 + 120 × its position on the colour scale (0 to 1), so warmer pixels stay lighter grey; in Solo mode it is drawn near black. The histogram has 96 bins; a bin is coloured when its centre lies in the range. When the anomaly search is restricted, the baseline (median) and σ are still those of the whole picture: only the pixels that may form a region are limited to the range. Nothing is saved: the range lives only while the picture is selected.

<a id="thermal-isotherm-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Reading temperatures: statistics, palette and scale, emissivity and distance](#thermal-analysis)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Vegetation indices from multispectral orthomosaics](#thermal-vegetation)

<sub>[Back to contents](#contents)</sub>

<a id="thermal-anomalies"></a>

## AI variance analysis, the AI narrative, and the provider key


**AI Variance Analysis** finds the regions of a picture that are clearly hotter or colder than the rest, grades them and suggests what they may be. The optional AI narrative turns the measured data into written findings, using an AI provider and a key you set in Settings.

<a id="thermal-anomalies-before-you-start"></a>

### Before you start

- You are in the **Thermal** tab of the desktop app with the Thermal add-on enabled.
- A still radiometric picture (or a vegetation index) is selected and its **Temperature Statistics** (**Index Statistics** for an index) are filled in.
- For the narrative only: an internet connection and an API key from Claude (Anthropic), OpenAI or Google Gemini, saved as described in [AI provider keys](#thermal-anomalies-ai-provider-keys).

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
2. Look at the subheading `AI Narrative (Claude)` (or `OpenAI`, `Gemini`): it names the provider chosen in Settings. Without a key the section shows only "Pick an AI provider and add its API key in Settings (below the DJI API key) to generate narrative findings from the image and measured data."
3. Click the purple button. It reads **Generate AI narrative (runs on image + stats)** before a detection, **Generate AI narrative of findings** after one.
4. Wait: the button reads **Analyzing with AI… (can take a minute)**. The text appears below with a summary, findings by `#` number with their ΔT, and prioritised recommendations.
5. Click **Copy** to put the text on the clipboard (it changes to **✓ Copied**), or **Regenerate narrative** for a new version.
6. Check every statement against the picture before you use it. Selecting another picture discards the text.

<a id="thermal-anomalies-ai-provider-keys"></a>

### AI provider keys

1. Open Settings and scroll to **AI Thermal Analysis** (below the DJI API key).
2. Pick the **Provider**: `Claude (Anthropic)`, `OpenAI (GPT)` or `Google Gemini`. A provider that already has a key shows ` ✓`.
3. Click **Get a key** to open the provider's key page in your browser, create a key there and copy it.
4. Paste it into the box (the placeholder shows the key's shape: `sk-ant-...`, `sk-...` or `AIza...`) and click **Save API Key**. The toast reads "AI analysis API key saved" and the status reads "API key configured".
5. To replace a key, paste the new one and click **Update API Key**. To remove it, click the **Personal** badge (it turns into **Remove** on hover).

Keys are kept per profile and per provider: switching the provider keeps each key, and another profile needs its own. The same key powers the `✨ AI draft` checkboxes in the report builders.

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
- Results are not saved with the picture. Run the detection again after reopening a picture or after **Re-measure**, which clears them.
- An AI key costs money per request at the provider. Generating a narrative for every picture of a large survey adds up.
- The narrative can be wrong. It is a draft for a qualified thermographer to check, not a diagnosis.

> **Under the hood**
> Every valid pixel gets z = (T − baseline) ÷ σ, where the baseline is the median of the picture and σ its standard deviation. Pixels with z ≥ +threshold are hot, z ≤ −threshold cold; 4-connected neighbours of the same kind form a region, and regions smaller than the minimum are dropped. ΔT is the region's mean minus the baseline. Severity: high when |ΔT| ≥ 8 °C or |ΔT| ≥ 6σ, medium when |ΔT| ≥ 4 °C or ≥ 3.5σ, else low. Classification, hot: |ΔT| ≥ 10 °C on fewer than 900 px is an electrical fault, an elongated box (width to height above 3 or below 1/3) thermal bridging, |ΔT| ≥ 5 °C HVAC leakage, else an insulation void; cold: elongated is air infiltration, |ΔT| ≥ 6 °C moisture intrusion, else missing insulation. Regions are ranked by |ΔT| × (1 + ln area) and at most 24 are kept. The detection runs on your computer. The narrative sends the picture file, its file name, the statistics, the measurement parameters, the anomalies and any heat-flow results to the chosen provider (`claude-opus-5`, `gpt-5` or `gemini-2.5-pro`); nothing else leaves the machine, and nothing is sent until you click. Report drafts send only the text facts of the report, no picture. Keys are stored in the profile's local database and sent only to their provider.

<a id="thermal-anomalies-see-also"></a>

### See also

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
- For take-offs in the report, add materials in the Scale strip; see [Material take-offs](#materials-takeoff).
- For AI drafts, add a provider key in Settings → **AI Thermal Analysis**. Everything else works without it.

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
| 1 | Header Data & Administrative Information | Property, date, site, inspector and credentials, camera; **📷 Fill camera from imagery** reads the camera from the pictures. Holds the **Executive summary**. |
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

The materials section works as described in [Material take-offs: In the report](#materials-takeoff-in-the-report). Its From column names the pair and the picture, such as `Pair 2 (thermal)` or `Pair 2 (visual)`, because the two pictures of a pair are separate figures.

<a id="thermal-report-ai-drafts"></a>

### AI drafts

Four sections carry a **✨ AI draft** checkbox in their heading: Header Data (the executive summary), Anomalies & Findings, Action Plan & Repair Prioritization, and Follow-Up & Re-inspection.

1. Enter the facts first: conditions, anomalies, inventory, materials.
2. Tick **✨ AI draft**. The heading shows `writing…`, then the notice `AI draft applied to “…” — review and edit it; untick to restore your own text.` For anomalies, each entry's finding and recommendation is filled by its ID.
3. Read and edit the draft. It is your report.
4. Click **↻** next to the box to write a new draft, or untick the box to get your own text back.

Without a key the box is greyed out, and its tooltip reads `Configure an AI API key in Settings (AI Thermal Analysis) to enable AI drafting`. **Save** waits while a draft is being written.

<a id="thermal-report-preview-export-and-bundles"></a>

### Preview, export and bundles

1. Click **Preview & edit**. The **Edit** tab shows the report text: click any text to change it in place. The **PDF** tab shows the exported PDF. **Refresh** re-renders after you change pictures or sections.
2. Export with the preview's own export buttons (PDF, Word, RTF), or with **Export ▼** in the builder.
3. Click **Export Bundle** to save the whole inspection as one `.odlbundle` file. `Inspection bundle exported.` confirms it.
4. On another machine or profile, open **📄 Report ▼** → **Import inspection bundle…** and pick the file. A message reads `Bundle imported: N new asset(s), M already present, report "…"`, sometimes followed by `, N archived flight(s) in the bundle file` (the flights stay archived in the file; they are not added to your logbook). Pictures already in the library are not copied twice, and the report appears under **Saved reports** with its links intact.

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
- Export a bundle, not just a PDF, when someone else will continue the inspection.

> **Under the hood**
>
> An AI draft sends only the facts entered in the report (conditions, flights, anomalies, inventory, the material count and projected total, and the waste allowance when prices exist) to the provider chosen in Settings, never the pictures. A bundle is a gzipped tar holding the report, every asset it refers to (thermal media and Metashape files with their previews), the annotations, the heat-flow networks and the linked flights' full telemetry; assets are matched by content hash on import. Every report names its publisher and the workflow under the title, "Generated by \<publisher\> · \<workflow\>": the publisher is the company saved under Settings → **Branding**, and "Airwulf, LLC" until one is saved.

<a id="thermal-report-see-also"></a>

### See also

- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [AI variance analysis, the AI narrative, and the provider key](#thermal-anomalies)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Saving clients and claim details for reuse](#clients)

<sub>[Back to contents](#contents)</sub>


---

# Photogrammetry

<a id="photo-start"></a>

## Photogrammetry: getting started, importing, the library and Metashape deliverables


The Photogrammetry tab collects the imagery and the Agisoft Metashape outputs of a survey and turns them into a survey report. You import photos, videos and Metashape deliverables into one library, annotate and measure the pictures, and queue the ones you want as report figures. This topic covers setting up, importing and the library.

<a id="photo-start-before-you-start"></a>

### Before you start

- Use the desktop app. The library stores media in your local profile, so the tab is not available in the web version.
- Install the add-on: click **Add-ons** next to Settings, click **Download installer…** for Photogrammetry, run the installer, then click **↻ Refresh**. The add-on's badge reads `Enabled · v<version>` and the Photogrammetry tab appears in the sidebar.
- To hide the tab without removing anything, untick **Enabled** in the same screen.
- Have the survey photos or videos at hand, and the Metashape exports you want in the report: orthomosaic and DEM GeoTIFFs, the processing report PDF, the camera XML, point clouds.

<a id="photo-start-steps"></a>

### Steps

1. Open the Photogrammetry tab. The top bar shows the 📷 Photogrammetry title; the library is on the left, the viewer in the middle and the report queue on the right.
2. Click **+ Import photos / videos** and pick the files. Or drag them onto the window: the overlay reads `Drop photos, videos or Metashape exports to import`.
3. Wait while the button reads `Importing…`. The new items appear in the library.
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

The library lists everything you imported, with its count in the header (`Library (N)`).

1. Click **All**, **Photos**, **Videos** or **Metashape** to filter the list.
2. Read the rows. The icon says what it is: 📷 photo, 🎬 video, 🗺️ Metashape image, 📄 Metashape document. The line below reads `Photo`, `Video` or the Metashape kind. A queued item shows `In report`, or `In report ×N` when it is queued more than once.
3. Tick the checkboxes of several photos, videos or orthomosaics to add them in one go. Documents have no checkbox.
4. Hover a row for its buttons: **+** adds it to the report, **✏️** renames it, **🗑** deletes it.
5. To rename, double-click the name or click **✏️**, type, and press Enter (Esc cancels). The name is printed in the report; the stored file keeps its name.
6. To delete, click **🗑** and confirm. The file, its annotations and its measurements are removed, and it leaves the report queue. For a Metashape file the question warns that it is shared with the Thermal Studio, so it goes there too.
7. Click a document (a processing report, a camera file, a point cloud) to see its card: size, cameras, markers, coordinate system and format when known, and **Open in default application**. A document is not a figure, but it travels in the report's bundle when you tick it as a deliverable in the report builder.

The Metashape files are shared with the Thermal Studio: an orthomosaic imported here can be analysed and annotated there, and the other way round. Photos and videos you import here stay in the Photogrammetry library.

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
5. Open the orthomosaic in the viewer. The DSM overlaps it in the same coordinate system and its name says DSM, so it pairs automatically and the Scale strip can measure slopes and volumes.

<a id="photo-start-tips-and-common-mistakes"></a>

### Tips and common mistakes

- Name the DEM so it pairs: a one-band GeoTIFF that overlaps the orthomosaic in the same coordinate system pairs automatically only when it has one numeric band and its name has the word DEM, DSM, DTM, elev, elevation, height or heights.
- Documents cannot be figures. They have no checkbox, and with a document selected **+ Add to report** is greyed out (tooltip `Documents cannot be report figures — photos, videos and orthomosaics can`).
- Deleting a Metashape file here deletes it from the Thermal Studio too.
- Rename before you export: the name, not the file name on disk, is printed in the report.
- Queue order is figure order. Fix it in the queue, not in the library.

> **Under the hood**
>
> Imported files are copied into the profile's data folder and recognised by their content and name: a picture GeoTIFF gets a PNG preview of at most 4096 px, an elevation model one at full size (up to 120 Mpx); a raster with one numeric band is an elevation model when its name says so; four or more bands make a multispectral orthomosaic; PDF, XML, CSV, point clouds and KML or KMZ are kept as documents with their metadata. Annotations are saved with each picture and drawn into its report figure. The library lives in the local profile, which is why the tab is desktop only.

<a id="photo-start-see-also"></a>

### See also

- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Giving a picture a scale: references, altitude and pitch, the Scale strip, units](#measure-scale)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Thermal Studio: getting started, importing, the library](#thermal-start)

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
- For AI drafts, a provider key is set in Settings → **AI Thermal Analysis**. That section shows only while the Thermal add-on is enabled.

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

<a id="photo-report-steps"></a>

### Steps

1. Click **📄 Report ▼** → **Open report builder…**. The **Photogrammetry Survey Report** window opens with a blank report dated today.
2. Type a name in the `Report name` box.
3. Work down the 13 numbered sections (see the table below). Each heading reads like `9 · Survey Imagery`.
4. Click **Save as new**, later **Save**. `Report saved.` confirms it.
5. Click **Preview & edit**. In the **Edit** tab, click any text to change it in place; the **PDF** tab shows the exported file; **Refresh** re-renders after you change figures or sections.
6. Click **Export ▼** and pick **PDF**, **Word (.docx)** or **RTF**.
7. Click **Export Bundle** to save the whole survey as one `.odlbundle` file.

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

**📏 Add measurements from pictures** adds a row for each distance, angle, area, volume, position and slope on the queued pictures, with its method and the figure that shows it; see [Measuring lengths, angles and areas: In the report](#measure-tools-in-the-report). **📦 Add materials from pictures** does the same for the take-offs; see [Material take-offs: In the report](#materials-takeoff-in-the-report). Both skip rows already added. A finding has a category, a severity (`Low severity`, `Medium severity`, `High severity`), a location, a **Documented in figure** link, an **Observation** and a **Recommendation**; an observation is a neutral note without a grade.

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
- **+ New blank** appears once a saved report exists. When figures are queued it asks whether to clear them too; choose Cancel to keep them for the new report.
- Both "Add … from pictures" buttons read only the queued pictures: queue first, then import.

> **Under the hood**
>
> An AI draft sends only the facts entered in the report (project data, flights, deliverables, measurements, the material count and projected total, findings) to the provider chosen in Settings, never the images. The bundle is a single `.odlbundle` file holding the report, its figures' assets with their annotations, the ticked deliverables, the embedded orthomosaic (even when it is not ticked) and the linked flights' full telemetry; the Thermal Studio's **Import inspection bundle…** reads it back. Every report carries the publisher line "Generated by \<publisher\> · \<workflow\>" under the title: the publisher is the company saved under Settings → **Branding**, and "Airwulf, LLC" until one is saved.

<a id="photo-report-see-also"></a>

### See also

- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames](#annotate)
- [Measuring lengths, angles and areas](#measure-tools)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)
- [Saving clients and claim details for reuse](#clients)

<sub>[Back to contents](#contents)</sub>


---

# Pictures: annotating and measuring

<a id="annotate"></a>

## Viewing and annotating pictures: zoom, pan, shortcuts, tools, colours, notes, video frames


The viewer in the Thermal Studio and in the Photogrammetry tab shows the picture you select in the library, with a toolbar above it. You can zoom and pan, mark up the picture with arrows, shapes and text, write a note for the report, and turn a video frame into a picture you can measure. Everything you draw is saved with the picture and drawn into the report figures.

<a id="annotate-before-you-start"></a>

### Before you start

- The Thermal or Photogrammetry add-on is installed, and its tab is open.
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

- [Giving a picture a scale: references, altitude and pitch, the Scale strip, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)
- [Heat flow network: nodes, conductors, solving](#thermal-network)
- [Thermal Studio: getting started, importing, the library](#thermal-start)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Photogrammetry survey reports](#photo-report) and [Thermal inspection reports](#thermal-report)

<sub>[Back to contents](#contents)</sub>

<a id="measure-scale"></a>

## Giving a picture a scale: references, altitude and pitch, the Scale strip, units


A measurement is only as good as the picture's scale: how much ground one pixel covers. This topic shows where the app finds a scale, how to give a picture one with a reference of known length, how to correct the altitude and pitch, and how to read the **🧭 Scale** strip that lists every source and its limits.

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
3. The camera's altitude and lens: the focal length, the altitude above the surface and the pitch from the file. The strip calls this metadata only.
4. No scale: measurements read `no scale`, and the strip says what is missing.

GCPs are covered in [Positions, ground control points and georeferenced orthomosaics](#measure-geo).

<a id="measure-scale-steps"></a>

### Steps

1. Press **📐 Reference** in the toolbar's **Measure** group.
2. Zoom in, then click both ends of the object of known length, or drag between them. A box opens at the middle of the line, with the placeholder `length, e.g. 2.5 m, 250 cm, 8 ft 2 in [± 0.02]` (imperial: `length, e.g. 8 ft 2 in, 8.5 ft, 250 cm [± 1 in]`).
3. Type the length and press Enter: `2.5 m`, `250 cm` or `8 ft 2 in`. A bare number is metres, or feet under imperial units. Add a tolerance after `±`: `2.5 ± 0.02` (a bare tolerance takes the length's unit). The tool switches to **📏 Measure**.
4. If the box shows `Not understood. …`, correct the text and press Enter. Esc, or an empty box, discards the reference.
5. Press **🧭 Scale**. The strip opens under the toolbar.
6. Read the **Scale** line: where the scale comes from, for example `1 reference + camera geometry (focal 3000 px, pitch −45.0°): 42.43 m ± 0.30 m above the reference plane`. Warnings follow in red (error), amber (caution) or blue (note).
7. Read **Ground sample distance at the centre**, for example `2.00 × 2.83 cm/px (across × along)` on a tilted picture, and **Camera focal length**.
8. If the file's altitude is wrong for this surface, type the camera's height above it in **Altitude above the surface (m)**, and its uncertainty after **±**. The note says `used only without references`: a reference always wins.
9. If the pitch is missing or wrong, type it in **Pitch (°)**: `−90` is straight down. A blank box uses the flight data in the file.
10. Check the **References** list: a name box (placeholder `Reference 1`), the length, `tolerance not given (exact)` when you typed none, the length in pixels and, with two or more, the deviation from the fit (for example `+1.7 % from the fit`). **✕** removes one.
11. Read the footer: what no ± includes (lens distortion, ground slope and relief, camera roll, pitch error for positions, DEM correlation and interpolation across ridges).

With a single reference the strip adds `Single sample, no cross-check: a second reference or two GCPs would show how well they agree.`

<a id="measure-scale-example-a-tilted-inspection-photo"></a>

### Example: a tilted inspection photo

A 4000 × 3000 px photo is taken at −45° pitch, focal length 3000 px, 50 m above the yard by the file (the scale specification's vectors).

1. From the camera data the strip reads `Camera metadata (…): focal 3000 px, pitch −45.0°, 50.0 m ± 1.0 m above the surface`, with the note `Scale from the camera metadata only (focal length and altitude); add a reference to check it.` The ground sample distance is `2.36 × 3.33 cm/px (across × along)`: 50 m ÷ (3000 px × sin 45°) = 2.36 cm across, 50 m ÷ (3000 px × sin² 45°) = 3.33 cm along.
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


Once a picture has a scale, three tools measure on it: **📏 Measure** for distances, **∠ Angle** for angles and roof pitches, and **⬠ Area** for plan areas and perimeters. Each value is labelled with its uncertainty, listed in the **🧭 Scale** strip and copied into the report in one click.

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
4. For a roof pitch, draw one ray along a level eave (within 5° of the picture's horizontal) and the other along the rafter. The strip adds, for example, `roof pitch 6.0:12 ± 0.1`.

<a id="measure-tools-area"></a>

### Area

1. Press **⬠ Area**. Three icons appear after it: polygon (⬠), rectangle (▭) and circle (◯). Pick one.
2. Draw the outline:
   - Polygon: click each corner; finish on the first corner, with a double-click or with Enter. Backspace removes the last corner.
   - Rectangle: click two opposite corners, or drag. Its sides run along the picture's edges.
   - Circle: click the centre, then a point on the rim, or drag from the centre.
3. Read the label: the plan area with its ±, for example `A1: 4.00 m² ± 0.05 m²`. From one hectare (or one acre) it reads in ha or ac.

<a id="measure-tools-the-scale-strip-rows"></a>

### The Scale strip rows

Press **🧭 Scale**. Each tool has its list: **Measurements** (M1, M2…), **Angles** (∠1…) and **Areas** (A1…).

- Name: type one in the row's first box (placeholder `name`). It replaces the tag on the picture (`ridge: 10.00 m ± 0.06 m`); in the report the tag stays and the name is added, for example `M1 10.00 m ± 0.06 m (ridge)`.
- Value: a length with ± (or `no scale`, or `n/a`), an angle `in the picture`, or an area with `perimeter …` and, for those shapes, `rectangle 14.00 m × 10.00 m` or `circle, diameter 48.00 m ± 0.28 m` (on a camera picture `rectangle in the picture (a trapezoid on the ground)` or `circle in the picture (an oval on the ground)`).
- **height above the reference plane (m)**: type how far a feature lies above the surface the scale was set on (negative below). It needs a camera picture with a focal length; on an orthomosaic a note says it is ignored, and on a flat scale an amber notice reads `A height above the reference plane needs the camera focal length; it is not used.`
- Detail lines: the ± broken down, for example `± 0.062 m = marking 0.007 m · scale 0.061 m` (plus `focal …` when known). An angle adds the angle `on the ground` and the roof pitch; a measurement adds its bearing and height difference when a position source or elevation model gives them.
- **✕** removes the row and its drawing.

Below the areas a note reads `Plan area on the reference plane; materials with a roof pitch multiply it by √(1 + (x/12)²). …` An area is always seen from straight above. Volumes are covered in [Elevation models](#measure-elevation).

<a id="measure-tools-example-a-flat-roof-survey-picture"></a>

### Example: a flat-roof survey picture

A picture looking straight down on a flat roof, with no focal length in its file, has one reference typed as `2 m ± 0.01`: a roof hatch 400 px long. The scale line reads `1 reference: 0.00500 m/px (flat picture, no camera geometry)`.

1. **📏 Measure** across a parapet, 2000 px long: `M1: 10.00 m ± 0.06 m` (imperial `32 ft 10 in ± 2 in`), detail `± 0.062 m = marking 0.007 m · scale 0.061 m`: the reference's own ±, scaled up five times with the length.
2. **⬠ Area**, polygon, around a skylight curb of 400 × 400 px: `A1: 4.00 m² ± 0.05 m²` (`43.1 ft² ± 0.5 ft²`), perimeter `8.00 m ± 0.05 m`.
3. On a second photo, square-on to the gable end of the stair housing, **∠ Angle** with one ray along the eave reads `∠1: 153.4°`, and the strip `roof pitch 6.0:12 ± 0.1`: the acute angle is 180° − 153.4° = 26.6°, and 12 × tan 26.6° = 6.0.

<a id="measure-tools-in-the-report"></a>

### In the report

The Photogrammetry report builder copies what you drew into its **Advanced Analysis & Measurements** section. The Thermal report prints, under each imaging pair, one measurements line per picture of the pair.

1. Queue the pictures as figures in the Photogrammetry tab (**+ Add to report**).
2. Open **📄 Report ▼** → **Open report builder…** and go to **Advanced Analysis & Measurements**.
3. Press **📏 Add measurements from pictures**. One row appears per distance, angle, area (with its perimeter), position and slope on the queued pictures, plus height-difference and elevation rows when an elevation model is paired, and a volume row per solid or cut, fill and net rows per elevation-model volume.
4. Check each row:
   - **Type**: `Length / distance`, `Area`, `Angle`, `Volume`, `Slope / pitch`, `Position`, `Height / elevation` or `Other`.
   - **Feature**: your name, or `Measurement 1`, `Area 1`…; a perimeter has its own row.
   - **Value** and **Unit**: in Settings → Units, rounded to two decimals.
   - **Method / tolerance / remarks**: most rows start with `In-image:` (a position row starts with the position itself), name the scale source and end with the ±, for example `± 0.062 m (1 sigma)`.
   - **Shown in figure**: the figure it is drawn on.
5. Read the notice: how many rows were added and what was skipped, for example `2 measurement(s) have no scale yet and were skipped.` Rows already there (same figure, type and feature) are not added again: press the button after adding measurements; to refresh a changed value, delete its row first.
6. Rows made under the other unit system show **Convert rows to ft** (or **Convert rows to m**). It converts the value, the unit and the ± in the method text.
7. **+ Add measurement** adds a row by hand, for a tape measurement on site.

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
> The picture angle uses the six click coordinates only; the ground angle is scale-free. The roof pitch is x = 12 × tan β, β being the acute angle between the rays. Not included: lens distortion, ground slope and relief, camera roll, a consistent click bias.

<a id="measure-tools-see-also"></a>

### See also

- [Giving a picture a scale: references, altitude and pitch, the Scale strip, units](#measure-scale)
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

<a id="measure-geo-the-scale-strip-s-position-block"></a>

### The Scale strip's Position block

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

> **Under the hood**
>
> Precedence: the orthomosaic's georeferencing, then a GCP fit (two or more GCPs of one kind), then the camera. A GCP fit is a weighted least-squares similarity for two GCPs (or collinear ones) and an affine for three or more, from the picture's reference plane to the map: a local transverse Mercator plane at the GCPs for latitude/longitude GCPs, their own grid for easting/northing GCPs. Each GCP is weighted by its accuracy combined with its marking. The Birge factor is √(χ² ÷ degrees of freedom), at least 1, and scales the fit's ± when the residuals exceed the stated accuracies.
>
> A camera position rotates the ground point by the heading (gimbal yaw, else the aircraft's heading, else the EXIF direction) about the GPS position. Its ± combines GPS (3 m by default), heading (2° by default, times the distance), scale or altitude, marking and focal length.
>
> Every position ± is horizontal and radial: about 63 % of positions fall within it. Not included: gimbal pitch error, lens distortion, relief (unless a height is typed), the antenna-to-camera offset, magnetic declination, datum differences such as NAD83 against WGS 84 (about 1 m).

<a id="measure-geo-see-also"></a>

### See also

- [Giving a picture a scale: references, altitude and pitch, the Scale strip, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Thermal Studio: getting started](#thermal-start)

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

When a one-band raster matches but its name says nothing, a blue note reads, for example, `1 one-band raster matches this orthomosaic; pick the elevation model (DEM) in the Scale strip.`

<a id="measure-elevation-slope"></a>

### Slope

1. Press **⟋ Slope** (greyed out until an elevation model is paired).
2. Click the low end, then the high end (eave to ridge, toe to crest), or drag between them.
3. Read the label: the pitch in degrees and as x:12, for example `S1: 26.6° (6.0:12)`.
4. Read the **Slopes** row: pitch, x:12, `grade` (%), `run` (horizontal), `rise` (end minus start) and `slope length`, each with its ±; the detail line adds both elevations and the bearing.

<a id="measure-elevation-volume-inside-an-area"></a>

### Volume inside an area

1. Draw an outline with **⬠ Area** around the pile, the pit or the slab (see [Measuring lengths, angles and areas](#measure-tools)). Trace it on bare ground at the toe of a pile.
2. In the strip, under the area's row, open the **Volume** select:
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

<a id="measure-elevation-example-a-stockpile-and-a-pit"></a>

### Example: a stockpile and a pit

The synthetic test pair `pile_ortho.tif` and `pile_DSM.tif` (0.1 m and 0.2 m pixels) has a mound of exactly 1000π ≈ 3,142 m³ and a pit of 10 m × 6 m × 2 m = 120 m³.

1. Draw a circle **⬠ Area** around the mound, 24 m in radius. Set **Volume** to `From the elevation model` with the plane base.
2. The strip reads `cut 3142 m³ ± 63 m³ · fill 0 m³ · net 3142 m³ ± 90 m³`, and the label `A1: 1809 m² ± 21 m² · 3142 m³ ± 90 m³` (imperial `A1: 19476 ft² ± 230 ft² · 4109 yd³ ± 118 yd³`). The area is π × 24² ≈ 1,810 m².
3. The net ± is the area times the DEM accuracy: 1,809 m² × 0.05 m ≈ 90 m³. The cut ± uses only the 1,257 m² that lie above the base: 1,257 × 0.05 ≈ 63 m³.
4. Switch the base to `Mean elevation of the outline`. Net stays 3142 m³, but the ± grows to 677 m³ and a warning says the outline is not level: on sloping ground use the plane.
5. Draw a rectangle over the pit. With the plane base its label reads `A2: 140 m² ± 2 m² · −120 m³ ± 7 m³`.
6. On a picture with no elevation model, a small gravel heap outlined as 4.00 m² and set to a cone 3 m high reads `4.00 m³ ± 0.05 m³`: ⅓ × 4 m² × 3 m = 4 m³.

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
- [Giving a picture a scale: references, altitude and pitch, the Scale strip, units](#measure-scale)
- [Material take-offs: from a measurement to an order, waste, prices](#materials-takeoff)
- [Photogrammetry: getting started, importing, the library and Metashape deliverables](#photo-start)
- [Thermal Studio: getting started](#thermal-start)

<sub>[Back to contents](#contents)</sub>

<a id="materials-takeoff"></a>

## Material take-offs: from a measurement to an order, waste, prices


A take-off turns a measurement on a picture into an order: how many bundles of shingles, fascia boards or tons of stone to buy. You pick a material under a measurement or an area in the Scale strip; the app adds the waste allowance, rounds up to whole units and, with a price, works out the cost. The same rows go into the report.

<a id="materials-takeoff-before-you-start"></a>

### Before you start

- A picture with a scale. Without one the row reads `no scale`. See [Giving a picture a scale](#measure-scale).
- A **📏 Measure** line (materials sold by length) or an **⬠ Area** (by area, roof surface, perimeter or volume). See [Measuring lengths, angles and areas](#measure-tools).
- For a volume material: an area with a volume, a solid or a cut and fill. See [Elevation models](#measure-elevation).
- For roofing: a pitch from a **⟋ Slope** or an **∠ Angle** with a level ray, or one you type.

<a id="materials-takeoff-steps"></a>

### Steps

1. Click **🧭 Scale** in the toolbar. Every row under **Measurements** (`M1`…) and **Areas** (`A1`…) has a **Materials** line.
2. Open **+ Material…** on that row. Materials are grouped by category: `Roofing`, `Exterior walls, fencing and decking`, `Concrete`, `Masonry`, `Pavement`, `Landscape and drainage`, `Bulk materials`, `Other`.
3. Pick a material, for example `Asphalt shingles — by roof surface`. The list offers only what the row can give (see the table below). A line appears with the material's fields and, under them, the take-off sentence.
4. Change **waste** if the job needs another allowance. Blank means the preset's percentage, shown greyed in the box.
5. For roofing, choose the **pitch**: a slope such as `S1: 6.0:12 (elevation model)`, an angle such as `∠1: 6.0:12 (in the picture)`, or `Typed`. With `Typed`, enter the rise in **x** (`6` for 6:12).
6. For a volume material on an elevation-model volume, choose `The larger of cut and fill` (the default), `Cut (above the base)`, `Fill (below the base)` or `Net (cut minus fill)`.
7. Type a **price** per order unit (per bundle, per ton). Blank means the preset's price; the shipped presets have none. The sentence then ends with the cost, such as `× $38.50 = $2,849.00`.
8. Read the block's footer once a take-off is priced. It reads like `Projected cost: $4,120.50 for 3 materials (of which waste $269.50; 1 without a price)` (illustrative figures; the worked example below gives real ones).
9. If **↻ use the catalogue's values** appears, the catalogue's preset has changed since you added the material. Click it to take the new values; the waste, pitch and price you typed stay.
10. Remove a take-off with **✕** at the end of its line.

| Row | A material can be taken from |
|---|---|
| Measure line | `length` |
| Area | `plan area`, `roof surface`, `perimeter` |
| Area with a volume | the above, plus `volume` |

<a id="materials-takeoff-in-the-report"></a>

### In the report

Both report builders have a **Materials and Projected Cost** section. The photogrammetry report reads the queued pictures; the thermal report reads the pictures of its imaging pairs.

1. Open **📄 Report ▼** → **Open report builder…** and scroll to **Materials and Projected Cost**.
2. Click **📦 Add materials from pictures**. A row appears for each take-off, with its price. Take-offs without a quantity are skipped, and rows already in the report are not added again.
3. Check each row: **Material**, **From**, **Order**, **Unit**, **Waste %**, **Waste units**, the unit price, the **Basis** sentence and a **Note** (supplier, quote number). **Cost** shows under it `of which waste $…` whenever the row has a cost and its waste units are known, even when that is $0.00.
4. Set the **Currency** (`USD`, `EUR`, `CAD`…). While no row has a price, the report takes the catalogue's currency.
5. Read the total line, for example `Projected total $2,849.00 for 1 priced row · of which waste $231.00`. Rows without a price or an order count are counted after it (`· N row(s) without a price or an order count (not in the total)`) and left out of the total.
6. Add a row by hand with **+ Add material**, or remove one with **✕**.
7. Click **Preview & edit**. The table has the columns Material, From, Basis, Order, Unit price, Cost and Waste. From starts with `Figure 2` (photogrammetry) or `Pair 2 (thermal)` (thermal). Below the rows come `Projected total` and, when waste costs something, `Waste allowance (in the total)`, then a note that prices were entered by the inspector and the total is a projection.

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
- A notice such as `Asphalt shingles: No roof pitch: type x in x:12.` means the roof line needs a slope, an angle or a typed x.

> **Under the hood**
>
> The count is the quantity (× √(1 + (x/12)²) for roofing), plus the waste percentage, divided by what one unit covers, rounded up. With a package the rounding is done in packages from the exact count: 24.6 × 3 = 73.8, so 74 bundles, not 25 squares × 3 = 75. By weight: volume × density, then weight ÷ the weight of one unit. Waste units are the order minus the order at 0 %. Prices are per order unit, and each cost is rounded to the cent as printed, so the strip, the builder and the export agree.
>
> Presets are rules of thumb: check them against the product. Values are stored in metric and shown in your units. Each take-off keeps a copy of its preset, so a picture reads the same anywhere.

<a id="materials-takeoff-see-also"></a>

### See also

- [Editing the material catalogue: presets, units, packages, waste, prices](#settings-material-presets)
- [Measuring lengths, angles and areas](#measure-tools)
- [Elevation models: pairing a DEM, slopes, cut and fill volumes, solids](#measure-elevation)
- [Photogrammetry survey reports: the figure queue, sections, flights, deliverables, export](#photo-report)
- [Thermal inspection reports, AI drafts and inspection bundles](#thermal-report)

<sub>[Back to contents](#contents)</sub>


---

# Settings

<a id="settings-material-presets"></a>

## Editing the material catalogue: presets, units, packages, waste, prices


The material catalogue is the list the **+ Material…** chooser offers in the Scale strip. Each preset says how a material is measured, what it is sold as, what one unit covers, how it is packed, the usual waste and, if you want, a price. You edit it in Settings, so the take-offs match your suppliers and your prices.

<a id="settings-material-presets-before-you-start"></a>

### Before you start

- The desktop app, with the Thermal or the Photogrammetry add-on enabled. The section shows only then.
- Open **Settings** and find **Material take-off presets** in the left column.
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

1. Set **Currency** above the table: three letters, such as `USD`, `EUR` or `CAD`. Press Enter or leave the box to apply it; Esc puts it back.
2. Click **+ Add a material** for a new preset, or **Edit** on a row to change one. A form opens above the table and the row is highlighted.
3. Type the **Material** name and choose its **Category**: `Roofing`, `Exterior walls, fencing and decking`, `Concrete`, `Masonry`, `Pavement`, `Landscape and drainage`, `Bulk materials` or `Other`.
4. Choose **Measured by**: `Length or perimeter`, `Area`, `Roof surface (area × pitch factor)` or `Volume`. Switching between length, area and volume resets **One unit covers** to 1.
5. Choose **Sold as**. The list fits the basis: `ft`, `m`, `ft²`, `m²`, `square / squares`, `sheet / sheets`, `bundle / bundles`, `ft³`, `yd³`, `m³`, `gallon / gallons`, `ton / tons`, `tonne / tonnes`, `lb`, `kg`, then counts such as `piece / pieces`, `board / boards`, `roll / rolls`, `bag / bags`, `pallet / pallets`. For your own word pick `Other…` and fill **Sold as (one)** and **Sold as (many)**.
6. Check **One unit covers**. Picking a unit fills it when the size is known: a square is 100 ft², a sheet 32 ft² (4 × 8 ft), a bundle 33⅓ ft². Change its unit in the list next to it (`ft`, `in`, `m`, `cm`; `ft²`, `square (100 ft²)`, `m²`; `ft³`, `yd³`, `gal (US)`, `m³`); the number is converted.
7. For a volume material, picking `ton / tons`, `tonne / tonnes`, `lb` or `kg` ticks **Sold by weight**, fills **Weight per unit** (its unit: `lb`, `ton (2,000 lb)`, `kg`, `tonne (1,000 kg)`) and, when **Density** is blank, fills it with 100 lb/ft³ or 1,600 kg/m³. Check both against the product. Without that tick the field reads **Density (optional, shows the weight)**.
8. Choose **Waste**: `0 % — exact count (panels, posts, fixtures)`, `5 % — simple gable roof, straight runs`, `10 % — standard`, `15 % — hips and valleys, many cuts`, `20 % — complex roof, patterns, diagonal layouts`, or `Other…`, which adds a small box followed by `%` (named `Waste (custom)` for screen readers) for your own figure.
9. Under **Package (optional)**, pick `No package` or a package: `bundle / bundles`, `box / boxes`, `carton / cartons`, `case / cases`, `bag / bags`, `roll / rolls`, `pallet / pallets`, `pail / pails`, or `Other…`, which adds two boxes showing `bundle` and `bundles` as placeholders (`Package (one)` and `Package (many)`) for your own words. Next to the package a count box (placeholder `3`, followed by `per unit`; named `Packages per unit`) fills from the convention: 3 bundles or 0.5 box per square. Otherwise it stays blank and the form asks for it.
10. Type the price in **Price per** (the order unit and currency follow, such as `Price per bundle (USD)`). Leave it blank for `not priced`.
11. Add a **Note (shown on hover in the strip)**, then click **Save**. `Material presets saved.` confirms it. **Cancel** closes the form.
12. Click **Delete** on a row to remove a preset. It goes at once, with no question.
13. Click **Reset to the shipped presets** to start over. The app asks first; your own presets and edits are removed, the currency stays.

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
- Editing a preset changes only new take-offs. Old ones keep their copy until you click **↻ use the catalogue's values** in the strip.
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
- [Giving a picture a scale: references, altitude and pitch, the Scale strip, units](#measure-scale)
- [Measuring lengths, angles and areas](#measure-tools)

<sub>[Back to contents](#contents)</sub>

<a id="settings-branding"></a>

## Branding your reports: logo, company and Part 107 number

> **Coming in the next update:** this feature is not in add-ons 1.0.0 yet.


Branding puts your company on every report the Thermal and Photogrammetry add-ons produce: your logo and company name at the top of the first page, your name and FAA Part 107 certificate number, your contact details, and your company as the publisher under the title. You enter it once in Settings. New reports also start with your name, certificate and contact already filled in.

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

<a id="clients"></a>

## Saving clients and claim details for reuse

> **Coming in the next update:** this feature is not in add-ons 1.0.0 yet.


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


---

# Add-ons

<a id="addon-license"></a>

## Buying, activating and renewing an add-on license, and updating add-ons


The Thermal Analysis Studio and the Photogrammetry add-on each run on a license: a subscription per add-on at $7.99 a month or $75 a year, which you can cancel at any time. The add-on itself is free to download and install; the license switches its functions on.

<a id="addon-license-before-you-start"></a>

### Before you start

- You need the desktop app for Windows, installed per user from Open DroneLog's own GitHub setup (`.exe`). The all-users (MSI) install is not supported by the add-on installers.
- Install the add-on first: click **Add-ons** in the sidebar, then **Download installer…** for the add-on, run it, and click **↻ Refresh**. Until it has a license, the add-on's tab shows a lock panel headed "… needs a license" instead of the studio.
- Activating a key needs an internet connection once. A computer that never goes online uses a license file instead (see [Offline computers](#addon-license-offline-computers)).

<a id="addon-license-buying-a-license"></a>

### Buying a license

1. On the lock panel, or in the add-on's row of the **🧩 Add-ons** window, click **Buy monthly ($7.99)** or **Buy yearly ($75)**. The purchase page opens in your browser.
2. If you already have a key for the other add-on, paste it into the "Already a customer?" field. Both subscriptions then stay on one account and one customer portal. The field is optional.
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

The add-ons run inside an Airwulf build of Open DroneLog that their installer puts in place. If you later install a newer Open DroneLog from GitHub, its installer puts the original program back: Open DroneLog starts without the add-ons and without the **Add-ons** button.

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

<sub>[Back to contents](#contents)</sub>
