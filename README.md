# Tinfoil Reborn

By **TechRepairs4U**. An independent Nintendo Switch homebrew application.

This repository hosts compiled releases and user instructions. Application
source code is not stored in this repository or attached to its releases.

## Download and install

Download the latest **Tinfoil-Reborn** release ZIP from Releases. It contains:

- `Tinfoil-Reborn.nsp`: a standalone HOME-menu application, with the executable,
  icon and UI assets embedded. It is not an NRO forwarder.
- `switch/foil/foil.nro`: the homebrew-menu version. It can also install the
  standalone application or recover a downloaded update.
- License notices and the source-on-request offer.

Copy the `switch` folder to the microSD root. Install `Tinfoil-Reborn.nsp` with
your existing homebrew installer, or with Reborn's NRO using title override.
The NSP title ID is `0500545242550000`; the author is `TechRepairs4U`.
Both versions share settings, shops and cached artwork in `/switch/foil`.
No shops, accounts, games, console credentials or firmware are supplied.
The NSP requires a CFW setup capable of running unsigned homebrew applications.

## Changes in 0.99.28

- Background file-transfer outcomes reach Console even after their Queue rows
  have been cleared. Finished downloads and failures are reported once.
- A failed retry reports its new outcome. Queue-file save errors are reported
  without repeating an unchanged error, and completed files are retained.
- Pause and cancellation use Debug logging; failures remain visible at Error.
  The same filtering applies to Console and the saved log.

Validated with bounded original worker-lifecycle instructions, controlled HTTP
responses, real transfer workers, Console/disk logging and Queue UI regressions.
Physical Switch validation and full parity remain pending. General alternate-source
retries for title installation remain unfinished.

Also includes the 0.99.27 changes:

- A/tap selects a Queue row without pausing an active or waiting job.
- ZL/ZR page Queue instead of switching sections, with matching footer touch buttons.
- Active Status cells show progress bars; speed uses decimal MB/s.
- Package names use the existing language-aware display cleanup; finished installs
  show Complete. Ordinary transferred filenames keep their names.
- Paused jobs and interrupted installs retain explicit A Resume/Recover actions.
  Ordinary Queue rows no longer expose an extra R Details action.

Validated against bounded original Queue instructions, synthetic jobs and desktop
controller/touch scenarios. Physical Switch rendering and full parity remain pending.

Also includes the 0.99.26 changes:

- Queue uses X Delete for the selected job and Y Delete All for the list.
- Delete All removes waiting work and dismisses active rows. Operations already
  running continue in the background; a message explains this behavior.
- Completed download files are retained. Recovery errors stay visible, and
  active work still blocks an app update even after its row is dismissed.
- Queue controls were further aligned in 0.99.27 as described above.

Verified with original Queue instruction checks, a controlled local download,
synthetic installer/queue tests and desktop input scenarios. Physical Switch
validation and complete control/feature parity remain pending.

Also includes the 0.99.25 changes:


- Install All continues past named catalog files already in the install queue,
  and reports how many requests were already queued.
- Newly selected updates and DLC still queue when their base game is pending.
- Replacing a queued update with a newer version preserves other selected
  files attached to that job.

Verified with original queue instructions, synthetic installer/queue tests
and desktop controller/touch scenarios. Switch validation remains pending.
Inspected bundles retain explicit error handling. Complete feature parity
is still in progress.

Also includes the 0.99.24 changes:

- Install All can queue more than 128 titles. Saved queues support the larger
  list as well.
- Retains the existing queue storage-size budget, duplicate checks, recovery
  protection and worker limits. An oversized submission preserves earlier jobs.
- Keeps the requested queue clearing at every boot.

Verified against the original queue-growth routines and with synthetic queue,
production UI and installer tests. Physical large-queue testing and complete
feature parity remain pending.

Also includes the 0.99.23 changes:

- Catalog Install All skips already registered extras when automatically
  expanding later titles in the batch.
- Explicitly selected updates still queue, even when an older version is
  registered. The first title's reviewed file checkboxes remain unchanged.
- Retains latest-version selection and skips duplicate title/version requests.

Verified against the original related-title callback with synthetic inputs
and desktop menu/queue regressions. Physical Switch validation and complete
feature parity remain pending.

Also includes the 0.99.22 changes:

- In game catalogs and ROM lists, Plus opens Sort and Minus changes view.
  The footer supports the same controls by touch. Sidebar Plus remains Search.
- X Install All opens the Install Menu for the current filtered game list.
  Confirm Install to queue those titles with the selected options. Only the
  latest update is selected; partial queue failures report how many were added.
- The left file pane shows the first title's base/update/DLC choices.
- Fixes install recognition when shops send display names separately from
  package filenames. ROM lists ignore X.

Verified against original control/dispatch routines and desktop menu, touch,
queue and theme tests. Switch validation, bulk source-selection edge cases
and complete feature parity remain pending.

Also includes the 0.99.21 changes:


- In Installed, Plus opens Sort and Minus changes view, matching the original
  controller routing. The cycle is normal icons, small icons, then list.
- Remembers Installed's view independently after restarting.
- Shows the corresponding footer labels with touch controls. Sidebar Plus
  still opens Search; the other Installed actions remain available.

Verified against original input routines and desktop controller/touch/restart
flows in Dark, Light and Atmosphere. Physical Switch validation and complete
feature parity remain pending.

Also includes the 0.99.20 changes:

- Each game catalog and ROM system remembers its own view: normal icons,
  small icons or list. Switching another section no longer changes it.
- Restores those choices after restarting while retaining your previous
  global preference for sections you have not changed.
- Uses the active section's icon size for controller navigation, captions,
  touch hit regions and scrolling, including custom themes.
- Keeps fallback names below the placeholder symbol on small tiles when
  artwork is unavailable.

Verified against original view/configuration routines, local settings fixtures
and production controller/touch flows. On-console validation and complete
feature parity remain pending.

Also includes the 0.99.19 changes:


- Remembers sorting separately for Installed, New Games, New Updates, New DLC,
  XCI, Recommended, Incomplete and each ROM system.
- Restores each section's field and direction after restarting. Changing one
  section no longer changes another section or File Browser's direction.
- Preserves your existing order for sections you have not changed yet.
- Reuses prepared lists when switching between sections with different sorts.

Verified against the original per-view configuration lookup, settings migration,
local catalogs and production controller/touch flows across restarts. Physical
sorting validation and complete feature parity remain pending.

Also includes the 0.99.18 changes:

- Preserves the original order of tied games when changing sort fields, and
  matches the original reversal of tied rows when sorting descending.
- Keeps prepared ordering when revisiting a section or rendering another
  frame. Installed reuses its prepared list instead of sorting every frame.
- Matches missing-rank handling while retaining an explicit server rank of
  zero. Existing catalog caches still load without a forced redownload.
- Keeps unavailable Incomplete rows attached to the correct titles when the
  sort direction changes. ROM systems retain their own prepared row order.

Verified against original sort routines, local catalog/cache fixtures,
production controller/touch flows and native compilation. Physical sorting
validation and complete feature parity remain pending.

Also includes the 0.99.17 changes:

- Matches game-list size labels to the original decimal units and precision,
  including compact labels such as `14 GB` and `0.8 MB`. A zero recorded size
  displays `0.0 B`.
- Centers Region and right-aligns Version/Size within consistent cell padding.
- Uses the base game's name and region for updates; DLC rows show
  `base game - DLC name` and the base game's region. English-name preferences
  still apply. The Install Menu keeps its simplified names.
- Matches ordinary content and system-version title text, including `23.0.1`,
  and uses the original common Type/Version fields in ROM lists.

Verified against original formatter routines, local metadata and a loopback
shop through the production renderer, plus native compilation. Physical
verification and complete feature parity remain pending.

Also includes the 0.99.16 changes:

- Matches Installed's list columns to the original: Name, Type, Version,
  Region, Size and Released. The name column expands when the sidebar closes.
- Uses the same column spacing and row rendering across Installed, shop and
  ROM lists. Installed uses its local content version and available title
  metadata. Version 0.99.17 updates these size labels as described above.

Verified against both original column constructors, desktop UI checks and
native compilation. Physical Switch verification of this layout is pending.

Also includes the 0.99.15 changes:

- Adds Last Used sorting from Switch application records, including Installed.
- Adds sorting to Installed and retains region, release date, rank and size
  metadata for its available columns.
- Uses the original eight-field sort selector. Selecting the current field
  again reverses its order; selecting a different field starts ascending.
  All choices fit above the footer and accept controller or touch input.
- Timestamp changes refresh sorted catalogs; normal section switches reuse
  the prepared lists.
- Matches the original Type and Region ordering, including its Version-column
  comparison. Latest-update installation still selects the highest version.

Verified using synthetic execution of the original routines, a local shop,
the production controller/touch UI and native compilation. Physical Switch
verification and full feature parity remain pending.

Also includes the 0.99.14 changes:

- Makes Released, Rank and Region sorting work in RetroArch ROM sections.
- Retains rank metadata provided by a server and follows the original region
  ordering and size comparison.
- Prepares display-name sort keys once per list, reducing repeated work when
  sorting large ROM catalogs.

Verified with a local test server, the actual controller/touch menu, original
comparison routines and native Switch compilation. Physical ROM/core testing
and remaining parity work are still pending.

Also includes the 0.99.13 changes:

- Adds large **B Cancel** and **A Exit** buttons inside the quit confirmation
  box, with touch support. The footer keeps the same choices as well.
- Uses opaque button backgrounds and ordinary text for A/B so the choices do
  not depend on a controller-symbol font or on seeing the bottom of the screen.
- The tester has confirmed that 0.99.12 cancels correctly and exits to HOME
  without the closing error. This update changes the button presentation.
- The tester has also confirmed that both on-dialog buttons are visible on
  the Switch after installing the visibility fix.

Also includes the 0.99.12 changes:

- Adds the quit confirmation: "Are you sure you want to quit?" Press B to
  cancel or A to exit; the footer buttons also support touch. Cancel keeps
  your current screen and selection. Active installations retain their exit guard.
- Fixes the embedded HOME application's shutdown path to use libnx's orderly
  application exit instead of returning to the loader as an ordinary NRO.
  Successful RetroArch core handoffs keep the loader-return behavior.

The 0.99.10 to 0.99.11 automatic HOME update, restart and launch are confirmed
by the tester, as is closing 0.99.12 without the earlier system error.
Both on-dialog buttons from 0.99.13 are now confirmed visible on the Switch.

Also includes the 0.99.11 changes:

- Adds an embedded loader to the standalone NSP for launching installed
  RetroArch cores. Reborn stays inside the NSP; an SD copy of Reborn is not
  needed to open it from HOME. Cores and ROMs are not bundled.
- Returning from a core reloads Reborn. Exiting Reborn returns to HOME.
  Missing, incomplete or invalid core files return to Reborn with an error.
- Keeps the NSP updater and packaged UI resources active when Reborn is
  running through its embedded loader. The separate NRO keeps its normal
  homebrew-menu behavior.

The RetroArch core launch/return has passed host boundary tests and native
compilation, but still requires a physical Switch test.

Also includes the 0.99.10 updater changes:

- Checks for updates in the background at launch and announces a newer release.
  Choose A to update, or B to continue using Reborn. Offline checks stay quiet.
- After downloading and verifying an update, closes active resources, applies
  the update and requests a restart. HOME updates use the existing transactional
  installer with fixed app-update settings and preserve the old content.
- NRO updates replace the executable after its RomFS and fonts have closed;
  the previous executable is retained beside it as a `.previous` backup.
- Interrupted HOME updates recover their transaction before the main UI starts.

Also includes the 0.99.9 changes:

- USB starts before theme and network initialization. Windows capacity queries
  no longer scan the Firmware export before displaying the device.
- Selecting Hekate on OLED or Mariko offers a reboot into the Hekate menu.
  Other payloads can then be selected in Hekate.
- Idle MTP disconnects automatically before reboot; an active file transfer
  must finish first. USB is restored if the reboot request fails.

The changes compile for Switch and pass PC regression checks. MTP discovery
speed and OLED Hekate reboot still need confirmation on a physical console.

## App updates

Reborn checks in the background at launch. You can also choose **Options >
Check for app updates**. New releases are fetched from this
repository over HTTPS and checked against their declared size and SHA-256.
Updates are downloaded only after you choose Download.

- NRO: closes resources, replaces the NRO you launched, and reloads it when the
  homebrew loader supports this. Otherwise reopen it after the update completes.
- HOME/NSP: installs the verified NSP in the application's current storage and
  requests a restart. The app updater never replaces the running NCA files;
  ordinary game installations still refuse to replace the running title.
- Failed downloads or verification do not install anything. The verified NSP
  remains available under **Options > Install downloaded app update** for retry.

**Upgrading from 0.99.8 or 0.99.9:** install 0.99.10 or newer once, because the old HOME
updater only downloads its NSP. You can use Reborn's NRO through the homebrew
menu or another homebrew installer. Subsequent releases use the new automatic
apply flow after you accept the update.

The first standalone NSP release is **0.99.8**. Its package structure, metadata
digest, executable, resource hashes and updater have been checked on PC.
The author has confirmed that 0.99.8 opens from HOME on an OLED Switch.
The tester has confirmed the 0.99.10 to 0.99.11 HOME self-update and restart.
The standalone RetroArch loader added in 0.99.11 still requires console
verification; the NRO version continues to use the homebrew menu's loader.
This is a development release, not a claim of complete Tinfoil or firmware parity.

## License and source requests

The combined application includes GPLv2 components. License notices and a
three-year written source offer are included with the release. To request the
complete corresponding source, open an issue here addressed to TechRepairs4U
and identify the release version. Source is supplied separately, not uploaded
to this repository. See `SOURCE-OFFER.txt` for the full offer.

Tinfoil Reborn is not affiliated with or endorsed by Nintendo or the original
Tinfoil developers. Third-party components and resources retain their owners'
licenses and notices.
