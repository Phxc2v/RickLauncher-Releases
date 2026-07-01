# What's new in RickLauncher

> Plain-language notes on what changed in each version.

## 1.0.8

A big update after 1.0.4 — lots of new features and a pile of fixes.

**Highlights**
- 🎮 **Bring your data over from the game** — the launcher no longer starts "factory-fresh": on first detecting a game it imports your **saves, mod (MCM) settings** and your **actual enabled-mod list and load order** into the profile. Just continue playing. Already had a profile? The "⋯" menu has **"Import my data from the game"**. The import leaves graphics/shaders **untouched** — and there's nothing to rebake afterwards (the launcher tells you so).
- ✨ **Our mods** — a new button on the profile card: our mods (Crash Doctor, RTS Camera Universal, TOR Russian translation, Lore-Hardcore) install in one click. Only the ones that **fit this build and aren't installed yet** are shown — nothing is forced. Each has a **"Read"** link to Nexus/GitHub. The TOR Russian translation is only offered when the UI is Russian. RTS Camera Universal disables the conflicting originals it replaces (RTS Camera / Command System / Mini Map).
- 🧰 **Mod packs — from a profile and bundled** — create a pack straight from a profile ("⋯" → "Create a pack from this profile", with mod links). And ready-made packs now **ship with the launcher** — "Install mod pack" (and the editor's "Open") open that folder straight away.

**Downloads & updates**
- 🌍 **A backup server when GitHub is unavailable** — launcher updates and our mods are fetched from **GitHub first**, and from **our own server** automatically if GitHub can't be reached (e.g. it's blocked). So updates keep working even where GitHub is closed. Settings has a **"Download from GitHub"** toggle (on by default): turn it off to use our server only. Every download from the server is checksum-verified.

**Stability & shaders**
- 🧱 **Fixed a crash on launch after import + shader bake** (on TOR's main mod screen). Cause: shaders were baked only for the mods enabled in the profile, so the cache was missing some. Baking now covers **all installed mods** — the cache is complete and the launch doesn't crash. (If a version already hit this, clear the shader cache and bake again.)
- 🧱 **Rebuild-shaders hint** — the launcher notices when the installed mod set changed and suggests a rebake. Baking always drops shader quality to minimum (less memory, fewer crashes).
- 🖥 **GPU hint (hybrid laptops)** — if the game is set to the weak integrated GPU, the launcher offers to switch to the discrete card before a launch/bake (the integrated one tends to crash with `create_texture_array`).

**Mods**
- 🔁 **Smart adding** — if a mod is already on disk (another profile, the game folder, Steam Workshop) it's **not re-downloaded** — it's added. It takes the **newest version by number**; when you re-add, the launcher checks the server/GitHub for a newer version and downloads it instead of resurrecting an older on-disk copy.
- 🔢 **Auto-placed in the load order** — a mod you add drops into the right spot in the load order (before anything that depends on it), not just at the end. The rest of your order is left alone.
- 🧩 **Optional dependencies** — mods with an optional dependency (e.g. Lore-Hardcore without Crash Doctor) are no longer blocked by a demand to install it.
- 📝 **Mod description on hover** — even for mods without their own README, it's fetched automatically on install. It's taken **in your UI language** (English only when there's no translation), and a LICENSE is no longer shown instead of a description.

**UI**
- ✏️ Renamed: "Standard" → **"Native"**, "Your mods" → **"Your modlist"**; a **"＋"** button next to each game's gear for quickly creating a profile.
- 🖥 **The launcher window no longer gets lost off-screen** — if its saved position is outside the screen or behind the taskbar (e.g. after unplugging a monitor), it opens centered on the primary monitor.
- 🎛 Touches: removed the white title strip on several windows; mod descriptions wrap to the next line; no more blurry popup text; the "what will launch" list uses the full height; wider sidebar; fixed deleting shaders from the profile menu.

## 1.0.4

- 🧱 **Shader baking fixed** — no more endless "build shaders" loop. The shader cache could previously get split (part in the launcher folder, part in the system folder), so the game didn't see the finished shaders. Now everything lives strictly in the launcher catalog and pre-built shaders are always picked up. Old "lost" data from earlier versions is migrated back into the catalog automatically on startup.
- 📦 **Re-installing a mod pack** no longer re-downloads gigabytes: if a mod is already installed and the version matches, it's simply re-linked — no download, no extraction.
- 🗑 **Deleting a profile** now asks whether to also delete its mods from disk (except ones still used by other profiles) or keep them. Keep them and re-installing the same pack is instant.
- 🧹 Clearing the shader cache now always clears the selected version.
- 🎛 UI touches: the header shows the full build number; the "Cancel" button is now on the right; confirmation dialogs are wider.

## 1.0.3

- 🗂 **All files** (shaders, mods, saves, settings) now live in the launcher folder. If the launcher is inside OneDrive, the folder is automatically taken out of sync so OneDrive can't corrupt anything.
- 🧱 Fixed: the game didn't see the pre-built shaders and recompiled them every launch. Now it picks them up.
- ⬇ Mod and dependency downloads show a progress bar and speed; a dropped connection no longer hangs — it resumes where it stopped.
- 🧩 Dependencies no longer install incorrectly.
- 🛠 Error log (`RickLauncherData\logs`) and crash resilience; many small fixes.

## 1.0.0 — First version

The first public release of RickLauncher. In short, it can:

- 🎮 Find your installed Bannerlord games and launch different versions and mod sets ("builds") from one window.
- 🧩 Manage mods: enable/disable, reorder, auto-order, dependency and conflict checks.
- 📦 Install mods from an archive, a folder or a link. Share a ready mod set as a single file (`.rickpack`).
- 🛡 Your mods and saves stay separate and never mess up the game's own files.
- 🌍 Languages: Russian and English (you can add your own). Pick the language in Settings.
- ⬆ Auto-update: the launcher tells you when a new version is out and updates in one click.
- 🧱 Pre-build shaders for TOR mods ahead of time — with a progress bar.
