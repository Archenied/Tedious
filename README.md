# Tedious

A Minecraft client with its own launcher (Java + Bedrock, Modrinth mods, skins, servers, English and Korean).

## Download

Get the newest version from the download page (GitHub Pages), or straight from **Releases**:

* **Tedious-Setup.exe** - installer (no admin needed; Start menu + desktop shortcut; uninstall in Apps & features)
* **Tedious.exe** - portable, runs without installing

Tedious updates itself: *Settings -> Updates -> Check for updates* downloads the newest release, checks its SHA-256
(the `Tedious.exe.sha256` file next to it), and replaces itself.

## What is in this repository

Only the download page (`docs/`). The program's source code is **not** published here.
The `.exe` files are **Release assets** and are never committed to git.

## Publishing a new version (maintainer notes)

1. Build the portable `Tedious.exe` and the installer `Tedious-Setup.exe` (`installer/build.cmd` in the source folder).
2. Create `Tedious.exe.sha256` containing the SHA-256 of `Tedious.exe` (`Get-FileHash Tedious.exe -Algorithm SHA256`).
3. Create a GitHub Release tagged `vX.Y.Z` (same as the exe's version) and attach all three files. The notes text becomes "What is new" on the page.
4. GitHub Pages: Settings -> Pages -> Deploy from branch `main`, folder `/docs`.

Never commit keys, tokens, `english-log`, `out/` or `build/`.

*Tedious is a fan-made project and is not made by or connected to Mojang or Microsoft.*
