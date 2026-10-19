# Tinfoil Reborn

By **TechRepairs4U**. An independent Nintendo Switch homebrew application.

This repository hosts compiled releases and user instructions. Application
source code is not stored in this repository or attached to its releases.

## Download and install

Download the latest **Tinfoil-Reborn** release ZIP from Releases. It contains:

- `Tinfoil-Reborn.nsp`: a standalone HOME-menu application, with the executable,
  icon and UI assets embedded. It is not an NRO forwarder.
- `switch/foil/foil.nro`: the homebrew-menu version and companion for installing
  future NSP updates.
- License notices and the source-on-request offer.

Copy the `switch` folder to the microSD root. Install `Tinfoil-Reborn.nsp` with
your existing homebrew installer, or with Reborn's NRO using title override.
The NSP title ID is `0500545242550000`; the author is `TechRepairs4U`.
Both versions share settings, shops and cached artwork in `/switch/foil`.
No shops, accounts, games, console credentials or firmware are supplied.
The NSP requires a CFW setup capable of running unsigned homebrew applications.

## App updates

Choose **Options > Check for app updates**. New releases are fetched from this
repository over HTTPS and checked against their declared size and SHA-256.
Updates are downloaded only after you choose Download.

- NRO: updates the NRO you launched, preserving the old file as a `.previous`
  backup. Close and reopen Reborn after completion.
- HOME/NSP: downloads and verifies the new NSP. Close Reborn, launch the NRO
  through the homebrew menu using a different title, and select **Options >
  Install downloaded app update**. Confirm Install, then reopen the HOME app.
  The currently running HOME title is deliberately protected from replacement.

The first standalone NSP release is **0.99.8**. Its package structure, metadata
digest, executable, resource hashes and updater have been checked on PC.
Installation and launch of this new NSP on physical hardware remain unverified.
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
