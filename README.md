# Open DroneLog Add-ons

Optional add-ons for **Open DroneLog**, the free desktop program that keeps and analyzes your drone flight logs. Each add-on gives Open DroneLog a new tab for a kind of drone work that the free program does not cover.

| Add-on | What it adds | Installer file |
|---|---|---|
| **Thermal Analysis Studio** | A **Thermal** tab: a temperature for every pixel of a thermal (radiometric) drone photo, hot and cold spot detection, heat-flow modelling and inspection reports | `OpenDroneLog-Thermal-Addon_<version>_x64-setup.exe` |
| **Photogrammetry** | A **Photogrammetry** tab: one library for survey photos, videos and Agisoft Metashape outputs, with measuring tools and survey reports | `OpenDroneLog-Photogrammetry-Addon_<version>_x64-setup.exe` |

The add-ons are made by Airwulf, LLC. They are not part of, or endorsed by, the original Open DroneLog project.

**Contents**

- [Before you start](#before-you-start)
- [Install an add-on, step by step](#install-an-add-on-step-by-step)
- [Activate your license](#activate-your-license)
- [Update an add-on](#update-an-add-on)
- [After you upgrade Open DroneLog itself](#after-you-upgrade-open-dronelog-itself)
- [Turn off or remove an add-on](#turn-off-or-remove-an-add-on)
- [Troubleshooting](#troubleshooting)
- [Help with the add-ons](#help-with-the-add-ons)
- [Licenses and source code](#licenses-and-source-code)

---

## Before you start

Check these five things first. Each takes a minute, and together they prevent almost every install problem.

1. **A Windows 11 computer (64-bit).** The add-ons only work in the Windows desktop program. The Open DroneLog web app, Docker version and Android app cannot use them.
2. **Open DroneLog installed with its "setup.exe" installer.** Open DroneLog offers two Windows installers: a *setup.exe* (installs for your Windows account only) and an *.msi* (installs for every account on the computer). The add-ons only work with the **setup.exe** install. Step 1 below shows how to get it.
3. **The right Open DroneLog version.** Each add-on release is built for one Open DroneLog version, and its installer will not run on a newer one. The current add-ons are built for **Open DroneLog 3.3.2**. If you have a newer Open DroneLog, check the [Releases page](https://github.com/AirwulfLLC/open-dronelog-addons/releases) for a matching add-on release.
4. **No administrator password needed.** The add-ons install into your own Windows account, the same way Open DroneLog does.
5. **A license for each add-on you want to use.** Downloading and installing the add-ons is free. A license switches their features on: **$7.99 a month or $75 a year per add-on**, cancel anytime. You can install first and buy the license later from inside the program. Activating a license needs an internet connection once; for a computer that is never online, see [Offline computers](HELP.md#addon-license-offline-computers) in the help file.

> **Words used in this guide**
> - **Installer**: the `.exe` file you download and double-click to add a program to Windows.
> - **Release**: a published version of the add-ons on GitHub. Its installer files are listed under **Assets**.
> - **License key**: the code you get after buying. It switches an add-on on.
> - **Host program**: the add-ons run inside a slightly extended copy of Open DroneLog (the "Airwulf build"). The add-on installer puts it in place for you and keeps a backup of your original program. Your flights, settings and profiles are not touched.

---

## Install an add-on, step by step

Do these steps once for each add-on. If you want both add-ons, install one, then repeat Steps 2 to 7 for the other.

### Step 1: Install Open DroneLog (skip if you already have it)

1. Go to the Open DroneLog releases page: https://github.com/arpanghosh8453/open-dronelog/releases
2. Find release **3.3.2** and open its **Assets** list (click **Show all assets** if the Windows files are hidden).
3. Download the file whose name ends in **`_x64-setup.exe`**. Do **not** download the `.msi` file.
4. Double-click the downloaded file and follow the installer.
5. Start Open DroneLog once to make sure it opens, then close it.

> **Already have Open DroneLog but not sure which installer you used?** Just go on to Step 2. The add-on installer checks for you and stops with a clear message if it finds the `.msi` version. In that case, uninstall Open DroneLog from Windows **Settings → Apps → Installed apps**, then install the `setup.exe` as above.

### Step 2: Download the add-on installer

1. Open this repository's latest release: https://github.com/AirwulfLLC/open-dronelog-addons/releases/latest
2. Under **Assets**, click the installer for the add-on you want:
   - Thermal: `OpenDroneLog-Thermal-Addon_<version>_x64-setup.exe`
   - Photogrammetry: `OpenDroneLog-Photogrammetry-Addon_<version>_x64-setup.exe`
3. Your browser saves it, usually in your **Downloads** folder.

> You can ignore the other files in the release. `addons.json` is what Open DroneLog reads to check for updates, and the `source-….zip` is the published source code.

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
2. Click the **🧩 Add-ons** button (next to **Settings** in the sidebar).
3. Click **↻ Refresh**. Your add-on appears in the list.
4. Make sure **Enabled** is ticked.
5. Close the Add-ons window. A new **Thermal** or **Photogrammetry** tab appears in the sidebar.
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
3. If you already have a key for the other add-on, paste it into the **"Already a customer?"** box so both subscriptions share one account. Otherwise leave it empty.
4. Click **Continue to payment** and pay by card.
5. The thank-you page shows your license key. Click **Copy**, and **bookmark the page**: it is your way back to the key if you lose it.

**To activate the key:**

1. Open the add-on's tab. The lock panel shows **No license**.
2. Click **Enter license key…**, paste the key and click **Activate**.
3. The lock panel disappears and the studio opens. In the **🧩 Add-ons** window, the add-on's row now reads **Licensed until \<date\>**.

Subscriptions renew by themselves. To change your card, see invoices or cancel, click **Manage subscription** in the add-on's row. Each license covers one add-on: a Thermal key does not unlock Photogrammetry.

The help file has the full details, including offline computers and renewal warnings: [Buying, activating and renewing an add-on license](HELP.md#addon-license).

---

## Update an add-on

Open DroneLog checks for add-on updates by itself about once a day. To check now:

1. Open the **🧩 Add-ons** window and click **Check for updates**.
2. If a newer version exists, the add-on's row shows **Update to v\<version\> (\<size\> MB)**. Click it.
3. A progress bar fills while the update downloads and is verified.
4. The row reads **Restarting to apply…**. Open DroneLog closes, installs the update and starts again.

**No internet on that computer?** Download the newest installer from the [Releases page](https://github.com/AirwulfLLC/open-dronelog-addons/releases) on another computer, copy it over (for example on a USB stick), and run it. You do not need to enter your key again.

---

## After you upgrade Open DroneLog itself

If you later install a newer Open DroneLog from the original project's GitHub page, its installer puts the plain program back. Open DroneLog then starts **without** the add-on tabs and without the **🧩 Add-ons** button. Nothing is lost.

1. Download the current add-on installer from the [Releases page](https://github.com/AirwulfLLC/open-dronelog-addons/releases/latest). It must be built for your new Open DroneLog version; an older installer stops and tells you so.
2. Run it (Steps 3 to 6 above). You do not need to enter your key again.
3. Start Open DroneLog. The add-on tabs are back, with your licenses, pictures, reports and settings.

---

## Turn off or remove an add-on

**Hide an add-on for now:** in the **🧩 Add-ons** window, untick **Enabled**. Its tab disappears and its files stay. This does **not** cancel your subscription; use **Manage subscription** for that.

**Remove an add-on completely** (either way works):

- **From Open DroneLog:** in the **🧩 Add-ons** window, click **Remove** on the add-on's row and confirm.
- **From Windows:** open **Settings → Apps → Installed apps**, find **Open DroneLog Thermal Analysis Add-on** or **Open DroneLog Photogrammetry Add-on**, and choose **Uninstall** from its **⋯** menu.

What happens next:

- Your imported pictures, measurements and reports stay in your Open DroneLog profile.
- Your license stays on the computer, so a later reinstall finds it.
- If it was the **last** add-on installed, Open DroneLog restarts with your original program put back. If another add-on is still installed, the host program stays.
- If putting the original back cannot finish, the row reads **Removing … failed**, with **Retry** and **Keep add-on** buttons.

---

## Troubleshooting

When the installer stops, it says why, and it has changed nothing. Find the message below:

| Message | What it means | What to do |
|---|---|---|
| **Open DroneLog was not found. Install Open DroneLog first** | Open DroneLog is not installed for your Windows account | Do [Step 1](#step-1-install-open-dronelog-skip-if-you-already-have-it), then run the add-on installer again |
| **An all-users (MSI) install of Open DroneLog was found. It is not supported** | Open DroneLog was installed with the `.msi` | Uninstall it from **Installed apps**, install the `_x64-setup.exe` (Step 1), then run the add-on installer again |
| **Open DroneLog \<version\> is newer than this add-on's build** | Your Open DroneLog is newer than this add-on release supports | Get a newer add-on release from the [Releases page](https://github.com/AirwulfLLC/open-dronelog-addons/releases), if there is one |
| **Open DroneLog is still running** | The program was open | Close Open DroneLog (check the taskbar) and run the installer again |
| **Another add-on installer or uninstaller is running** | Two installers were started at once | Let the first one finish, then try again |
| **Open DroneLog could not be replaced (the program file is locked)** | Another program is using the Open DroneLog file | Close Open DroneLog, wait a minute or restart the computer, then try again |
| **Windows protected your PC** | SmartScreen warning for a new download | Click **More info → Run anyway** (see [Step 4](#step-4-run-the-installer)) |
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

**[HELP.md](HELP.md)** holds every help guide built into the add-ons (the **?** buttons in the program) in one file with a table of contents: getting started, thermal analysis, measuring, reports, settings and licensing.

For the main Open DroneLog program (importing flight logs, maps, charts, battery tracking and so on), see the original project's [user manual](https://github.com/arpanghosh8453/open-dronelog/blob/main/docs/manual.md).

---

## Licenses and source code

- **Open DroneLog** is free, open-source software by Arpan Ghosh, licensed under the [GNU Affero General Public License v3.0](https://github.com/arpanghosh8453/open-dronelog/blob/main/LICENSE) (AGPL-3.0). Original project: https://github.com/arpanghosh8453/open-dronelog
- The host program that the add-on installers put in place is built from Open DroneLog. Its complete source code is attached to every add-on release as `source-<commit>.zip`, as the AGPL-3.0 requires.
- The Thermal add-on includes the DJI Thermal SDK runtime, which is DJI's software and is distributed under DJI's own terms.
- DJI is a registered trademark of SZ DJI Technology Co., Ltd. Other product names are trademarks of their owners. These add-ons are independent and are not affiliated with or endorsed by those companies.
