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

## Changes in 0.99.13

- Adds large **B Cancel** and **A Exit** buttons inside the quit confirmation
  box, with touch support. The footer keeps the same choices as well.
- Uses opaque button backgrounds and ordinary text for A/B so the choices do
  not depend on a controller-symbol font or on seeing the bottom of the screen.
- The tester has confirmed that 0.99.12 cancels correctly and exits to HOME
  without the closing error. This update changes the button presentation.

Also includes the 0.99.12 changes:

- Adds the quit confirmation: "Are you sure you want to quit?" Press B to
  cancel or A to exit; the footer buttons also support touch. Cancel keeps
  your current screen and selection. Active installations retain their exit guard.
- Fixes the embedded HOME application's shutdown path to use libnx's orderly
  application exit instead of returning to the loader as an ordinary NRO.
  Successful RetroArch core handoffs keep the loader-return behavior.

The 0.99.10 to 0.99.11 automatic HOME update, restart and launch are confirmed
by the tester, as is closing 0.99.12 without the earlier system error.
The new on-dialog buttons in 0.99.13 still need a physical Switch check.

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
