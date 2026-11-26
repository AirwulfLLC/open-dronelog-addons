# Open DroneLog Add-ons

Optional add-ons for **Open DroneLog**, the free desktop program that keeps and analyzes your drone flight logs. Each add-on gives Open DroneLog a new tab for a kind of drone work that the free program does not cover.

| Add-on | What it adds | Installer file |
|---|---|---|
| **Thermal Analysis Studio** | A **Thermal** tab: a temperature for every pixel of a thermal (radiometric) drone photo, hot and cold spot detection, heat-flow modelling and inspection reports, an analysis boundary, side-by-side documents, temperature exports and claim packages | `OpenDroneLog-Thermal-Addon_<version>_x64-setup.exe` |
| **Photogrammetry** | A **Photogrammetry** tab: one library for survey photos, videos and Agisoft Metashape outputs, with measuring tools and survey reports, orthomosaic and linework export, volume tickets and claim packages | `OpenDroneLog-Photogrammetry-Addon_<version>_x64-setup.exe` |
| **360 Panorama Studio** | A **360 Pano** tab: the photos of one drone hover stitched into one 360-degree photo, with mark-ups drawn on the photos, a viewer to look around in, a starting view you choose, and exports as a 360 JPEG and as a web page that opens in any browser | `OpenDroneLog-Panorama-Addon_<version>_x64-setup.exe` |

The add-ons are made by Airwulf, LLC. They are not part of, or endorsed by, the original Open DroneLog project.

**Contents**

- [What's new in 1.1.0](#whats-new-in-110)
- [What was new in 1.0.2](#what-was-new-in-102)
- [What was new in 1.0.1](#what-was-new-in-101)
- [Before you start](#before-you-start)
- [Install an add-on, step by step](#install-an-add-on-step-by-step)
- [Activate your license](#activate-your-license)
- [Update an add-on](#update-an-add-on)
- [After you upgrade Open DroneLog itself](#after-you-upgrade-open-dronelog-itself)
- [Turn off or remove an add-on](#turn-off-or-remove-an-add-on)
- [Troubleshooting](#troubleshooting)
- [Help with the add-ons](#help-with-the-add-ons)
- [Licenses](#licenses)

---

## What's new in 1.1.0

This release brings **Thermal Analysis Studio 1.1.0**, **Photogrammetry 1.1.0** and the first version (1.0.0) of a new add-on, the **360 Panorama Studio**. All three are built for **Open DroneLog 3.4.0**. If you already have an earlier version, get the new one as described in [Update an add-on](#update-an-add-on). The update also brings your Open DroneLog program to 3.4.0.

**New add-on: 360 Panorama Studio**

- A **360 Pano** tab turns the photos of one drone hover into one 360-degree photo. You import the photos, the studio groups them into sets and shows how much of the sphere they cover, and **Stitch 360** joins them. See [360 Panorama Studio: getting started](HELP.md#panorama-start) and [Stitching a 360](HELP.md#panorama-stitch).
- The photos use the camera angles the drone writes into them. DJI photos have them (check your software to be sure).
- Draw on the photos to point something out: the mark-ups show on the 360. A photo that does not render correctly when stitched can be left out with **Leave out of 360**; the choice lasts until you close the program. See [Mark up a photo](HELP.md#panorama-start-mark-up-a-photo) and [Leave photos out](HELP.md#panorama-start-leave-photos-out).
- Look around the finished 360, and choose the view it opens at with **Set starting view**. See [Looking around a 360](HELP.md#panorama-export).
- Save it as a 360 JPEG with **Export 360 JPEG…**, or as one web page that opens in a web browser without an internet connection with **Export HTML viewer…**. With a licensed Photogrammetry add-on, **Save view to Photogrammetry** keeps one view as a picture for a survey report. See [Export a 360 JPEG](HELP.md#panorama-export-export-a-360-jpeg), [Export an HTML viewer file](HELP.md#panorama-export-export-an-html-viewer-file) and [Save a view to the Photogrammetry library](HELP.md#panorama-export-save-a-view-to-the-photogrammetry-library).
- Install it like the other add-ons: see [Install an add-on, step by step](#install-an-add-on-step-by-step). After you update Thermal or Photogrammetry to 1.1.0, the **🧩 Add-ons** window lists it too, with a **Download installer…** button that opens the release page.
- Its license is not on sale yet: see the note in [Activate your license](#activate-your-license).

**Open DroneLog 3.4.0**

- The add-ons now run in the Airwulf build of Open DroneLog 3.4.0. From the original project, 3.4.0 brings the **Chat** tab and the **External agents** section in Settings.

**AI**

- **AI tools for Chat and external agents.** While an add-on is licensed, the **Chat** tab can read your add-on data: the library, thermal figures, annotations, heat flow networks, saved reports and AI usage. So can an external agent, once you turn the server on under **Settings** → **External agents** and make a connection for it. If you allow it (for Chat in **Settings** → **AI tools**, for an agent when you make its connection), they can also propose changes, such as a new picture name, a note or report text. Open DroneLog then shows every change with its value before and after, and nothing is stored until you press **Apply**. What a tool returns is sent to the AI provider or the agent you connected; the guide lists what is never given. See [AI tools](HELP.md#ai-tools).
- **One key for Chat and the add-ons.** The AI narrative of the Thermal Studio and the `✨ AI draft` boxes of the report builders can use the Chat connection, so one key serves both. Your own Claude, OpenAI or Gemini key still works. You choose in **Settings** → **AI providers** (this section was called **AI Thermal Analysis**). See [AI provider keys](HELP.md#thermal-anomalies-ai-provider-keys).
- **AI drafts with either license.** The `✨ AI draft` boxes now work with a Thermal or a Photogrammetry license. The AI thermal analysis narrative of the Thermal Studio still needs the Thermal license.
- **Chat in the AI usage bar.** The bar now shows as soon as the Chat connection is set, and it counts each answer in the **Chat** tab too, in the month's figures under **No customer**. See [AI usage](HELP.md#ai-usage).

**Customer data**

- **Encrypt your saved clients with a password.** In **Settings** → **Customer data encryption** you can lock the saved client list, and the customer picked in the AI usage bar, behind a password. You enter it each time the program starts, and again after you switch profiles or log back in. Saved reports, pictures and exports are not encrypted; the guide lists what stays readable. Nobody can reset the password or recover the data, Airwulf included. See [Encrypting customer data with a password](HELP.md#customer-encryption).

**The program and Settings**

- **The build you run, in the sidebar.** The bottom of the sidebar now reads, for example, **Open DroneLog Airwulf 3.4.0 (build 4)**, with **Latest** or an update link beside it. See [Update an add-on](#update-an-add-on).
- **Settings.** UI updates for easier AI management. Messages now show on one line at the bottom of the Settings window.
- Fixes in profile switching, backup restore, inspection bundles and the light theme.

---

## What was new in 1.0.2

Version 1.0.2 of Thermal and Photogrammetry brought the following. All of it is part of 1.1.0.

- **Add-ons moved into Settings.** Click **Settings** in the sidebar, then **Open Add-ons**. The button next to Settings is gone. (In 1.0.1 and earlier the **🧩 Add-ons** button is still next to Settings: use it to update.)
- **AI usage.** With an AI provider key saved, a usage bar under the Thermal and Photogrammetry studios shows what your AI runs used and cost, for the customer and project you are working on and for the calendar month. A setting adds that cost to a report. See [AI usage](HELP.md#ai-usage).
- Fixes in reports, inspection bundles, the library and Settings.

---

## What was new in 1.0.1

Version 1.0.1 brought the following. All of it is part of 1.1.0.

**Thermal**

- Draw an outline with **⛶ Boundary** around the item you want to analyse. The statistics, the isotherm figures, the palette range and the AI analysis then read only inside it. See [The analysis boundary](HELP.md#thermal-boundary).
- Read every spot and ΔT mark of a picture, with its pixel position, in the **Spot readings** section of the Analysis panel. See [Spot readings](HELP.md#thermal-deliverables-spot-readings).
- Build a document with the visual and the thermal picture side by side, one page per picture, with **📄 Side-by-side…**. See [Side-by-side](HELP.md#thermal-deliverables-side-by-side).
- Export the temperature of every pixel as a TIFF or CSV file with **🌡 Export temperatures…**. See [Temperature export](HELP.md#thermal-deliverables-temperature-export).
- Link each thermal picture to its visual twin, by itself on import or with **⇄ Pair pictures**. See [Pairing thermal and visual pictures](HELP.md#thermal-start-pairing-thermal-and-visual-pictures).

**Photogrammetry**

- Export an orthomosaic as a JPG with its world file and a presentation copy with **🗺 Export orthomosaic…**. See [Exporting an orthomosaic](HELP.md#mapping-deliverables-exporting-an-orthomosaic).
- Print a numbered ticket for one measured volume with **🧾 Volume ticket…**. See [Printing a volume ticket](HELP.md#mapping-deliverables-printing-a-volume-ticket).

**Thermal and Photogrammetry**

- Search the library by name, filter it, and delete multiple pictures at once with **Select all** and **Delete selected…**. See the [Thermal library](HELP.md#thermal-start-the-asset-library) and the [Photogrammetry library](HELP.md#photo-start-the-library).
- Export the measurements and drawings of a picture as DXF, GeoJSON or ODL XML with **📐 Export linework…**. See [Exporting linework](HELP.md#mapping-deliverables-exporting-linework).
- Turn a measurement into a material order, with waste and prices, in the **🧮 Material Takeoff** strip. See [Material take-offs](HELP.md#materials-takeoff-steps).
- Hand a report over as a claim package (original pictures, portal copies and a custody sheet in one folder) with **📦 Claim package…** in the report builder. See [Delivering a claim package](HELP.md#claim-package).
- Import a whole camera folder with **📂 Import folder…**. See [Import folder](HELP.md#claim-package-import-folder).
- Put your logo, company name and Part 107 number on every report in **Settings** → **Branding**, and save clients to pick them in later reports. See [Branding your reports](HELP.md#settings-branding) and [Saving clients](HELP.md#clients).
- Some licenses are tied to one computer. Move such a license to another computer with **Deactivate this PC**. See [Licenses tied to this computer](HELP.md#addon-license-licenses-tied-to-this-computer) and [Deactivating this computer](HELP.md#addon-license-deactivating-this-computer).

---

## Before you start

Check these five things first. Each takes a minute, and together they prevent almost every install problem.

1. **A Windows 11 computer (64-bit).** The add-ons only work in the Windows desktop program. The Open DroneLog web app, Docker version and Android app cannot use them.
2. **Open DroneLog installed with its "setup.exe" installer.** Open DroneLog offers two Windows installers: a *setup.exe* (installs for your Windows account only) and an *.msi* (installs for every account on the computer). The add-ons only work with the **setup.exe** install. Step 1 below shows how to get it.
3. **The right Open DroneLog version.** Each add-on release is built for one Open DroneLog version, and its installer will not run on a newer one. The current add-ons are built for **Open DroneLog 3.4.0**. An older Open DroneLog is fine: the add-on installer brings it to 3.4.0. If you have a newer Open DroneLog, check the [Releases page](https://github.com/AirwulfLLC/open-dronelog-addons/releases) for a matching add-on release.
4. **No administrator password needed.** The add-ons install into your own Windows account, the same way Open DroneLog does.
5. **A license for each add-on you want to use.** Downloading and installing the add-ons is free. A license switches their features on: **$7.99 a month or $75 a year per add-on**, cancel anytime. You can install first and buy the license later from inside the program. Activating a license needs an internet connection once; for a computer that is never online, see [Offline computers](HELP.md#addon-license-offline-computers) in the help file.

> **Words used in this guide**
> - **Installer**: the `.exe` file you download and double-click to add a program to Windows.
> - **Release**: a published version of the add-ons on GitHub. Its installer files are listed under **Assets**.
> - **License key**: the code you get after buying. It switches an add-on on.
> - **Host program**: the add-ons run inside a slightly extended copy of Open DroneLog (the "Airwulf build"). The add-on installer puts it in place for you and keeps a backup of your original program. Your flights, settings and profiles are not touched.

---

## Install an add-on, step by step

Do these steps once for each add-on. If you want more than one add-on, install one, then repeat Steps 2 to 7 for each of the others.

### Step 1: Install Open DroneLog (skip if you already have it)

1. Go to the Open DroneLog releases page: https://github.com/arpanghosh8453/open-dronelog/releases
2. Find release **3.4.0** and open its **Assets** list (click **Show all assets** if the Windows files are hidden).
3. Download the file whose name ends in **`_x64-setup.exe`**. Do **not** download the `.msi` file.
4. Double-click the downloaded file and follow the installer.
5. Start Open DroneLog once to make sure it opens, then close it.

> **Already have Open DroneLog but not sure which installer you used?** Just go on to Step 2. The add-on installer checks for you and stops with a clear message if it finds the `.msi` version. In that case, uninstall Open DroneLog from Windows **Settings → Apps → Installed apps**, then install the `setup.exe` as above.

### Step 2: Download the add-on installer

1. Open this repository's latest release: https://github.com/AirwulfLLC/open-dronelog-addons/releases/latest
2. Under **Assets**, click the installer for the add-on you want:
   - Thermal: `OpenDroneLog-Thermal-Addon_<version>_x64-setup.exe`
   - Photogrammetry: `OpenDroneLog-Photogrammetry-Addon_<version>_x64-setup.exe`
   - 360 Panorama Studio: `OpenDroneLog-Panorama-Addon_<version>_x64-setup.exe`
3. Your browser saves it, usually in your **Downloads** folder.

> You can ignore the other files in the release. `addons.json` is what Open DroneLog reads to check for updates. `OpenDroneLog-Airwulf-Build_…_x64-setup.exe` is the Open DroneLog program itself in the build the add-ons run in, for a new install. The `…_base-source.zip` holds the source files of the base program, without the add-ons (see [Licenses](#licenses)). GitHub's own **Source code** links under a release hold only this page and the help file.

### Step 3: Close Open DroneLog

Close Open DroneLog if it is open. (If you forget, the installer asks: click **OK** to let it close the program, or **Cancel** to stop.)

### Step 4: Run the installer

1. Double-click the installer file you downloaded.
2. Windows may show a blue box saying **"Windows protected your PC"**. This is Windows SmartScreen, which warns about new programs it has not seen often. Click **More info**, check that the app name matches the add-on you downloaded, then click **Run anyway**.

   Only do this for an installer you downloaded yourself from the Releases page above.

### Step 5: Enter your license key (optional)

The installer opens on a **License key** page.

- **Already bought a license?** Paste the key from the purchase page into the box.
- **Not yet?** Leave the box empty. You can enter the key later inside Open DroneLog (see [Activate your license](#activate-your-license)).

Click **Install**. The installer lists each step as it works: it saves a backup copy of your original Open DroneLog program, puts the host program in place, and copies the add-on's files.

### Step 6: Finish

When the install is done, a message says the add-on is installed. Click **OK**, then **Close**.

### Step 7: Switch the add-on on in Open DroneLog

1. Start Open DroneLog.
2. Click **Settings** in the sidebar, then **Open Add-ons**.
3. Click **↻ Refresh**. The window always lists all three add-ons. The one you installed now shows its version, for example **Enabled · v\<version\>**. An add-on that is not installed shows **Not installed** and a **Download installer…** button.
4. Make sure **Enabled** is ticked.
5. Close the Add-ons window. A new **Thermal**, **Photogrammetry** or **360 Pano** tab appears in the sidebar.
6. Open the new tab:
   - If the studio opens, you are done.
   - If you see a panel headed **"… needs a license"**, follow [Activate your license](#activate-your-license).

> **Thermal add-on check:** the top of the Thermal tab should show a green **DJI Thermal SDK ready** badge. If it shows a red **DJI SDK unavailable** badge, run the Thermal installer again.

---

## Activate your license

If you entered your key in the installer, Open DroneLog activates it the next time it starts, and you can skip this section.

**To buy a license:**

1. Open the add-on's tab (or its row in the **🧩 Add-ons** window).
2. Click **Buy monthly ($7.99)** or **Buy yearly ($75)**. The purchase page opens in your web browser.
3. If you already have a key for another add-on, paste it into the **"Already a customer?"** box so all your subscriptions share one account. Otherwise leave it empty.
4. Click **Continue to payment** and pay by card.
5. The thank-you page shows your license key. Click **Copy**, and **bookmark the page**: it is your way back to the key if you lose it.

> **360 Panorama Studio:** its license is not on sale yet. Until it is, its **Buy** buttons open a page that reads **Not found**. You can install the add-on now; its tab shows the lock panel until it has a license.

**To activate the key:**

1. Open the add-on's tab. The lock panel shows **No license**.
2. Click **Enter license key…**, paste the key and click **Activate**.
3. The lock panel disappears and the studio opens. In the **🧩 Add-ons** window, the add-on's row now reads **Licensed until \<date\>**.

Subscriptions renew by themselves. To change your card, see invoices or cancel, click **Manage subscription** in the add-on's row. Each license covers one add-on: a Thermal key does not unlock Photogrammetry.

**No internet on this computer?** The thank-you page also has a **Download license file** button. Download the file on a computer with internet, carry it over (for example on a USB stick), and click **Import license file…** on the lock panel or in the **🧩 Add-ons** window. See [Offline computers](HELP.md#addon-license-offline-computers).

**Refresh:** click **Refresh** on the lock panel or in the add-on's row to check the license again, for example after the computer is back online.

**To move a license to another computer:** some licenses are tied to the computer they were activated on. For such a license, the lock panel and the add-on's row show a **Deactivate this PC** button.

1. On the old computer, click **Deactivate this PC**.
2. Click **Copy** to keep the key, then click **Deactivate**.
3. On the new computer, activate the key as above.

See [Licenses tied to this computer](HELP.md#addon-license-licenses-tied-to-this-computer) and [Deactivating this computer](HELP.md#addon-license-deactivating-this-computer).

The help file has the full details, including offline computers and renewal warnings: [Buying, activating and renewing an add-on license](HELP.md#addon-license).

---

## Update an add-on

Open DroneLog checks for add-on updates by itself about once a day. To check now:

1. Open the **🧩 Add-ons** window and click **Check for updates**.
2. If a newer version exists, the add-on's row shows **Update to v\<version\> (\<size\> MB)**. Click it.
3. A progress bar fills while the update downloads and is verified.
4. The row reads **Restarting to apply…**. Open DroneLog closes, installs the update and starts again.

Instead of the update button, the row may show one of these lines:

- **Update v\<version\> cannot be installed on this computer yet**, followed by the reason. When your Open DroneLog is newer than the one the update was built for, wait for an add-on release built for your version.
- **Update check failed:** followed by the reason. Check the internet connection and click **Check for updates** again.

**No internet on that computer?** Download the newest installer from the [Releases page](https://github.com/AirwulfLLC/open-dronelog-addons/releases) on another computer, copy it over (for example on a USB stick), and run it. You do not need to enter your key again.

**The program's own version.** The bottom of the sidebar names the build you are running, for example **Open DroneLog Airwulf 3.4.0 (build 4)**. The badge beside it reads **Latest**, or **Update to Open DroneLog Airwulf \<version\> (build \<number\>)** when a newer build is published. (It reads **Checking…** while it looks, and **Check failed** when it could not look, for example without an internet connection.) Click the update badge to open the release page. With an add-on installed, update the add-on as above: the add-on update brings the newer program with it. Without an add-on, download `OpenDroneLog-Airwulf-Build_…_x64-setup.exe` from the release page and run it.

---

## After you upgrade Open DroneLog itself

If you later install a newer Open DroneLog from the original project's GitHub page, its installer puts the plain program back. Open DroneLog then starts **without** the add-on tabs and without the **Add-ons** section in Settings. Nothing is lost.

1. Download the current add-on installer from the [Releases page](https://github.com/AirwulfLLC/open-dronelog-addons/releases/latest). It must be built for your new Open DroneLog version; an older installer stops and tells you so.
2. Run it (Steps 3 to 6 above). You do not need to enter your key again.
3. Start Open DroneLog. The add-on tabs are back, with your licenses, pictures, reports and settings.

---

## Turn off or remove an add-on

**Hide an add-on for now:** in the **🧩 Add-ons** window, untick **Enabled**. Its tab disappears and its files stay. This does **not** cancel your subscription; use **Manage subscription** for that.

**Remove an add-on completely** (either way works):

- **From Open DroneLog:** in the **🧩 Add-ons** window, click **Remove** on the add-on's row and confirm.
- **From Windows:** open **Settings → Apps → Installed apps**, find **Open DroneLog Thermal Analysis Add-on**, **Open DroneLog Photogrammetry Add-on** or **Open DroneLog 360 Panorama Add-on**, and choose **Uninstall** from its **⋯** menu.

What happens next:

- Your imported pictures, measurements and reports stay in your Open DroneLog profile.
- Your license stays on the computer, so a later reinstall finds it.
- Removing an add-on does not free a license that is registered to this computer. If the license should move to another computer, click **Deactivate this PC** first (see [Activate your license](#activate-your-license)).
- If it was the **last** add-on installed, Open DroneLog restarts with your original program put back. That is the Open DroneLog you had when you first installed an add-on, so it can be older than 3.4.0; install the current version from the original project's page if you want it. If another add-on is still installed, the host program stays.
- If putting the original back cannot finish, the row reads **Removing … failed**, with **Retry** and **Keep add-on** buttons.

---

## Troubleshooting

When the installer stops, it says why, and it has changed nothing. Find the message below:

| Message | What it means | What to do |
|---|---|---|
| **Open DroneLog was not found. Install Open DroneLog first** | Open DroneLog is not installed for your Windows account | Do [Step 1](#step-1-install-open-dronelog-skip-if-you-already-have-it), then run the add-on installer again |
| **An all-users (MSI) install of Open DroneLog was found. It is not supported** | Open DroneLog was installed with the `.msi` | Uninstall it from **Installed apps**, install the `_x64-setup.exe` (Step 1), then run the add-on installer again |
| **Open DroneLog \<version\> is newer than this add-on's build** | Your Open DroneLog is newer than this add-on release supports | Download the current add-on installer from the address the message gives; it opens this repository's [latest release](https://github.com/AirwulfLLC/open-dronelog-addons/releases/latest). If no release is built for your Open DroneLog yet, wait for one |
| **Open DroneLog is still running** | The program was open | Close Open DroneLog (check the taskbar) and run the installer again |
| **Another add-on installer or uninstaller is running** | Two installers were started at once | Let the first one finish, then try again |
| **The installed program could not be read (is it locked?)** | The installer could not read the Open DroneLog program file | Close Open DroneLog and run the installer again |
| **Open DroneLog could not be replaced (the program file is locked)** | Another program is using the Open DroneLog file | Close Open DroneLog, wait a minute or restart the computer, then try again |
| **Windows protected your PC** | SmartScreen warning for a new download | Click **More info → Run anyway** (see [Step 4](#step-4-run-the-installer)) |
| **Repair needed: run the add-on installer** at the bottom of the **🧩 Add-ons** window | An earlier install or removal was interrupted | Run the add-on installer again (Steps 3 to 6) |
| The add-on tab doesn't appear after installing | Open DroneLog has not re-read its add-ons folder | In **🧩 Add-ons**, click **↻ Refresh** and tick **Enabled** |
| **DJI SDK unavailable** on the Thermal tab | The thermal camera library files are missing | Run the Thermal installer again |
| A license key shows as **Rejected** | The licensing service refused the key | Check the key, then click **Retry**; see the [license help](HELP.md#addon-license) |

**Still stuck?** The installer writes its last error to a file. Press **Windows key + R**, type `%TEMP%\odl-addon-installer.log`, press **Enter**, and include what it says when you ask for help in this repository's [Issues](https://github.com/AirwulfLLC/open-dronelog-addons/issues).

**Where the add-ons keep their files** (you normally never need these):

| What | Folder |
|---|---|
| Installed add-ons | `%APPDATA%\com.drone-logbook\addons\` |
| Licenses | `%APPDATA%\com.drone-logbook\licenses\` |
| Backup of your original Open DroneLog program | `%APPDATA%\com.drone-logbook\host\backup\` |

---

## Help with the add-ons

**[HELP.md](HELP.md)** holds every help guide built into the add-ons (the **?** buttons in the program) in one file with a table of contents: getting started, thermal analysis, the analysis boundary, side-by-side documents and temperature exports, 360 panoramas, measuring, material take-offs, reports, claim packages, orthomosaic and linework export, volume tickets, settings, branding, AI usage, AI tools, clients, customer data encryption and licensing.

For the main Open DroneLog program (importing flight logs, maps, charts, battery tracking and so on), see the original project's [user manual](https://github.com/arpanghosh8453/open-dronelog/blob/main/docs/manual.md).

---

## Licenses

- **Open DroneLog** is free, open-source software by Arpan Ghosh, licensed under the [GNU Affero General Public License v3.0](https://github.com/arpanghosh8453/open-dronelog/blob/main/LICENSE) (AGPL-3.0). Original project: https://github.com/arpanghosh8453/open-dronelog
- The program that the add-on installers put in place (the Airwulf build) is built from Open DroneLog 3.4.0. The source files of that base program, as the Airwulf build changed them, are attached to the current add-on release as `OpenDroneLog-Airwulf-Build_<Open DroneLog version>_base-source.zip`.
- The **Thermal Analysis Studio**, **Photogrammetry** and **360 Panorama Studio** add-ons are software of Airwulf, LLC and are licensed separately (see [Activate your license](#activate-your-license)). They are not part of that archive.
- The Thermal add-on includes the DJI Thermal SDK runtime, which is DJI's software and is distributed under DJI's own terms.
- DJI is a registered trademark of SZ DJI Technology Co., Ltd. Other product names are trademarks of their owners. These add-ons are independent and are not affiliated with or endorsed by those companies.
