# What's new in RickLauncher

> Plain-language notes on what changed in each version.

## 1.1.3.5

**Mods**
- 🔄 **The launcher now notices when a mod has been updated.** Each profile keeps its own copy of every mod, so a Steam Workshop update (or a newer version that showed up in another profile, in the game folder or in a pack) never reached the profile by itself. Switching to a profile now quietly compares versions: if a newer copy is on disk, the mod is highlighted in the "will launch" list with an "↑ new version" tag, and an **"Update mods"** button appears on the main screen. Updating replaces the profile's copy while keeping its load order and enabled state; other profiles stay on their own versions.
- 🌐 **Our own mods now tell you about new releases.** Crash Doctor, RTS Camera Universal, the TOR Russian translation and Lore-Hardcore are checked against their published releases (GitHub first, our backup server if GitHub is unreachable). When a newer release exists the mod gets a **"new release"** tag and installs in one click, exactly like it does from "✨ Our mods". If a suitable copy is already on your disk, that one is used and nothing is downloaded.
- ⚓ **Official DLCs (War Sails, Birth & Aging Options, Fast Mode) can finally be removed from a profile.** A removed DLC used to come back — merely unticked — every time the mod list was rebuilt. Now it disappears, and you can bring it back from "Add existing mod", where such DLCs are listed as "Game DLC". No game files are copied or deleted; only the profile's contents change.
- 🩺 **Crash Doctor no longer nags about an update forever.** Its releases are tagged by date, which the launcher read as a huge version number — so the installed mod always looked outdated and was re-downloaded on every install. Versions are now read correctly.
- 🔁 **Mods that never bump their internal version stop offering the same update again and again.** RTS Camera Universal is exactly that case. The launcher now remembers which release it installed into a profile and won't offer it twice.
- 💾 **Updating a mod no longer wipes what the mod itself accumulated.** Installing or updating used to delete the profile's copy of the mod folder and copy it again from scratch — taking with it everything the mod had written inside itself. For Crash Doctor that meant crashes captured during play disappeared, while crashes the player had deleted came back from the stale copy. An update is now applied on top (only the code in `bin` is replaced), and a mod's live folders live in a separate launcher store linked back into every copy — shared by all profiles of that game and surviving any update or reinstall. Game and mod settings (MCM, saves) are still kept per profile as before.
- 🎯 **Updating a mod inside a pack profile now actually reaches the game.** The list showed the new version (Crash Doctor 1.8.1.3, say) while the game kept loading the pack's old one (1.7) — the profile's updated copy never made it into the game. The profile's copy now always wins over the pack's: what the list shows is what launches. The pack itself is left untouched, so reinstalling it still restores the original.
- 🧹 **No more leftover duplicate folder after a mod update.** When a new release renamed its folder, the old one used to stay behind and the launcher could pick the wrong one. The stale copy is now removed.

**Mod packs (.rickpack)**
- 🔢 **Installing the same pack again no longer damages the profile you already built.** The launcher used to quietly rebuild the same mod folder and add a second profile with an identical name — there was no way to tell them apart. It now asks: **install another copy** (its own "… 2" profile and its own mod folder, the existing one untouched) or **reinstall over it** (the old profile of this pack and its mods are deleted). Copies never interfere and may hold different versions of the same mods. An already-installed pack is recognised by its name too, so a re-export that changed the pack's internal id is still spotted as the same pack.
- 👀 **You can see which mod is being installed right now.** The current mod is outlined, the list scrolls to it, and the footer reads "Installing: name — mod 7 of 19". Each mod now shows its author too.
- ⚡ **Installing a pack is noticeably faster.** The built-in browser used to restart and reload the Nexus page from scratch before every single mod — ten long pauses for a ten-mod pack. One window is now shared across the whole pack. A false alarm is gone too: a slowly loading page is no longer treated as stuck and pointlessly reloaded.
- 🔑 **Settings now show that your Nexus login actually works.** It used to be blank, or claim "signed in" months after the session had expired. It now shows the account name (when it can be detected) and the date the session was last confirmed by a real Nexus page, and the flag clears itself as soon as a signed-out page is seen.
- 🔑 **Installing no longer hangs when you're not signed in to Nexus.** The launcher sometimes mistook a signed-out visitor for a signed-in one and silently waited for a download button that guests never get. Sign-in is now detected correctly, and if something does go wrong the login window appears right away instead of after ten minutes of silence.
- 🧩 **Fixed the install hanging on certain mods (Mod Configuration Menu and the like).** Nexus now hands some files back through a new-style link — no extension, from a new CDN. The launcher didn't recognise it and got stuck on a mod like MCM, spinning uselessly for up to ten minutes. Those links now download normally.
- 📡 **You can see what the built-in browser is doing while it downloads.** Instead of a frozen "Downloading via browser…", the mod row now moves through stages: "Getting the file link…", "Downloading the file…", "Checking Nexus…". And if the file still fails, the install no longer hangs forever — the mod is honestly flagged and the launcher moves on.

**Profiles**
- 👯 **Cloning a profile now has progress, detail and a Cancel button.** A clone is made with all its saves, settings and mods and can be tens of gigabytes — before, only a status line showed during the copy and it looked like "cloning doesn't work". A window now shows a progress bar and speed, and the list shows what's being copied right now (saves, settings, then each mod in turn). **Cancel** removes the half-finished copy, so no junk is left behind. Clicking "Clone" again no longer starts a second clone at the same time.
- 🔢 **Correct mod count when deleting a profile.** The delete confirmation showed an inflated number (e.g. "19 mods" for a 16-mod profile) — updated mods were counted twice: the copy in the profile and the original in the pack. It now counts unique mods.
- 🧹 **The launcher tidies up "orphaned" mod copies on its own.** Interrupted clones and deleted profiles could leave full copies of mod lists on disk that nothing references any more (one tester had piled up nearly 60 GB). Now a profile's own mod folder is removed as soon as the profile is deleted, and on startup the launcher clears any orphaned copies — carefully: if the profile list can't be read, it touches nothing.

**Interface**
- ✨ **The "Update" button catches your eye.** When an update is found, the button now gently shimmers with a golden glow and pulses a little — hard to miss.
- 🐢 **A slow Nexus download no longer looks like a freeze.** Nexus caps free accounts at roughly 1–2 MB/s. When a download steadily sits at that ceiling the launcher says so — in the download window and in the pack-install window. While the speed is normal, no note appears.
- 📐 **The launcher window can no longer be squashed to a sliver.** Dragging an edge shrank it down to almost one pixel — the minimum size was being ignored (the "maximize to the work area" fix had disabled it). The minimum is enforced again, including on scaled displays. The built-in browser window got a minimum size too.

**Under the hood**
- 🛡 **Many small reliability fixes from a code audit.** Downloads can no longer silently hang forever; an interrupted download won't be appended onto the wrong file; reinstalling a pack won't install an old cached version of a mod; and an archive that isn't a mod is honestly flagged as an error instead of a fake success. These are all internal — invisible day to day, but they make things steadier.

**Launcher updates**
- 📜 **The "update available" window now shows everything you missed.** The changelog is read from the history file (GitHub first, our backup server when GitHub is unreachable) and lists **every version released after yours**, not just the newest one. Five versions behind? You'll see all five, with a scrollbar.

## 1.1.0

A big round of fixes after 1.0.8 — straight from your reports.

**Stability & settings**
- 🖥 **Fixed the "stretched screen" and random crashes when switching between builds.** The cause was a config desync when your Documents folder lives in OneDrive: the game sometimes started with a stale config (wrong resolution) and crashed on heavy mods. The correct config is now always applied.
- 💾 **In-game settings persist between sessions.** Before, you could change settings in-game, quit, relaunch — and get the old config back. Changes are now saved — but **only if the game exited cleanly** (a crash won't save a broken config over your good one).
- 🧱 **Shader baking no longer "hangs forever" if the game crashes.** Previously the crash-report window was hidden (the game is minimized during a bake), so the launcher thought it was still baking. It now detects that, aborts, and tells you plainly (whatever was already built is kept — just rerun to catch up).
- 🩹 **Crash Doctor sees crashes again** for games launched through the launcher. The launcher was wrongly clobbering the symlink Crash Doctor uses to redirect the crash folder to its cache — it now stays out of that folder when Crash Doctor is enabled.
- ⚓ **Optional official DLCs** (War Sails, Birth & Aging Options, Fast Mode) work correctly again. They used to be offered as "deletable" and then re-installed by copying tens of GB (breaking launch) — or, conversely, force-loaded in a game version where you hadn't enabled them. They're now proper on/off checkboxes in the mod list, loaded from the game install and never copied.

**Mods & downloads**
- ⬇ **Fixed Nexus downloads for mods with dependencies** (e.g. translations): the requirements popup used to block the download — now it works.
- 📄 **Translations and patches** (archives with no `SubModule.xml`) no longer throw a cryptic error: the launcher explains it isn't a standard mod and **opens the folder with its files** so you can drop them into the target mod by hand.
- 🩺 **Crash Doctor now sees your launched mods as enabled** on its "Mods" tab (they used to show as off).
- 📊 **Progress bar when installing mods from an archive/folder.** Big packs (hundreds of mods, tens of GB) now show the **extraction** and **install** progress ("Installing mod X/N") — so it's clearly working, not frozen. The install can be cancelled.
- ⚙️ Fixed per-profile **mod (MCM) settings** isolation.
- 🗂 **"Add existing mod" no longer offers mods from other game versions.** It now lists only the current version's mods — so the "compatible only" checkbox was removed as redundant.

**Interface**
- 🔤 **Fixed blurry text** in context menus, hover tooltips and dropdown lists (popup text was soft/smeared).
- 🧩 **Disabling a mod — new "Only this one" option.** Before, disabling a mod with dependents forced you to either disable everything or cancel. Now you can disable just **one** mod and keep the rest.
- 🖥 **A maximized window no longer hides under the taskbar** — in fullscreen the bottom (status, buttons) is fully visible again. Multi-monitor aware.
- 🌐 **The update window's changelog now follows the UI language** (English by default). It could previously show Russian even on an English UI.
- 🏷 The "Our mods" button is renamed to **"Recommended mods"**.
- ⌨ **Launch arguments can now be cleared** — an empty field is saved (it used to keep the old value).

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
