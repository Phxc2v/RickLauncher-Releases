# RickLauncher

A launcher for **Mount & Blade II: Bannerlord** — one place to launch several game versions (1.2, 1.3, 1.4.5 …), each with multiple mod sets ("builds"), with separate saves, configs and shaders.

Version: **1.1.0** · what's new in `CHANGELOG.en.md`.

## Features
- Detect installed games on disk + add manually.
- A **game → builds** tree: each game has a "Native" (vanilla) build plus your own mod sets.
- **Import data from the game:** on first detecting a game (or manually from the profile menu) the launcher imports your saves, mod (MCM) settings and your actual enabled-mod list and order into the profile — so you can just continue playing. Graphics/engine settings are left untouched (so it can't break rendering/shaders).
- **GPU hint:** on hybrid laptops, if the game is set to the weak integrated GPU, the launcher offers to switch to the discrete card before a launch or shader bake.
- Mod management: enable/disable, **load order** (critical for Bannerlord), auto-order by dependencies, dependency and conflict checks.
- **Install mods** from an archive, a folder, or a URL (GitHub/ModDB/direct); auto-fetch missing dependencies (Harmony/ButterLib/UIExtenderEx/MCM) from GitHub. If a mod is already on disk (another profile, the game folder, Steam Workshop) it's added instead of re-downloaded — always taking the **newest version by number**.
- **Recommended mods:** a profile button — recommended mods (Crash Doctor, RTS Camera Universal, TOR Russian translation, Lore-Hardcore) install in one click. Only the ones that fit the build and aren't installed yet are shown; nothing is forced, and each has a "Read" link.
- **`.rickpack` mod packs** — share a ready-made mod set as one file; standalone pack editor (`RickPackEditor.exe`). You can **create a pack straight from a profile** (profile menu → "Create a pack from this profile"): the launcher fills in the mod links it remembered at install time. Ready-made packs ship with the launcher (the `Packs` folder) — "Install mod pack" opens it straight away.
- **Fully autonomous:** mods you add live in the launcher's catalog and are composed into the game only for the duration of a launch — the game folder and the player's existing mods/settings are never changed. Once the launcher is closed everything runs "as before".
- **Isolation** of saves and mod (MCM) settings **per profile**, and shaders per version.
- **Interface languages:** Russian and English (add your own — files in the `Lang` folder). Pick the language in Settings; it applies instantly.
- **Auto-update:** on launch the app checks for a newer version and updates in one click. GitHub first, and if it's unreachable (e.g. blocked) — from our backup server (same for our mods). A "Download from GitHub" toggle is in Settings.
- Skins (Calradia, Cinematic), export/import of all settings (`.rlbak`).
- Mod description tooltip on hover (from the mod's README — or, if it has none, pulled from GitHub/Nexus on a URL install, or from the pack).
- **TOR shader baking** ahead of time, with a progress bar and ETA ("🧱 Build shaders" button).

## How to use
1. Run `RickLauncher.exe`.
2. On first run, allow the game scan (or add a game folder manually via "＋").
3. Pick a game and build on the left; optionally click "🧩 Configure mods".
4. Press **"PLAY"**.

## Deleting mods
The launcher tracks **who installed a mod** and deletes accordingly, so it can never wipe files it didn't put there:

- **Mods you added through the launcher** (via "Add mod" from an archive/folder/URL, or installed by a `.rickpack` build) live in the launcher's catalog, as a separate copy per profile. Removing such a mod from a build **physically deletes it from disk** — but only this build's copy; other builds and clones keep their own copies.
- **Mods sitting in the game's `Modules\` folder** (e.g. Fast Mode, Birth and Aging Options — placed there by hand or shipped with a repack) and Steam Workshop mods are treated as the game's "native" mods. Removing them from a build only **hides** them; the files on disk are left untouched — the launcher never deletes what it didn't install.
- **Official modules** (Native, SandBox, StoryMode, …) are never touched.

The delete button picks the right behaviour automatically and shows the matching confirmation — "Delete from disk" or "Remove from build". A hidden mod comes back by simply adding it to the build again.

**Deleting a profile.** If a profile has its own (launcher-added) mods, the launcher offers a choice: "Delete profile + mods" (wipes them from disk, except ones still used by other profiles) or "Profile only" (mods stay on disk — re-installing the same build is then instant, with no re-download).

## Requirements
- Windows 10/11 (64-bit). **No .NET install required** — the build is self-contained.
- An installed copy of Bannerlord.

## Data & portability
- All launcher data lives in a **`RickLauncherData`** folder next to `RickLauncher.exe`. You can move the launcher together with that folder.

## Note about OneDrive
If your Documents folder is redirected into OneDrive, save isolation for it is **disabled** (to avoid corrupting cloud files) — the launcher will warn you. Moving Documents out of OneDrive is recommended.

## Feedback
Report issues with: what you did, what you expected, what happened. Attach the files from `RickLauncherData` if possible.
