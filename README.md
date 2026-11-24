# Tedious

A Minecraft client with its own launcher (Java + Bedrock, Modrinth mods, skins, servers, English and Korean).

## Download

Get the newest version from the download page (GitHub Pages), or straight from **Releases**:

* **Tedious-Setup.exe** (~60 KB) - installer: downloads the full app, installs it (no admin needed; Start menu + desktop shortcut; uninstall in Apps & features)
* **Tedious.exe** (~67 MB) - portable, the whole app in one file (self-contained, needs nothing installed)
* **Tedious-Updater.exe** (~50 KB) - updater / repair: downloads the newest app (SHA-256 checked) and replaces or installs it; keeps the flavour you already have
* **Tedious-NET.exe** (~1.4 MB) - small build that needs the free .NET 10 Desktop Runtime (x64)

Tedious updates itself: *Settings -> Updates -> Check for updates* downloads the newest release for the build you run (`Tedious.exe` or `Tedious-NET.exe`), checks its SHA-256
(the `.sha256` file next to it), and replaces itself. Optional extras are separate assets, downloaded only when needed.

## What is in this repository

Only the download page (`docs/`). The program's source code is **not** published here.
The `.exe` files are **Release assets** and are never committed to git.

## Publishing a new version (maintainer notes)

1. Publish the full app (`dotnet publish -c Release -r win-x64`) -> `Tedious.exe`, and the small one
   (`-p:TediousFlavor=net -p:SelfContained=false -p:EnableCompressionInSingleFile=false -p:PublishSingleFile=true`) -> rename to `Tedious-NET.exe`.
   Build the two helpers with `installer/build.cmd <outdir>` -> `Tedious-Setup.exe`, `Tedious-Updater.exe`.
2. For `Tedious.exe` and `Tedious-NET.exe` create `<name>.sha256` containing the SHA-256 (`Get-FileHash <file> -Algorithm SHA256`).
3. Create a GitHub Release tagged `vX.Y.Z` (same as the app's version) and attach all six files above (optional extras such as
   `stodgy.jar.enc` + `.sha256` too). The release notes become "What is new" on the page.
4. GitHub Pages: Settings -> Pages -> Deploy from branch `main`, folder `/docs`.

Never commit keys, tokens, `english-log`, `out/` or `build/`.

*Tedious is a fan-made project and is not made by or connected to Mojang or Microsoft.*
