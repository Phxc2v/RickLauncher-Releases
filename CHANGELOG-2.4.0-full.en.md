# RickLauncher 2.4.0 — the full list of changes

> Everything that went into 2.4.0 since 1.3.6, down to the last detail — more than five hundred entries.
> The short digest of what matters most is in `CHANGELOG.en.md`, section "2.4.0".

A big one. At the heart of it the launcher has its own **mod reference**, and nearly everything else rests
on that: the launcher finally knows what mod you are installing, whether it will run on your game, what it
needs alongside and what it will fall out with.

### The reference now answers about what you are doing right now

- 🟢🔴 **A green and a red stripe beside the mods — what changed since the game worked.** The launcher
  remembers the set of mods the game last *got into the game itself* with and closed fine — reaching the
  menu and quitting does not count, mods that break a campaign work fine in the menu. Those mods carry a
  green stripe on the left. If the game has fallen since, everything that came in or was updated after the
  last good launch carries a red one. The load order is not touched — colour instead of reordering. Above
  the list, a notice “The game fell after the set changed” names them, with one button, “Switch off these
  N”: it unticks (never deletes), you launch, and if the game runs you bring the red ones back one at a
  time. Hover the stripe for the date of the last good launch, when the mod was installed and with what.
- 🔢 **An install number on the left of every mod — “#27”.** After a good launch every mod is green
  alike, and “what did I put in last week that I want out” cannot be told by colour. Now the left of the
  mod's row carries its number in the order of installation, the date on hover: the higher the number, the later it
  came, and mods of one run sit in a row. Hover — “number 27 of 40 mods the launcher installed; together
  with 4 more”. Mods the launcher did not install have no number. A pack install is now written into the
  history too — one line per mod.
- 🧩 **“Mod is incomplete” is now what a crash is called when a mod cannot find a file of its own.** “Could
  not find file …\Modules\AD1259\ModuleData\sp_battle_scenes.xml” used to show as “a mod’s code threw”
  with a stack. The crash card now names the mod and the file missing from its folder and says what to do:
  install the mod again (or “Repair” the pack) and install 7-Zip — without it big .7z archives go through
  the built-in reader. The reader itself now counts: fewer files out than the archive lists is called an
  archive problem before the install, not a crash after it. The crash report header now carries the
  launcher version.
- 📋 **The launcher remembers which files a mod is made of, and notices when they are gone.** After every
  write of its own into a mod's folder — install, update, rollback, a translation laid in or taken out — it
  records the file list with sizes. Before a launch the list is checked against the disk: a file missing or
  emptied means the notice “Mod is incomplete” with the mod and the file named, instead of a crash half an
  hour later. That is exactly how a mod breaks when a translation is put into it by hand, folder by folder.
- ⟳ **“Reinstall the mod”.** A button on the mod's row and in that notice: the current copy stays as the
  rollback copy (the “↩” button brings it back), the folder is removed, the mod is downloaded and installed
  again from its recorded source. If the download fails, the previous copy comes back on its own. No premium
  account needed: the road is the same as an ordinary install.
- 🈯 **A translation added by hand goes into the mod by itself.** “Add mod” with an archive that has no
  `SubModule.xml` used to open the folder and say “copy it into the right mod”. Now the launcher finds the
  mod — by the folder inside the archive or by its name — and asks “Put into ‘AD1259’?”: the files go in by
  the same safe plan the translations window uses (manifest and code untouched, what is replaced is kept,
  the translation can be taken out). “Open the folder” stays as the second button.
- 💾 **A folder for downloaded archives** — a new setting under “Downloads”, off by default. Switch it on
  and pick a folder: every downloaded mod archive moves there after the install instead of being deleted.
  Next time the mod — installed alone, from a pack, or as an update — is taken from that folder without a
  download; it is downloaded only when the server has a newer version, and then the launcher asks:
  “download the new one or take the kept one” (a batch install takes the new one). For a big disk and a
  slow line: a 3.6 GB mod is downloaded once.
- 🈯 **A translation with a code file inside is no longer refused whole.** Some translators put a rebuilt DLL
  of the mod beside the strings (BannerCraft’s Russian translation — a 1.2.9 build, on game 1.4.7). The
  launcher used to refuse the whole archive — “neither a module nor files for this mod” — and the mod stayed
  in English. Now the strings and data go into the mod, the code stays out, and the launcher says which file
  was left out and why: somebody’s build for another version would break the mod. An archive with code and
  no strings is still not installed.
- 🧹 **The “downloads folder the pack installer listens to” is gone from the settings.** The installer had not
  listened to it since June: manual downloads go through the embedded browser, and the folder changed
  nothing. A setting that changes nothing is a lie in a form; the archive folder sits in its place now. The
  manual's note on the “Mod Manager Download” button is corrected too: a mod fetched that way is installed
  into the profile, not merely downloaded.

- 🖐 **Checked by hand.** If somebody actually ran the mod on your game version, the launcher says so first
  — on the card and before launch: "checked by hand on 06.09.2026 on game 1.4.7: playable, but falls at
  exit". A hand check outranks the reading of the code both ways: "playable" lifts the red, "not playable"
  puts it on.
- ⏱ **"Will not run" means start-up only.** A mod that, by the reading, falls at exit or in a battle is no
  longer called one that will not start: before launch it says, in amber, "the game will start, but the mod
  fails later — at exit".
- 💾 **Asked at the moment, not on the card.** Tick a mod that needs a new campaign into a set with saves and
  the launcher offers a new set (a copy without the saves) or adding it anyway. Untick a mod that keeps its
  data in the save file and it offers to copy the saves aside first.
- 📏 **How much to download and what is already here** — before you agree to dependencies: "3 more mods
  needed — ≈ 41 MB. Of what they need, already in this set: Harmony". The same in the RLink plan.
- 🌐 **Which of three translations to take.** The one built for your game version comes first; one built
  for another says "the strings may not line up".
- 👥 **"Usually installed with it"** — on the card, from players' Steam Workshop collections. Not advice:
  this is how others play; the scaffolding (Harmony, ButterLib, UIExtenderEx, MCM) is not listed.
- 🔁 **A rework in place of a broken mod.** When a mod is broken on your version and its rework runs by the
  reading of its code, the launcher names it and can swap them in the set — the old mod stays on the disk,
  switched off.
- 📅 **When your game version came out** — in the left list, and as an argument on the card: "the mod was
  last updated on 12.03.2026, and game 1.4.7 came out on 09.07.2026 — it was not built for it".
- 🔑 **The mod's key** after an install, when the author names one.
- 🗂 **Packs you opened stay in the catalog.** Open a `.rickpack` from Downloads and it is in “Ready-made
  packs” next time too. Every pack there now has “Delete”: it asks, deletes the file and drops the card. Your
  packs live in `RickLauncherData\Packs`; ours sit beside the launcher and come back with an update.
- 🚫 **A pack built for a game version you do not have is not installed.** A `.rickpack` built for 1.3 used
  to offer your 1.2 and 1.4 copies to choose from — and the mods in a pack are pinned to the version it was
  made on. Now the install window says “This pack was built for game version 1.3, and no such copy is
  here”, and the Install button stays dark: install that version, or take the pack made for yours.
- 🧲 **Installing a pack no longer drags foreign mods into its profile.** The dependency check that runs
  after the install looked at every mod of the game copy — your other profiles included — and brought the
  new profile what *they* needed, not what the pack did. The pack went in right, and ten seconds later eight
  strangers appeared in it. Every check now works on its own profile only — and so do the other places that
  used to read the shared list.
- 🔢 **The update’s version is the one the source named.** Many authors keep one number inside the archive
  for years, and after an update the launcher asked “this version is older — keep it?” although the update
  list showed a newer one. Now the number of the Nexus file or the GitHub release is written into the mod,
  and the manifest is not allowed to argue. The question remains only for the Steam Workshop, which has no
  number.
- 🔑 **With a premium Nexus key an update no longer opens the login page.** When Nexus ran out of its hourly
  request limit, the launcher read the empty answer as “no such file” and went to the browser for it — which
  asked you to log in. Now the refusal is called by its name — “Nexus did not answer the key (HTTP 429) —
  try again later” — that mod is skipped, the rest update, and nobody goes to the browser.
- 🧯 **An updated mod no longer vanishes from the list.** For the length of an update the old copy is moved
  aside — and the installer took that very copy for “the mod already installed”, wrote the new version
  into it, and the clean-up after the update removed the folder whole. The mod was gone from the list and
  from the disk, with Nexus still showing “downloaded”. The parked copy no longer exists for the installer,
  and the new version lands in its own place. If a mod of yours vanished this way, install it again: its
  place in the load order is kept.
- 🈯 **A translation is not offered a translation.** A localisation pack that is a mod in its own right
  (“Русская правка”) was offered a “translation” of itself in the translations window — another
  localisation linked to it by name. A mod that translates is left out of that window.
- 🈯 **Translation choices are pages, not module numbers.** One translation archive often declares two
  modules (the strings and the MCM strings), and the choice showed two identical “Affairs of Calradia RU ·
  1,869 downloads” — one download twice. And the same translation by a second translator, on a page of their
  own, was never offered at all. Now every page appears once, and every translator is in the list.
- 🈯 **A translation copied into the mod by hand counts as installed.** The reference knows the mod was
  published without Russian; if Russian files sit in the mod’s folder, somebody put them there, and there is
  no point offering that translation again.
- ⚙️ **“Offer the missing parts of a mod set” is now a setting, off by default.** The hint “players also
  install this — fetch the parts (32)” before a launch and after an update appears only for those who turned
  it on. A part of a set is only a file that really holds a module you lack; the “Fetch” button after an
  update now actually fetches, and the install review says so on the mod it concerns — not as an “Install?”
  question on a neighbour’s card.
- 🚪 **The pre-launch window always has “Cancel”.** When a mod needs a module of the game itself (War Sails),
  the first button is “Switch on NavalDLC” — not “Switch on the parts (1)”; after an update the same window
  closes with “Close”, not “Launch anyway”.
- 🔍 **“Find games” always offers to walk every drive.** The full walk used to be offered only when the
  usual places held nothing — and a copy unpacked into a folder of your own stayed unfound. Now, after the
  quick search, the launcher asks whether to look through every internal drive as well.
- 🙅 **No account — the mod is skipped, not waited for.** When a pack’s mod lives only in the Workshop and
  you are not signed in to Steam (or only on Nexus, and there is no key), a batch install no longer stops
  with a login window mid-run: the mod is marked “needs a Steam sign-in” in the review at the end, the rest
  are installed.
- 📈 **“Top 3 %” beside the downloads.** In the reference search every mod shows its place by demand among
  all mods in the base — two mods of one name by different authors are told apart at once.

### The mod reference
- 🛟 **The reference base has a backup address on GitHub.** When the mirror does not answer, or has no base,
  the launcher takes the manifest and the file from the permanent `db` release in the encyclopedia's
  showcase — with the same size, sum and signature checks. The mirror stays the main address: while it
  answers GitHub is not asked, and on a version disagreement the mirror is believed.

- 📦 **The reference travels separately from the launcher — a launcher update is two and a half times
  lighter.** The reference base (≈330 MB) is no longer in the update archive: the launcher fetches it from
  the same server by the reference's own channel, the way the encyclopedia itself has long done. Every
  launcher update used to drag 550 MB along for a change in one button — and overwrote a base you may have
  refreshed yourself.
- ⬇️ **Started without a reference — the launcher offers to download it at once.** A question with the
  size on the button (“Download 332 MB”), the download runs in a card at the top right with a bar, the
  speed and a cancel, and the launcher stays usable throughout. “Fix” on the red strip now fetches the
  base instead of sending you to the settings.
- 🆕 **A base newer than yours is out — a card at the top right, “A new base is out — from 10.09.2026,
  332 MB”.** Press “Update” and the base is in place without a restart. “Later” puts the card away for a
  while: it returns on a profile switch some ten minutes on, and on the next start — later means later,
  not never. The base on the server is compared by build date, as the encyclopedia itself does — a base
  older than yours is not offered.


- 📦 **A mod that is not published on its own is now found exactly.** The reference unpacked the archives and
  recorded which submodule lives inside which mod (1 595 links) and in which file (4 248 links). The launcher
  used to infer this from two addresses matching — and once concluded that Harmony "ships inside Native", so
  it would have offered to install a part of the game. It now asks the reference, and only falls back to the
  guess on an older database.
- 💾 **A missing part of a mod is fetched as ONE file, not all of them.** "Tales from the Age of Men" ships as
  two files of 11 and 17.4 GB, and nothing on the page says which holds the library another mod needs. The
  reference knows, so the launcher asks: "this module is needed, it is in that file, 11 GB — fetch it?"
- 🔀 **Mutually exclusive files are no longer treated as parts of a set.** Some mods publish three files that
  are three versions of the same thing, and exactly one is meant to be installed. The launcher offered all
  three.
- 🐙 **A repository with no releases is no longer opened.** The reference asked GitHub about every one: 276
  publish releases, 664 do not. The launcher could not tell, and opened a browser on a page of source code
  under a caption saying "Download" — that was LOTRAOM. Such addresses are now skipped outright, while
  "nobody asked" still means the launcher asks GitHub itself.

- 🧹 **One mod, one row in search.** Some mods are several parts inside a single archive: "Templar Armor" is
  three, and search showed three identical rows — same picture, same download count, three Install buttons
  all fetching the same file. There is one row now. Translations and patches stay separate: they have their
  own file, and you can tell them apart.
- 🏅 **Search shows which entry is the original and which is somebody's copy.** A popular mod has half a
  dozen translations and forks on the sites — the mod itself now carries a green "✓ original" badge, and
  under a copy's name it says what it is a copy of: "translation of «Anno Domini 1259 continued»".
- 📈 **And how many people use it** — the download count (or Workshop subscribers where that is the only
  figure) right in the result row.
- ↕️ **Results can be sorted:** by downloads (the default), best match first, or by name.
  ⚠️ "By downloads" means by downloads **among what actually matches**: a giant that merely mentions your
  word in its description will not float to the top, however many downloads it has.
- 🔎 **Search understands your language — all six of them.** Type "гарнизон", "garnizon", "pillage" or
  "战斗" and you get the mods about it, even though they are all named in English. Only Russian could do
  that before: the reference ships a fast index for Russian alone, so the other five languages were
  searching English text with foreign words and finding nothing. What the index cannot answer is now looked
  up in the descriptions written in your language.
- 🏷️ **Under the English name, what the mod does — in your language.** "Improved Garrisons", and one short
  line below saying what it is about. The reference holds no translated names at all (9 165 mods described in
  six languages, and not one translated title), so the line comes from the short description, trimmed to fit
  a row. English gets no such line: there is nothing to explain.
- 🏷️ **That line shows wherever a mod is named:** search, the card, the profile's mod list, adding
  a mod you already have, updates, translations, our recommended mods and the pack install window.
- 🖼️ **Every mod in a list gets a tile, artwork or not.** The game's own add-ons (War Sails and the rest) are
  not in the reference at all, and six hundred catalogued mods have no artwork: such a row used to lose its
  first seventy pixels, start further left than the others, and make the whole list look broken. The tile now
  carries the mod's initial instead, and the column stays straight.
- ✍️ **The card says who actually published this build of a mod.** Thousands of mods on the sites are
  somebody else's work kept alive — an unofficial rebuild, a fork carried on with permission. The reference
  states it, and now so does the card, under the description instead of somewhere you find out later.
- 🔄 **A rebuilt reference finally reaches you.** The 200 MB base is replaced every few weeks, and small
  corrections arrive in between. The launcher only ever asked about the corrections — so when the reference
  published a new base and withdrew the old corrections, it cheerfully reported "up to date" while standing
  on the previous one for good. It now notices that the mirror holds a different base and offers to fetch
  it, with the size and your consent, as before.
- ⚡ **Updating the reference is twice as quick** — and, more to the point, out of the way: it used to take
  half a minute and to happen while the window was being drawn, so the launcher looked hung. It now runs
  beside the launcher and the window opens at once.
- ⚡ **Startup no longer waits for the reference to update.** Writing a 60 MB correction into the database
  takes half a minute, and it was being done inside the first question anyone asked the reference — which at
  startup is while the window is still being drawn. The launcher looked hung. That work now runs beside it
  and the window opens at once.
- 🔑 **Updates to the reference finally arrive.** Corrections to the database ship as separate files and are
  meant to be laid over it at startup. They never once were: a correction file is sealed exactly like the
  database itself, and it was being attached without the key — so SQLite answered "this is not a database",
  which is indistinguishable from a broken download. One warning line went to the log, nobody read it, and
  the launcher went on answering from a database a week old while the corrections sat on disk unused.

- 📚 **It ships with the launcher and works offline.** Over nine thousand mods: what a mod does, which
  versions of the game it runs on, what it needs alongside, what it fights with and where to get it. It is
  a snapshot as of a date — the date is at the bottom of every card.
- 📖 **Every mod now has a card** — the **ⓘ** button in the mod list. At the top: name, author, pictures
  from the mod's page, and the short answer in coloured chips — will it run on your game, what does it
  clash with, what is it missing. Below that: description, game versions, clashes, what it needs alongside,
  files, what it adds to the game, where to get it, what was made for it, what has changed in it.
- 🔎 **Search for mods you do not have yet.** "Add a mod → Find a mod in the reference…", and the button is
  on the main screen too. You can type in your own language — the reference carries translated
  descriptions. Each row says what the mod is, whether it suits your game and whether you already have it.
- 🖼️ **Pictures open inside the card**, with arrows and the keyboard.
- 🔗 **The "Where to get it" tab now puts the mod's own page on top, not somebody's archive that carries it.**
  For Improved Garrisons the only Nexus link shown turned out to be a Chinese translation — it ships the mod
  inside its archive, and that was enough to win the slot. Bundles and removed pages now always sit below,
  under their own line, and forks are labelled as forks: RTS Camera has some thirty of them, and unlabelled
  they read as thirty addresses for the same mod.
- 🔗 **Any mod named on a card opens its own card** — a separate window on top of this one, so a clash can
  be read beside the mod it is about. Cards do not block one another: arrange them side by side, switch
  between them, close them in any order.
- 🧩 **"Made for this mod" shows everything there is,** in two lists: add-ons, patches and forks in one,
  translations in the other. Big mods have over a hundred such entries — only the first eight used to be
  shown, with nothing said about the rest existing.
- 🌐 **If the description exists only in another language, the card says so** — rather than an English
  paragraph sitting silently under headings in yours.
- 🗣️ **The languages a mod was translated into are spelled out** — "German, Spanish", not codes like `GE`
  and `SP`, half of which mean something other than they look like.
- 🧪 **What we measured ourselves goes in red, above the author's own description.** The first such mod is
  Performance Optimizer: four days of measurements on the same saves produced no extra frames at all,
  while the mod stops updating distant parties, so in a long campaign the world does not live the way it
  was meant to. Only what we measured, and only what the mod does to the game.
- 🆔 **A mod's name and its internal id copy on a click.** The id is what mods find each other by — it is
  what forums and other people's instructions ask for.

### Installing mods
- 🎙️ **“Voices of Calradia” now comes from GitHub too.** The mod has a public repository with releases;
  the launcher takes it from there first (when GitHub is on in the settings), then from our server, then
  from the Steam Workshop — like our other mods. The server used to be the only source.

- 🔒 **The game's own modules are visible in the mods window — as a block that cannot be switched off or
  deleted — and a mod can be placed ABOVE it.** They used to be hidden and "always first", so no mod could
  load before Native however the list was arranged; total conversions (a LOTR pack, say) and override packs
  with a "!" in their name need exactly that. Now a "The game's own modules" block with Native, SandBox,
  StoryMode and the rest stands in the list; everything above it loads before Native, everything below
  after. Drop a mod on the block, step it across with ▲▼, or leave it to the launcher: mods that declare
  "before Native" themselves ("!" in the id, LoadAfterThis on Native in SubModule.xml, Harmony and the
  other libraries) are raised above the block automatically and always load there. Rows above the block
  carry a "before Native" tag. The game's optional add-ons (War Sails, Birth &amp; Aging) stay ordinary rows
  tagged "game".


- 🧭 **A file number no longer moves to somebody else's page.** Two Nexus pages can publish a mod under the
  same internal name. When a mod was installed from the second page, the launcher recorded the new page while
  keeping the first page's file number — and the update check then asked one page about a file that only
  exists on the other. That is how «Empires of Europe 1700» stopped finding updates: the record pointed at a
  page carrying nothing but the older build. The file number is now forgotten when the place changes, and the
  next check asks the new place from scratch.

- 🖼️ **«Голоса Кальрадии» has a picture now — in the recommended list, in search, in updates and on its
  card.** The mod has no public page, so the reference records its cover under a `local://` address meaning
  "the picture comes from whoever ships the mod". The launcher tried to fetch that over the network, which it
  is not, and the mod appeared everywhere without artwork. The cover now travels inside the launcher; should
  the reference ever ship one itself, its copy wins.

- 📗 **The launcher was checked against the new reference (base of 08.09).** Three things it now says
  differently, and the launcher read each of them the wrong way. «Requires Multiplayer» no longer means «your
  copy of the game has not got that part»: the multiplayer module ships with every copy — the launcher hides
  it because it only ever starts singleplayer — and eleven mods were being refused over it, with an untrue
  reason and advice to tick a module that is not in the list. «WarSails» is War Sails: under the shop name the
  game part went unrecognised and the launcher would have gone looking for it. And headings lifted out of a
  mod's description — «Required files», «Four Prerequisites», «No War Sails» — are no longer shown as mods to
  install: the reference marks them, and that mark is now read.

- 🏷️ **A missing mod is named by the reference, not by the author's own string.** UIExtenderEx's requirement
  carries a typo — «Bannerlord.ButterLub»; the reference repaired it internally but kept the author's wording,
  and the launcher would have sent a player looking for a mod that has never existed.

- 🔎 **Installing a mod from your own disk now says when you already have it.** Files from an archive or a
  folder used to be laid over whatever was there without a word. Now: the same version gives a line saying so;
  a different version, higher or lower, gives a question — replace with the new one, or keep the one you
  have — and it is asked before a single file of the old copy is touched. Declining costs nothing: the old
  mod stays exactly as it was and the new files are dropped.

- 🧩 **A damaged data file inside a mod is now caught at install time instead of as a crash.** While loading,
  the game merges every mod's data into one document and dies on the first file it cannot read — before the
  menu, with no crash folder and nothing in the mod list to explain it. Empires of Europe 1700 (the build for
  game 1.3.13) ships `ModuleData\cla_item_holsters.xml` with its closing line written twice: 568 data files
  are perfect, one is not, and that one was enough. The launcher now reads a mod's data straight after
  unpacking and names the file and the line. It does not touch the mod: the file belongs to its author, and
  the launcher only says what is wrong with it.

- ♟️ **Installing over another mod is no longer silent.** Two Nexus pages can publish a mod under the same
  internal name — and then “installing” one of them really means REPLACING the other. That is how 4,2 GB of a
  build made for game 1.3.13 landed on top of Empires of Europe 1700, updated for 1.4.7 the day before: same
  name, same folder, not a line anywhere, and a game that stopped starting. The launcher now compares what
  was there with what arrived and says so plainly.

- 🩺 **Fewer false “this mod will not load on your game”.** The compatibility check read EVERY program file in
  a mod's folder, including the ones the game never opens. Empires of Europe 1700 carries
  `CustomSpawns.dll` from an older branch of the game — the mod does not declare it and none of its own files
  reach for it. That dead file was enough to put a red window in front of a mod whose author supports this
  very build. Only the files the game actually loads are read now: the ones the mod declares, what those
  reach for, and the builds a mod's own loader picks up.


- 🧊 **Fetching a set's parts before playing no longer wedges the launcher.** The “fetch the parts” button
  started the install from inside the launch, which had already raised the “a game is running” flag. Two waits
  then closed into a ring: the install waited for the game to end so it could show its review, and the “game”
  waited for the install to finish so it could clear the flag. On screen it looked like an unpacking bar
  spinning for ever. The launch now unwinds completely first, and only then does the fetch begin.

- 👯 **One mod, one row in the install list.** The reference files the same mod under more than one key:
  “Empires of Europe 1700 Sound Overhaul” has two cards, and so does “…Expanded”. In the fetch list they
  appeared as two rows with the same name, and the launcher dutifully downloaded the same archive twice.
  Cards pointing at the same mod page now count as one mod.

- 🚫 **A mod the launcher has just called unusable on your game is no longer switched on by itself.** A
  batch install still asks nothing and installs what you picked — but the tick is a separate decision. A War
  Sails patch on game 1.2 arrived as 470 MB, unpacked to 713 MB, was found to need game code this build does
  not have — and was enabled anyway, right beside the note saying so. The files stay and the row is there;
  the tick is yours to put on knowingly.

- 🎯 **…and it is that very mod that is left switched off.** One pick sometimes brings several modules out
  of one archive — a mod and its add-on. The "will not run" verdict is reached per module but was remembered
  against the pick, so the review row carried the wrong name, its switch turned the wrong mod off, and the
  one that really cannot run was switched on. A mod added from a plain link has no id at all until the
  archive is unpacked, so nothing was remembered about it either and it went on as before.

- 🤫 **A batch install asks nothing again.** When a picked mod was already in the profile — from its pack
  or from the game's own folder — the launcher asked "replace it, or put it back?" in the middle of the
  downloads: forty mods stopped and waited for the click a batch exists to avoid. The new copy stays, as it
  already did whenever there was nothing to ask with, and the news waits for you on the review screen.

- 🧩 **A mod's folder is matched to its reference card by the reference's own data, not by guesswork.** The
  reference records which folders appear after unpacking — 2 522 such links, and in every one the folder name
  differs from the card's key. The launcher now asks that first and only then falls back to comparing the
  spelling: this is how “EoE1700Assets”, which looks nothing like “Empires of Europe 1700”, is found at all.

- 🪪 **A mod is found in the reference even when its folder spells the id slightly differently.** The mod
  calls itself “Europe 1700” with a space while the reference files it as “Europe1700” — and the launcher
  did not recognise it: the card vanished from the list, the update row lost its picture, and worst of all
  it decided “Empires of Europe 1700 is not installed”, switched the add-on off and offered to download
  1.2 GB again. Spaces, dashes and underscores no longer stand in the way. When more than one card fits the
  loosened spelling the launcher still says nothing: it will not guess.

- 📚 **A link to a Workshop collection now works.** The launcher used to try to download the collection
  as if it were a mod and reported that there was nothing to fetch — a collection has no files of its own.
  It now says this is a list, how many positions it holds and how many of them can be installed, and reads
  the reference's own verdict on it: how many positions are missing mods they require, how many clash
  heavily with each other, how many global mods are inside, and which branch of the game the list is for.
  Then: install the mods, open the list's page, or cancel. Of 3 615 Workshop collections the reference calls
  505 unworkable.

- 🩹 **The Nexus "Log in" button opens the login window again.** A tester signed out of Nexus, pressed "Log
  in" — and nothing happened: the button went dead while the login window sat off the edge of the screen,
  waiting for credentials nobody could type. The download browser is deliberately kept hidden — the launcher
  is supposed to fetch mods by itself, with no pages jumping out — but signing in had been swept up in that
  rule, and signing in is the one thing the window exists for. The two are now told apart: a download still
  runs hidden and still says so plainly when it cannot finish, while a sign-in you pressed for in Settings
  shows its window.

- 📄 **A mod with an unusual manifest no longer vanishes from the list.** `SubModule.xml` sometimes declares
  one encoding and is written in another — the game itself ships files like that. The launcher used to fail
  to read such a file in silence, and the mod disappeared from everywhere: the list, the load order, every
  check. It is now re-read in its real encoding, and a genuinely broken one is named in the log.
- 🗂️ **Updating a mod no longer leaves a second folder behind.** Authors glue the release number onto the
  folder name, so "MyMod v1.4" and "MyMod v1.5" became two folders holding one mod — and which one the game
  took was its own business. The new version now lands in the folder the mod already occupies.
- 🧹 **Packaging leftovers no longer travel with a mod** — the game's own `RuntimeDataCache` and macOS
  service files are not copied into your folder.

- 🔁 **The mod's file list is now read across servers instead of from one.** A chunk got ten attempts across
  twenty servers; the file list got exactly one, from one server. A cache that would not answer its port took
  the whole install with it: "A connection attempt failed because the connected party did not properly
  respond". The list now gets six attempts on different servers — nothing has been downloaded at that point,
  so another try costs a second.
- 🎲 **The first server is no longer the same one every time.** The rotation counter started at zero for each
  new download, so every run in the log read its file list from the same host — and a host having a bad
  minute had it for every attempt in a row.
- 🗣️ **"Could not connect" is said in plain words.** Instead of the network layer's own sentence with a host
  name and a port: that the problem is the line between you and Steam rather than the mod, and that it is
  worth checking the connection and trying again.
- 🐌 **A "503" refusal from Steam no longer kills a download halfway.** After a few dozen megabytes Steam
  starts turning requests away — its way of saying "not so fast". The launcher answered by moving to another
  server, but they refuse together, three attempts burned against one wall, and a 96 MB mod died at 26.5 of
  them. A refusal is now read as a request to ease off: everything in flight pauses — two seconds, then four
  times as long, up to half a minute — and the first chunk that gets through lifts the pause. A chunk is
  tried ten times instead of three: giving up throws away everything already fetched, which is the worst
  trade available.
- 🗣️ **And it is said in plain words.** The window used to show "Response status code does not indicate
  success: 503 (Service Unavailable)" — a sentence written for whoever wrote the HTTP library. It now says
  the mod is fine, this is Steam's side, it is worth waiting a few minutes, and nothing already fetched is
  thrown away.
- 🔑 **Steam's server tokens are refreshed rather than taken once and kept.** They have a limited life, and
  the launcher took them in the first seconds of a download and held them to the end.
- ⏱️ **A Steam install no longer breaks off while reading the file list.** The per-request limit is a static
  in the Steam library and covers everything alike, the mod's file list included. For a mod of several
  thousand small files that list takes five to eighteen seconds to read, and the limit was set to four: it
  could never finish. Preparation now gets a minute, and the short deadline applies only to chunks, which is
  what it was meant for.
- 🗣️ **A timeout is no longer written down as "the player pressed Cancel".** A timeout arrives as the same
  kind of exception as a cancellation, so the launcher was telling its log the opposite of what it showed on
  screen. Only a real cancellation counts as one now, and time running out is called what it is — with the
  screen saying the mod is fine and it is worth another go.
- 👀 **What Steam is doing before the download starts is now visible.** It hands out a server list, then a
  key, then the mod's file list — all of it under the word "Downloading" with a bar at zero, which is what a
  stuck download looks like. Each step now names itself, and the file-list step says outright that a mod of
  many small files takes a moment there.
- 🧩 **A mod the profile already has no longer lands as a silent second copy.** The check before a download
  compares ADDRESSES, and the same mod reached the pack from the pack's address and the player from theirs —
  different addresses, no match. TWO folders of one mod were left on disk, the game loaded one of them, and
  nothing said which. Nobody needs two copies. Now that the files are unpacked and the module id is known,
  the launcher asks outright: **replace**, and what you downloaded is what the game uses; **cancel**, and the
  download is removed again, leaving the copy that was there. Only what this install placed is removed, and
  the mod is not hidden from the profile — the whole point of cancelling is to go back to the copy that
  existed.
- 🔎 **A mod already installed in the profile is no longer downloaded again — from any source.** The launcher
  only found out afterwards: it fetched the whole mod first, sometimes for minutes, and only then said it had
  been there all along. The profile records where each of its mods came from, so the question is settled
  before the first byte — for the Steam Workshop, for Nexus, for GitHub and for ModDB alike. What is compared
  is whatever the address identifies a mod by: for Nexus the game and the number, for GitHub the repository,
  for the Workshop the item id. The page is compared only when there is nothing else: one mod has several
  pages, and one author's page has several mods.
- 📋 **A failed Steam install writes its reason to the log.** Of the three ways it could end, only
  cancellation left a trace: Steam refusing access, and every other error, showed a window and said nothing
  in the log. There was no way to tell a refusal from a timeout from a broken archive afterwards.
- 🛑 **A Steam Workshop download no longer hangs before it starts.** The cache of Steam's server tokens was a
  plain dictionary, and the launcher had just started fetching a mod on eight threads — eight writes at once
  can leave that dictionary with a loop in it, after which a read spins for ever. From the outside it looked
  like this: the download began, wrote not a single line to the log, and moved not one byte.
- 📋 **A Workshop download now writes down every step it takes.** There used to be nothing at all between
  "install pressed" and the first failing chunk, so hanging before the download and simply downloading slowly
  looked identical. It now says: asked for the servers, got the file list, this many chunks, done.
- 🚀 **A Steam Workshop mod downloads far faster.** Three things at once. A Workshop mod's chunks are tiny —
  one measured mod held 96 MB in 3678 chunks of twenty-six kilobytes — and the launcher fetched one chunk at a
  time for the whole mod: with a round trip of about a hundred milliseconds that is a ceiling of a quarter of
  a megabyte per second however fast the line is. Chunks are now fetched several at a time, and across the
  whole mod rather than inside one file, because a file with a single chunk has nothing to overlap. Next, one
  chunk was given ten seconds before being given up, while a healthy 26 KB chunk arrives in a fraction of one:
  ten seconds is not "slow", it is a dead server holding a slot — it is four now. And finally, a server that
  has just failed to answer is no longer the next one tried: it rests for half a minute while the other twenty
  carry on.
- 📋 **The log now says how fast a Workshop mod actually downloaded.** It carried the timeouts but never the
  rate, so "a slow line" and "our own doing" could not be told apart.
- 🚀 **Mods from Nexus packed as 7z or RAR now unpack in seconds instead of an hour.** Nexus serves every mod
  under the single name `download.zip` whatever is really inside, and the launcher picked its unpacker by the
  file's name. A real 7z went to the built-in reader, which is the wrong tool for it: a 7z is solid — reaching
  one file means decompressing its whole block from the start — and on a mod of 5094 files that was done 5094
  times. It looked like "unpacking at 20 KB/s and never finishing". The format is now read from the file's own
  first bytes and such an archive goes to the system 7-Zip: the same 8.5 GB in half a minute instead of
  forever. The file's name no longer decides anything.
- 🗜️ **And now just as fast on a computer with no 7-Zip installed.** The previous fix handed such archives to
  the system 7-Zip — which not everyone has, and for everyone who doesn't, nothing had changed: a tester sent
  a photo reading "Unpacking… 34%" at 263 KB/s three hours in. Same cause: a solid archive was read one file
  at a time, meaning from the start again for every file. It is now read in one sequential pass. Measured on a
  solid archive of 400 files / 392 MB: **10.5 seconds against the four minutes in which the old way got
  through only 157 of the 400 files** — and it was still slowing down. 7-Zip stays a speed-up for those who
  have it, rather than a condition for the thing working at all.
- 📋 **The log now says which engine actually unpacked an archive.** The line used to be the same whether the
  system 7-Zip did the job in half a minute or the built-in reader was three hours into it. There was nothing
  to answer a complaint with but guesswork. It now names which of the two took the archive, and says so when
  7-Zip is not found.
- ⏱️ **The unpacking speed stopped lying on big mods.** One mod of a pack reported 130 MB/s and the next one
  20-50 KB/s, while both were unpacking at full speed. Extraction progress is read by walking the folder and
  summing file sizes, and 7-Zip gives an output file its full length the moment it CREATES it and then spends
  seconds filling it: the sum climbs in steps, and "bytes since the last look, divided by the time since the
  last look" reads zero for the whole width of a step. A mod made of a couple of two-gigabyte asset packs is
  nothing but steps, and the only thing visible was the small files finishing alongside. It now shows the
  average since the unpack started — the same figure the download already shows: it cannot read zero while
  work is happening, and it cannot spike to gigabytes per second.
- 📋 **The log now says how long each mod of a pack took to unpack.** A pack install used to write
  "extracting…" and say nothing more until the mod was installed, so "the unpack crawled" could not be told
  apart from "the meter lied about an unpack that took forty seconds". A single mod has logged this for a
  while; a pack never did.
- 🤫 **The review screen appears only when it has something to say.** If the reference has no warning about
  any of the picked mods and nothing extra needs fetching, the install starts straight away. It used to open
  every time, asking you to confirm a list you had just chosen.
- 📚 **The libraries a mod cannot run without are fetched without asking.** Harmony, ButterLib, MCM are a few
  megabytes and the difference between a mod that works and a mod that does nothing. The launcher just gets
  them; which build it picked, and why it may not be the newest, goes to the status line and the log.
- 🔎 **Games are found by the launcher itself.** On a first run it no longer asks "shall I look for your
  games?" — it looks in the usual places straight away, and offers the walk of every drive right after.

- ⏳ **The download window no longer looks finished while it is still working.** After the download a mod is
  still unpacked, read against your game and written into the profile — and the bar sat full through all of
  it, as if everything were done. People pressed Cancel mid-run. The bar now starts moving again at every
  such step, a mark turns beside it, and it says so in words: work is going on, don't close the window.
  Steps that used to say nothing at all are noticed by the window itself.

- 🔎 **A search box in "Add an installed mod".** With forty folders on disk, scrolling the list is no help —
  now a couple of letters is enough. It matches the name, the name in your language, the folder, the version
  and the description; several words narrow it down in any order. "Select all" applies to what is on screen
  rather than to mods the filter is hiding, and the button says how many are ticked — the off-screen ones
  included.

- 🔒 **One mod operation at a time.** Installing, updating, translations and our own mods no longer run on
  top of each other — you could start an install, switch to another profile, press Update, and have two runs
  writing into two different vaults while one window narrated whichever spoke last. The second action now
  says what is going and offers to show it.
- 🧯 **The profile being installed into is closed off for the duration.** Not just Play: all of that
  profile's buttons and its menu go too, because every one of them writes into the same folders. They come
  back the moment the run ends, however it ends — an error included.
- 🚪 **Closing the launcher during a download asks first.** It used to just close, leaving half-arrived files
  in the vault and — for a Workshop mod — Steam still downloading in the background. It now asks, and if you
  agree it stops the run properly before closing.
- 📍 **The download window says where the file is coming from** — Nexus (noting when premium is pulling from
  several mirrors at once), the Steam Workshop, GitHub, ModDB, our mirror.
- 🧾 **One mod, one card in the review.** When there were two things to say about a mod (files missing AND a
  clash over records), it got one card and an identical-looking second one below it — same picture, same
  name — which read as the mod having been installed twice.
- 🔁 **A dependency that is already installed and switched on is no longer downloaded again.**

- 📦 **A mod is no longer fetched out of somebody else's archive when it has a page of its own.** This was
  the cause of the 4.2 GB of the wrong build. The reference records that a mod can travel INSIDE another
  mod's archive and marks such rows plainly; the launcher already avoided them — but avoided them
  *always*, which turns out to be only half the rule. Measured against the base: 708 mods have a page of
  their own beside such a row — those must never be raided; and 14 mods cannot be reached any other way,
  and those the launcher was making unreachable, answering "no address on record" about a mod whose address
  was right there.
  Now: the mod's own pages first, somebody else's archive only when there are none, and a line in the log
  saying why. ⚠️ Such rows are still shown on the card — "this mod ships inside that one" is true and
  useful; it is only not a place to download from.

- ⏱️ **You can now see WHEN a mod will fall over, not only what it trips on.** The reference re-read the
  whole catalogue — 40 252 builds — recording which part of a mod's code holds each finding, and turned that
  into a moment: "will not start the game", "will break loading a save", "will fall over when the game
  reaches this class", "in battle", "on the campaign map", "on the way out". Measured against the shipped
  base: **89 % of the evidence now names a moment**.
  The card used to say "reaches for CultureCode, which this version has not got" — true, and nothing to do
  about it. "Will not start" and "dies in battle" are different evenings: the first is found in ten seconds,
  the second costs an hour of play and a lost fight.
  Shown on the card — in the block about your own game and in every branch row — **and in the question asked
  before an install**, before the first byte moves.
- 📖 **And what the missing piece of the game actually is, in plain words.** "CultureCode — the list of
  Calradia's cultures: Empire, Vlandia, Sturgia, Battania, Aserai, Khuzait." The reference decompiled all
  seven versions of the game and described the pieces that turn up in evidence.
  ⚠️ Not every name has one. When a method is missing, the description of the class it belongs to is shown
  instead — which lifts coverage from 14 % to 62 %. Where there is no description at all, nothing is said:
  an empty line is not a line.
- 📄 **"Failed to open archive" is no longer said about an archive that opened.** When the file read
  perfectly and could not be written — an antivirus holding it, the game holding it, the disk full — the
  launcher now says exactly that: the install did not finish, and here is the file it stopped on. It used to
  blame the archive, sending people off to re-download a file that was fine.
- 🚫 **The launcher no longer opens any page in order to download something.** Installing things by hand is
  not your job — it is the launcher's. The one exception is what it always was: signing in to Nexus.
- 🧩 **A Steam Workshop mod is taken from Steam, not from its page.** The launcher could open a Workshop page
  in the browser and wait for a file that cannot be there: Valve hands those mods to the Steam client and to
  nothing else. It now fetches them properly, and if you are not signed in to Steam it asks you to sign in
  instead of showing a web page.
- 🔑 **A premium Nexus key stopped getting lost on mods with a long history.** Some of ButterLib's and Mod
  Configuration Menu's older files carry no recorded size, and reading Nexus' answer tripped over exactly
  that — which looked like "Nexus has no file", so the launcher went to the browser despite the key being
  premium. UIExtenderEx has no such files and worked throughout, which is why the cause stayed hidden.
- ⚡ **Mods from Nexus download far faster if your account is premium.** With no direct link to hand, the
  launcher used to go to the Steam Workshop — "it costs nothing". True for an ordinary account; but a premium
  Nexus key is handed seven addresses for a file, and the launcher pulls them in eight streams at once.
  Measured: 8 GB off Nexus in forty minutes against **seventy-one minutes** for a single Workshop item.
  Nexus is now tried first when the key is premium. A mod that is not on Nexus still comes from the Workshop.
- ⏳ **The list-install window can be minimised so you can get on with something else.** A dozen mods takes
  hours, and the launcher was occupied for all of them. Minimise puts the window away and the download
  carries on. ⚠️ Minimise and Cancel sit at opposite ends on purpose: one hides, the other stops.
- 🎮 **And you can play — on another profile.** The profile currently being installed into cannot be
  launched: the game would read folders still being written, and nothing about the result would be
  explainable afterwards. Its Play button shows the download instead and brings the window back when
  pressed, its row in the sidebar gets a ⬇️, and every other profile behaves exactly as usual — pick one and
  play.
- 🔔 **The install report will not minimise your game.** If the list finishes while you are playing, the
  review waits until you close the game.
- 🚦 **One list at a time.** A second run says an install is already going and offers to show it.
- 🧮 **A list picked in search is installed in dependency order, not in the order you clicked.** Pick a dozen
  mods in a row and the order is whatever your clicking made it — so a big mod easily lands before the one it
  is built on, arrives without it, and gets switched off again by the launcher. The list is now laid out
  first: what others need goes in ahead of what needs it. Libraries like Harmony come first even with no
  reference at all, and "this mod was made for that one" is read from the database — including for mods whose
  own files say nothing about it.
- 💸 **And nothing is downloaded twice.** A mod that already arrived as a neighbour's dependency simply has
  its row ticked off.
- 🎯 **When one archive holds several variants of a mod, the right one is installed rather than all of
  them.** Some add-ons ship as a single file carrying bridges to different overhauls at once — one for Anno
  Domini, one for The Old Realms, and so on. The launcher used to install the lot, and then dutifully went
  looking for The Old Realms, because the bridge to it requires it: a browser opened on Steam offering a
  multi-gigabyte overhaul nobody asked for. Now the base and the bridge whose mod you actually have go in;
  the rest are skipped quietly.
- ⛔ **Cancel stops the whole install, not one file.** A cancelled download used to look exactly like "there
  is nothing at this address", so the launcher moved calmly on to the next one. Pressing Cancel three times
  running and watching the install carry on is over.
- 🧹 **Deleting a profile while something is downloading into it stops the download.** It used to carry on
  into a profile that no longer existed.
- 🖱️ **Menus stopped going dead.** After some actions — most often deleting a profile from its menu — every
  menu item at once stopped responding and only a restart helped. An open menu holds the mouse, and a window
  appearing over it closed the menu without handing the mouse back.
- 🪟 **A second download window no longer opens on top of the first.**

- 🔒 **The Windows user name is gone from the reports.** A crash report and an install log are written to
  be sent to somebody, and they are full of paths — the crash folder, the dump, the logs. All of them
  started with `C:\Users\<your name>\`, and that name travelled with the file. It now reads `<user>`:
  which folder is still clear, whose is not. Windows' own accounts (Public, Default) are left alone, and
  anything that is not a path is untouched — a mod with the author's name in its title still has it.

- 💾 **An interrupted pack install is no longer lost.** Cancelling on mod eight of twenty went straight past
  the registry write: seven mods sat in the pack's vault, the launcher knew of none of them, the next attempt
  downloaded them again — tens of gigabytes — and they never reached the game either. What actually landed is
  now recorded. The pack does NOT claim the manifest's version in that case: half of a version is not that
  version, and the update check says so honestly.
- 🧾 **A failed rollback of a mod update no longer stays silent.** When the previous version cannot be put
  back — the game is running, a file is held — the log now says exactly where that copy is kept.

- 🗂️ **One rule for "is this path inside that folder", across the whole launcher.** There were four, and they
  disagreed: with a destination written with a trailing slash, three of them answered "outside" for the
  folder's own files. One of those checks is the guard against an archive unpacking outside its destination —
  and refusing every file is the other way it fails. The rule is now shared and pinned by tests.
- 🔁 **Undoing a mod update while the game runs now says so.** It used to surface a technical error about a
  path; it now reads "the folder is in use, close the game", and the restored copy stays beside it so the
  next attempt continues from there.

- 🎚️ **The shader quality a build uses is now your choice.** The launcher always forced the lowest and merely
  said so, leaving anybody whose card can carry more with no way to ask. The choice now sits in the window
  before the build, next to the Start button; the default is **low, marked as recommended**, with the reason
  beside it: the game then plays at the same setting (shaders are only valid for the quality they were built
  at), and the higher it goes the longer the build takes and the more memory it needs — on heavy packs like
  The Old Realms, high usually does not make it to the end.

- 🧭 **Early-access game versions (e1.x) are understood again.** The launcher and the reference spell a game
  branch differently — "1.7" against "e1.7" — and two places compared one with the other, quietly discarding
  every mod file recorded for an early-access branch. On today's 1.2–1.4 the two spellings agree, which is
  why nobody saw it.

- 🏷️ **A site's internal string is no longer shown where a version belongs.** The main screen and the updates
  window read "v2.12.0 → b1/e5/f2/b1e5f247-5ae5-4902-99ef-4db344ca3123" — that is how Nexus answers about a
  newer file: with its path in their storage rather than its name. The launcher now takes that file's real
  version from the same page, and where there is neither a version nor a readable name it simply says
  "a newer file". Labels people write by hand — "Beta 3", "hotfix2" — show exactly as before.

- 🛑 **Cancel really does cancel.** Cancelling a Steam Workshop download and starting it again straight away
  left the mod refusing to install until the launcher was restarted. The reason: the cancellation never
  reached Steam's downloader, which carried on in the background holding the files it was writing, so the
  second attempt could not even clear the folder ("cannot access the file 'pack0.tpac'"). Restarting the
  launcher is what actually stopped it. Cancellation now reaches everything — Workshop, Nexus, GitHub, the
  mirror, archive extraction, installing from a folder — each attempt gets a working folder of its own, and
  cancelling no longer shows up on the review screen as the mod having failed.

- ⏱️ **The rate now shows for Steam Workshop downloads too.** A 4 GB mod came in over four minutes with
  "0 KB/s" beside the bar the whole way — a moving bar and a zero look exactly like a stuck download. Steam's
  downloader reports bytes and nothing else, so the launcher works the rate out itself; that was already done
  when updating a Workshop mod, and now it is done when installing one.

- 🪟 **A question now always appears over the window you are working in.** Pressing "Undo the whole run" on the
  review screen put the confirmation BEHIND that window, and everything froze: the window would not answer,
  the question could not be seen, and there was nothing to click. That was true of any question asked from a
  window of its own. The launcher now looks at which window is in front and draws the question there — same
  card, same button order, Esc to cancel, Enter to agree. Progress bars step aside for it as they always
  have: one window per decision.

- 🔐 **The Nexus login no longer lapses every fortnight.** Measured on the cookies themselves: the site
  issues a session that lasts exactly **fourteen days from the last visit** — not "about a month", as it
  feels. Install nothing for two weeks and you are typing your password again. The launcher now visits Nexus
  quietly at start-up (at most once every four days, no window, nothing downloaded): the fortnight starts
  over, and the cookies are rewritten with a year's expiry so the browser never throws away a session the
  site would still accept. Open the launcher once a fortnight and the login holds. Longer than that is the
  site's rule, not ours.

- 🔗 **A mod set travels as one block of text — an RLink.** The profile menu has "Copy the mod set (RLink)":
  the clipboard gets a short `RL1[…]` string holding the mods, their order, their versions and the game
  version. Paste it into a chat or a forum, in the middle of a sentence if you like. On the other side,
  "Paste a mod set (RLink)" finds the block inside the conversation, downloads what is missing, switches on
  what is already on the disk, and puts everything in the same order — picking builds for THAT player's game,
  and saying so beforehand when the set was built on another branch. A 21-mod profile comes to 385 characters,
  a 150-mod one to about 1 100, so it fits in a single message. The game's own parts — War Sails, Birth and
  Death and the rest — stay out of the set: nobody can download them, and a player either owns them or not.
- 🈯 **Translations now travel with the set.** Only mods used to go into the block, so whoever pasted it got
  the mods and read them in English. Both kinds travel now: the ones that install as their own mod and the
  ones that are files laid inside the mod they translate. The block also carries a mod's real name: the
  reference knows some mods only by their page (`steam:3788489879`) while the folder on disk calls itself
  something else entirely — without that pairing the Russian translation of Empires of Europe 1700 simply
  never downloaded on the other end.
- 🔢 **A set's load order is applied once the mods are actually in.** The install runs on its own so the
  launcher stays usable, and the order used to be written the moment it started — onto a profile that was
  still nearly empty. Four mods of thirteen were in place; the other nine landed wherever the installer put
  them. The order, the switches and the update check now happen at the end of the run.
- 🏷 **…and it is applied by the name each mod ACTUALLY installed under.** One mod unpacks into differently
  named folders on different branches of the game — "Europe1700" and "Europe 1700" with a space — and the
  launcher did not recognise the mod it had just installed.
- 📋 **The clipboard is cleared as soon as the install starts**, so the "Paste mod set" button stops offering
  the same set to the profile it has just filled.
- 🔕 **After a set, updates are looked for quietly.** A copy you already have that suits your game is still
  left alone, but the sources are asked at once — and if something newer is out, the "Updates" button lights
  up. No window opens over your work any more.
- 🧭 **The set is worked out BEFORE the first download, and you see what will become of it.** There used to
  be one question — "30 mods in this set, fetch them?" — and then an hour of downloading, after which a third
  of them turned out not to work. Every mod is now decided in advance and shown in one window: how many will
  be fetched, how many you already have and they suit your game, how many are replaced with the build for it —
  and, by name, the ones your game cannot run at all. Those are not downloaded.
- ⚓ **Mods needing a part of the game you do not have stay out of the set.** A set built on 1.5 and pasted
  into a 1.2 game dragged War Sails patches along — and that part of the game does not exist on 1.2. They
  downloaded honestly, 470 MB apiece, and did nothing. The launcher now asks the reference what each mod
  needs from the game itself, compares it with what you have, and names such mods before the download:
  "needs NavalDLC, which your copy of the game does not have".
- 🔁 **A mod you have that was built for another game is replaced with the build for yours.** "Already on the
  disk" used to mean "nothing to do": a 1.5 build was simply switched on in a 1.2 game's profile, and the set
  looked applied. The copy on disk is now judged by the same three witnesses an ordinary install uses — what
  the mod itself declares, what we read in its files, what the reference says — and an unsuitable one is
  replaced. A suitable one is left alone: it is already here and it works.
- 🤐 **Pasting a set no longer asks one question per mod.** Thirty mods meant up to thirty dialogs in a row,
  after you had already pressed a single button. Everything worth asking is now in that one review window
  before the start, and the rest waits on the summary screen, exactly as a batch install does.

- ⚓ **The launcher no longer goes looking online for parts of the game itself.** After installing the
  Empires of Europe 1700 add-ons the review said «"EOP Blood Seas" needs "NavalDLC" and the launcher does not
  know where to get it» — about War Sails, which is bought with the game and downloads from nowhere. The
  cause: the game's own modules were filtered by their PLACE IN THE LOAD ORDER, and the optional DLC
  deliberately have no place — War Sails, Fast Mode and the sandbox fell straight through and counted as
  somebody's mod. A missing part of the game is now described by what can be done about it: "your copy of the
  game has not got it", or "it is there, tick it back on".
- 🃏 **One mod, one card in the review.** "CC's Banners" appeared as three identical cards in a row — one per
  missing game module, same picture, same name. That reads as the launcher having installed the mod three
  times. Everything known about a mod is now on a single card: the worst finding on top, the rest beneath it.
- 🔢 **The headline counts what is on the screen.** "Will not start: 8 of these" above four cards is a number
  whose wrongness is plain to see, and a number like that is one people stop trusting. Cards are counted, not
  findings.

- 🚢 **A mod built for a part of the game you have not got is simply not installed any more.** War Sails
  came with game 1.4: on 1.2 and 1.3 it does not exist, and on any version it is there only if it was bought.
  A patch for it cannot load — in no build, with no tick. Such a mod used to download honestly (470 MB),
  install, switch itself on and stay quiet until the game was started. The launcher now refuses: before the
  download from the reference, after it from the mod's own manifest, and the second cannot be dodged by any
  install path. It is the one refusal on the install path — everything else the launcher finds can be wrong
  and is therefore put as a question, while here there is nothing to be wrong about.

- 🧱 **The game's own modules are no longer called "switched off".** "CC's Banners requires the game module
  «SandBoxCore», and it is switched off — tick it in the mod list" — four such red cards in a row, about
  Native, SandBoxCore, Sandbox and StoryMode. Those are the game: they load always, they are not in the mod
  list and they cannot be ticked. The check could not see them because the review screen hands it the
  profile's mods, and the game's modules are not among those. What the game always loads now counts as
  present, on that screen and before a launch alike.
- 🆔 **One mod under two names is no longer counted as missing.** The reference files a mod under every id it
  has ever been seen under — 259 such pages in the shipped base, 566 rows between them. A mod you have under
  one of those names no longer reads as "not installed" when the requirement names another. Sameness is
  decided by what an install would actually fetch, not by how the name is spelled.
- 🔁 **A mod once found to be built for a missing part of the game is not downloaded again.** The reference
  says nothing about War Sails — only the mod's own files do, and reading those means fetching them. The
  first download cannot be avoided; every one after it can, and now is. Buy the DLC, or move to a version of
  the game that has it, and the record stops applying by itself.
- 🗣 **One reason per mod.** A card first explained that a part of the game was missing and then added a
  vaguer "not installed — it needs code this version of the game has not got". The second sentence is gone.

- 🚪 **"No part of the game — no mod" now stands at EVERY door at once.** It used to be added one door at a
  time, and each time one was missed: the install refused a mod, and "fetch the missing parts" offered it
  again, the window before the download counted it as sound, and it was fetched a second time. One and the
  same answer is now asked by the window before the download, installing by name, "the other files of this
  mod", fetching dependencies, offering the parts of a set, the pack installer, and the gate after the
  download. A test reads the compiled code and fails the moment one door stops asking.

- 📇 **The launcher looks at which version of the game a mod's files are actually published for.** This is
  where the reference fails twice over: it calls EOP Blood Seas "works on 1.2" (naming a build that is no
  longer published) and records not a word about War Sails. Its file list says the thing that matters: the
  only file it has is built for game **1.4**. That is enough not to fetch it onto 1.2 — and it works the
  first time, before any download. ⚠️ A file with no game version on it is "unknown", not "unsuitable": half
  the catalogue leaves it blank, and judging by its absence would refuse almost everything.

- 🔢 **The text and the button in the pre-launch window no longer argue about numbers.** It read "not
  installed: A, B, C +2" — five parts — above a button saying "Fetch the parts (2)". Both numbers were ours.
  The notice was written by the reference from ids alone, the button by the launcher, which also knows what
  is on the disk and what it read in files already fetched; filtered on one side only, the two disagreed in
  front of the player. The notice is now worded FROM the very list the button fetches: one list, two ways of
  showing it. With nothing to fetch there is no window at all, rather than "+0".

- 📋 **Missing mods are now listed in a column, every one of them.** It used to read "A, B, C +2" on one
  line — a list you cannot check, because what hides behind the "+2" is invisible while the button below
  takes all of them. Every part is on its own line now, with nothing shortened away.
- 🔍 **The window before the download shows what each mod IS, and gives it an "about" button.** Under the
  name sits the reference's short description in your language, and beside it a button that opens the mod's
  card: what it does, which builds of the game it runs on, what it needs alongside and what it will fall out
  with. You can read without closing the list — untick what you do not want and take the rest.

- 🪟 **The pre-launch window is the same list now.** It used to be a wall of text over three buttons: the
  names sat in a sentence, there was nothing to read about any of them, and the choice was all or nothing.
  It is now the same list shown before a download — a row per mod, a description, an "about" button and **a
  tick of its own**. Untick what you do not want and fetch the rest; untick everything and the launcher
  simply starts the game as it is.

- 📜 **The explanation in that window scrolls, and no longer touches the edge.** On a set of twenty parts
  the text was taller than any window and pushed the list and the buttons off the screen. It now has its own
  height and its own scrollbar, and the last line does not sit flush against the frame. The names have also
  gone from the explanation — they are the rows just below it, and one list is enough to read once.
- 🔘 **The "about" button draws again.** It was coming out as an empty box: the character had been picked
  from an icon font by number, and that number is not in the font. It is now the same ⓘ the mod list on the
  main screen uses — proven on every skin.

- 🧮 **The launcher no longer threatens a crash over mods almost nobody has.** It used to say: "this is a
  set and not one of its parts is installed — without them the world is usually built incomplete and the
  game dies on the campaign map". The reference's own figures say otherwise: “Empires of Europe 1700” has
  **107,370** downloads, while those "parts" have 4,550, 2,168, 1,214, 1,002 and 431. Ninety-six players in
  a hundred run that mod without a single one of them, and it works. Nor does the reference call any of them
  required: they are filed as add-ons, patches and translations, and the mod's own author marks them
  optional. The warning was predicting a crash that does not happen.
  What is asked now is the one thing that means anything here: **do the people who play the mod itself
  generally take this as well?** A companion nearly everyone installs still counts; a submod for a narrow
  taste — and every big mod has dozens — is no longer passed off as a missing piece.

- 🩺 **When no rule matches, the crash report now shows what the game itself complained about.** It used to
  say "No automatic diagnosis — new/unrecognised signature" and stop there, while the answer sat in the
  game's own log. Three facts now follow that line: how many of which mod's files the game **refused to
  load** (with an example), how many times it looked for an object that was not there, and what it was doing
  last. ⚠️ That log lives inside a crash archive of hundreds of megabytes and cannot be inlined, so the
  launcher reads it straight out of the archive and takes only those lines. On the live crash it reads:
  "Europe 1700 — 924 entries the game refused (lords_swedish.xml); 1 611 references to objects that were
  never created; the last thing the engine said: Ticking map scene for first initialization". The cause is
  visible at once, with no rule at all.

- 🤐 **Search no longer asks again about a mod it has just warned you about.** The row already says, in red
  under the name and beside the button, "will not run on your game v1.4.7". Pressing Install means you read
  it and decided. The "add it anyway?" dialog is gone — and it was opening underneath the search window
  itself, half off the screen, where it could not be read at all.
  ⚠️ The one thing that is not a question stays: a mod built for a part of the game you have not got still
  will not install, however many times it is pressed.

- 🈯 **A translation you have installed is not offered again.** Install Empires of Europe 1700 on 1.4.7,
  the launcher offers the Russian translation, you install it — and it offers it again. And again. Checked
  against your own profile: the reference has only ever seen that translation as a Workshop page and files
  it under "steam:3788489879", while the module unpacked from it calls itself "Europe1700Rus". Every
  "do you already have this?" question compares names, so the answer was permanently no.
  The launcher now writes down **what** each download actually landed as, so the reference's name and the
  name on disk stop losing each other. The same fix ends repeat offers of parts and dependencies fetched
  by a reference name.
  ⚠️ And for the translations already installed, the folder itself is read. A module the reference knows
  nothing about, carrying Russian and nothing else, named after the mod, is that mod's translation — there
  is no point offering it twice. A mod that merely ships eight languages is not a translation.

- 📥 **A mod you already have is not downloaded again — and the question comes BEFORE the download.** A mod
  fetched from a Steam link was already sitting in the game's own Modules folder. The launcher pulled the
  whole thing down and only then said a copy had been there all along. The check that existed compared
  ADDRESSES — "did we install anything from this very page" — and had nothing to say about a copy the game
  itself had put there.
  The question is now asked about the mod, and asked **before** the first byte moves, from any address:
  Steam, Nexus, GitHub, ModDB, a direct link. Provably the same mod at the same version is not fetched at
  all. Anything else is a window with the details — which mod, which version is here, where exactly it
  lies, what the address offers — and three answers: **"Take the one here"**, **"Download anyway"**,
  **"Cancel"**.
  ⚠️ "Take the one here" downloads nothing: a copy in the game folder is switched on where it stands, and a
  copy in another profile is copied across.

- 🧾 **No more duplicates on a mod card.** "Sound Overhaul" twice, "Expanded" twice, "Europe 1500s - Pike
  and Shot" twice — the Empires of Europe 1700 card had five such pairs. The reference keeps one mod under
  two ids, and the card printed every row it was given: 23 lines where there are 17 mods.
  Rows that are one mod now collapse into one line — not by name, but by the reference's own install key:
  all five pairs share one, and one Nexus page. Two of the pairs are named differently on the two rows
  ("Pickles Troops Empires of Europe 1700" and "Pickles Late 1700 Troop for EoE1700"; "War Sails EU1700
  Patch" and "Warsails patch - Empires of Europe"), so names would not have caught them.
  ⚠️ Different mods stay different: two Russian translations of Anno Domini 1259 by different translators
  are two lines and stay two lines. The counts in the headings read the same list, so they follow.

- ⓘ **The "about this mod" button is back wherever a card exists and the button did not.** Install Empires
  of Europe 1700, open the mod list, and there is no button — while the card itself opens from everywhere
  else and reads perfectly.
  The two questions were being asked in different alphabets: the mod on disk calls itself `Europe 1700`
  (with a space) and the reference files that same mod as `Europe1700`. The list asked "do you know this
  one?", got the answer in the reference's spelling, and looked in it for its own.
  The answer now comes back in the spelling it was asked in.
  ⚠️ This fixes more than one button: seven places ask that question — the mod list, the pack install
  window, the update list, "our mods", the journal and two reports — and all seven were silent about the
  same mods. The reference holds 2 522 rows where the folder name differs from the card's key: `Diplomacy`
  against `Bannerlord.Diplomacy`, `EoE1700Assets`, and so on.

- 🏷️ **The launcher can now find a mod by the name the mod calls itself.** A sequel to the entry above.
  The reference answered with a table of every self-name: the module's own id, its folder name, and the
  human name from its manifest — 26 289 spellings. Two of the three existed nowhere before: the folder
  differs from the id for 1 510 mods, and the human name for 5 480 (`Bannerlord.Diplomacy` calls itself
  "Diplomacy", `CustomSpawns` calls itself "Custom Spawns"). No amount of shuffling spaces derives that.
  It is asked as one query from one place, so all seven places got the answer at once.
  ⚠️ When several cards answer to one name, the strongest match wins — the one the game itself uses for the
  module. If several still remain, none is taken: a confident wrong answer is worse than no answer.
  ⚠️ The table arrives with the next reference. Until it does, everything behaves exactly as before.

- 📣 **A pack can now carry a notice to the player — and require that it be read.** Two new fields in the
  editor. The first is the notice itself: what the player must know BEFORE installing. A mod that breaks old
  saves, a step to take before the first launch, a known crash and its workaround. It appears in a block of
  its own, above everything, ahead of the description.
  The second is a tick: "installation may not start until this has been read". Off, the notice is simply
  information at the top. On, it is presented on its own like a licence, with scrolling and an "I have read
  this" box, and the Install button stays dark until the box is ticked.
  ⚠️ The text is per language; the requirement to read it belongs to the pack. If the player's language has
  no notice, nothing is blocked — there is no holding somebody in front of an empty box.
  ⚠️ Closed the window without confirming? Nothing is lost: the notice stays in the block at the top with a
  "Read it and confirm" button beside it. A blocked button with no way to unblock it is a dead end.

- 🧩 **A dependency that is already installed no longer counts as missing.** Switch a mod on, and it says it
  will not run because dependencies are needed — while they are installed and enabled. Checked against the
  owner's profile: the War Sails patch declares it needs "Empires of Europe" — a **human name** — while the
  module beside it on the disk calls itself `Europe1700`. Strings were compared, so the launcher offered to
  fetch what was already there and kept the mod switched off.
  The question is now asked before the comparison: first from the launcher's own record of what each fetch
  produced, then from the reference. ⚠️ Something genuinely absent is still called absent — the point is to
  stop crying wolf, not to stop looking.
- 🗣️ **The "fetch dependency" button no longer says nothing.** Sometimes there is nothing to fetch: the
  launcher refused each one for a reason — "Historical Banner Icons was not downloaded: everything it
  publishes is for game 1.3 and you are on 1.4". That used to go to a status line in the corner, leaving a
  button that looked dead. Now it is a window, with the reason **per mod** — a refusal nobody can see is
  worse than the refusal.
- ⬇ **"Fetch what is missing (N)" at the foot of the mod list.** One button for the whole list: it saves the
  ticks, closes the list and fetches the lot — the order anyone would have to follow by hand. On screen only
  when there is something to fetch.

- ✅ **A tick queues what is needed and downloads nothing.** Switch on a mod that is short of something and
  the missing pieces are collected into a list, with **"⬇ Download what is missing (N)"** lighting up at the
  foot of the window. Press it and the ticks are saved, the mod list closes, and only then does the download
  start. No extra question on the way.
  The button existed before but looked like an ordinary faint one and simply was not found. It is accented
  now, as the answer to what the list is complaining about should be.
  🔴 **And the real cause of "there is nothing there".** A mod's row compared its dependency LETTER BY
  LETTER: the author writes "Empires of Europe" and the module beside it on the disk calls itself
  `Europe1700`. The mod was declared incomplete, the button lit up — and there was nothing to fetch, because
  nothing was missing. That question is now asked by name here too, the same way as everywhere else.

- 🚫 **The dialog that popped up on a tick is gone.** It was the cause of both halves: switch on a mod that
  is short of something and the tick **snapped straight back off** while a question appeared. Press
  "Install" in it and the download started over the mod list; when there was nothing to fetch, that question
  was all that happened.
  The tick now **holds**, what is missing goes into the queue, the row says in red what it needs, and the
  button at the foot counts it. No question and no download until it is pressed.

- 🧭 **Ticking a mod that is short of something ASKS, and puts the files on a list.** Switch one on and the
  launcher asks **"Download the missing files?"**, naming them. Say yes and they go on the list, with
  **"⬇ Download what is missing (N)"** lighting up at the foot of the window. Press it and the window closes
  and the download starts. Nothing is downloaded before that.
  🔴 **And the second problem mod now responds too.** It used to do nothing, and the cause was not the
  interface: a tick on a mod whose file is absent is taken off again — the game would not load it anyway,
  and that guard is right. But the "what to download" list was built from those very ticks, so it emptied
  itself a moment after it filled. It is a list of its own now, and a tick coming off does not disturb it.
  ⚠️ The window no longer resizes under your hand either: the height is fixed and the list absorbs the
  difference.

- 🙊 **"Requires the game add-on «»" will not appear again.** In the window before a download a mod could be
  given a line about a game add-on **with no name** — the window filled a ready-made sentence with an empty
  slot and threw away the real reason it had worked out itself. The real reason is shown now; and where
  there is none, an honest "will not run on this version of the game" instead of empty quotes.

- 📄 **The report after an install no longer says the same thing six times.** For a mod short of five
  others, its card carried **five** copies of the heading "A mod it needs is not switched on", each above a
  near-identical sentence differing in one name. It is one heading, one sentence and the names as a list now.
  Findings that mean different things still get their own paragraph: a clash over game records and a missing
  library are different news.
- 🙃 **A mod is no longer "needed by itself".** The report could carry a line like «"Fire And Sword
  Remake1700" is needed by "Fire And Sword Remake1700"». It happened when a mod was fetched on its own
  rather than for another: the template put its name in both slots. The sentence is shorter now, without the
  "needed by" clause.
- ✅ **The card and the download window no longer contradict each other.** "Historical Banner Icons" is a set
  of banner pictures with no code in it at all, and the reference says plainly: no obstacles on game 1.4.7.
  The window refused to fetch it anyway, because its files are labelled for branch 1.3.
  The branch rule was written for mods whose **code** is built against a version. For a mod the reference has
  read and passed, a label on a file is much the weaker witness, and the verdict now outweighs it.
  ⚠️ Only an outright "works": "in question" and "will not run" leave the branch rule in place.

- 🔤 **The names of missing game pieces no longer break in half.** A mod card could show `!0>)` instead of a
  name. We stripped the assembly prefix in the wrong order, and a generic parameter is written `!!0` inside
  a method signature, so the split fell on that. Measured against the shipped base: **264** mentions were
  mangled, most often `AddModel`, the commonest entry point for a game model. The order is fixed; the
  encyclopedia reported it — they had the same bug.
- 🧩 **The "will not start" verdict is lifted from 178 mods, yours among them.** It turns out the game does
  not open every library in a mod's folder: some are named in the manifest and receive events, some are
  merely loaded, and some are named nowhere and run only if something calls them. The verdict on Empires of
  Europe 1700 rested entirely on the last kind — on `CustomSpawns` and `ItemCategoryAddons`, other people's
  mods packed inside it. It now reads "in question", which is the truth: the mod plays and falls over on the
  way out.
  Such findings are not hidden — they carry the line "the game does not open this part of the mod itself".
  And no moment of failure is claimed for them: they receive no handlers, so there is nothing to base one on.
- 🌍 **Plain-words descriptions of game pieces — in all six languages, and for almost everything.** It was
  Russian only and covered one name in seven; it is now six languages and **96 %**. Short names are taken
  from the reference too rather than derived by us: `CultureCode` and `CampaignGameStarter.AddGameMenu` look
  identical from outside and must be shortened differently.
- 📥 **If the wrong build of a mod arrives, you are told at once.** The launcher already knew, a second and a
  half after unpacking, that the binary was built against another version of the game; the reference already
  knew which build suits yours. The three facts were never joined: 4.2 GB stayed in silence and the update
  list offered the right build afterwards as if it were news. Now it is in the same window: "the reference
  records build 1.4.7.1 for game 1.4.7 — this is not it", with the address when one is known.
- 🔎 **"Add existing" says why a mod is not in the list.** A line at the top: "Already switched on in this
  profile: N. Those are not listed here — there is nothing to add." An absence with no reason is
  indistinguishable from a loss.
- 🔊 **Voices of Calradia is now offered to everyone running the launcher in Russian.** It used to appear
  only in a profile with a particular name. The language is the whole condition now. Its card opens too —
  the reference has both a description and a picture for it (checked).

- 📖 **"What the author says" folds up on a card — and starts folded.** With a talkative author that block
  grew longer than the description itself and sat ABOVE it: on Empires of Europe 1700 it ran six hundred
  pixels, so the description somebody opened the card to read began somewhere off the screen.
  It is now one line: **▸ What the author says · notes: 8**. A click opens it, another closes it.
  ⚠️ The count beside the heading is not decoration: a chevron on its own is a shape, "notes: 8" is a reason
  to press it. The row lights up in the skin's own colour under the pointer.
- 🚫 **The "Replace" button is gone — and what it promised never happened anyway.** The launcher never
  touched anybody else's copy: what you download goes into your profile alone. But the window said
  "Replace", which is a promise to reach into someone else's. The answers are now called what they do —
  "Use the downloaded one here" and "Keep the one that was here" — and the text says outright that the copy
  already there is left exactly as it is, whichever profile it belongs to.
- 🔤 **Raw machine text no longer reaches a window.** A question about a mod was showing a slice of the
  reference's internal data: `[{"asm": "CustomSpawns", "sev": "critical", …}]`. In its place is a sentence:
  "It reaches for game code this build has not got: CustomSpawns…".
- 🔘 **The "Paste a mod set (RLink)" button appears by itself** — on the main screen, exactly while a set is
  actually on the clipboard. Copy a block out of a chat, come back to the launcher, and the button is already
  there; with nothing to paste there is no button at all, neither on the screen nor in the profile menu. No
  more disabled buttons explaining that there is nothing to paste: that is not a choice, it is a dead end.
- 🔌 **A mod already on the disk is switched on instead of downloaded again.** It happens constantly: the mod
  sits in the game folder or in another profile, but not in this one. The launcher used to answer "already
  installed" and do nothing — a six-mod set pasted in changed the profile by precisely nothing and opened an
  empty review screen. Now it switches on what it found, and says so in the log.
- 🔧 **The launcher knows Harmony is needed by mods that never say so.** A mod declares the libraries it needs
  in its own file — and plenty of authors simply do not: the mod loads, does nothing, and there is nowhere to
  read why. For our mods (RTS Camera Universal, Crash Doctor, Lore-Hardcore) this is now written into the
  launcher itself: Harmony is offered alongside them, and it travels with a profile that moves.
- 🧾 **An "Install log" button on the screen that follows an install.** One file about one run: what was asked
  for, what arrived, what did not and why, the game version, the reference, the profile's mods with their order
  and versions — and the launcher's own log lines from exactly that run. Send it to us and the cause is in it.

- 📦 **Every mod says how much disk it takes.** "1.2 GB", quietly, next to the name: once a catalog is forty
  gigabytes deep, "which of these is the big one" is the first question before deleting anything. Sizes are
  measured after the list is drawn, and not measured at all while a shader build or the game is running.
- 🧱 **A mod published as several required files is installed whole.** "Tales from the Age of Men" ships as
  two files — 11 GB and 17.4 GB. The launcher fetched one, and the whole family of mods switched itself off
  with "the library is missing": the missing pieces were in the other file. It now notices that a mod is
  incomplete, says how big the rest is, and offers to finish it — and when a required mod is nowhere to be
  found, it first asks whether it is sitting in a part nobody downloaded.
- 🧩 **A mod that is not published on its own is no longer a dead end.** Some mods are folders inside another
  mod's archive: "LOTRAOM" and "LOTRLOME_Armory" arrive inside "Tales from the Age of Men". The launcher used
  to answer "I don't know where to get this", sending people after a file that does not exist. It now says
  which mod carries it and offers to install that one.
- 🔁 **When the reference's address holds the wrong file, the launcher tries the next one.** A mod usually has
  several addresses. For "TAOM" the reference pointed at an archive with no mod in it at all — and that was
  the end of it: mods needing TAOM were installed without it and the player was told to go and find it. A
  failed address is now set aside and the next one tried — the mod's Nexus page, for instance, which the
  launcher can fetch from by itself.
- 🚫 **No more browser where there is nothing to download.** For "LOTRAOM" the first recorded address was a
  source-code repository with no releases at all, so the launcher opened a page of code under the caption
  "sign in and press Download" and waited for a file that will never exist. Addresses are now tried in the
  order they can actually hand over a mod: Nexus, the Workshop, ModDB, a GitHub release — and only then
  anything else.

- 🗿 **Mods from ModDB install at last.** Thirty-nine mods in the reference are published nowhere else, and
  nothing was ever fetched from ModDB automatically — the site has no API and no permanent address for a
  file. The launcher now walks its pages to the file itself: mod page → file list → file → the mirror. The
  countdown drawn on the page does not have to be waited out. ModDB publishes no checksum, so what arrives
  is checked by unpacking it.
- ⏸️ **A download carries on from where it broke off.** Mods on ModDB run to thirty gigabytes and do not
  come down quickly — a day of transfer, over which a dropped connection is a matter of when, not if, and it
  used to mean starting the whole file again. What has arrived now sits in a file of its own beside it, and
  the next attempt asks the server to continue from that byte. The site's link lasts about two hours; when
  it expires the launcher walks its way to the file again and picks up where it left off. It survives a
  restart of the launcher too.
- 🗜️ **A ModDB archive is not necessarily a zip.** Of the first five files, three were `.rar`, one `.7z` and
  only one `.zip`. The extension is taken from the file's real name — otherwise a perfectly good archive was
  declared broken.
- 🧱 **The unpacker grumbling no longer cancels an install.** Some mods ship an archive with rubbish after
  the end of the data — one of them with 16.8 GB of it. 7-Zip complains, then reads the table and gets the
  files out anyway. What came out is what counts now, not the exit code.
- 🚦 **When ModDB asks us to wait, the launcher waits instead of pushing.** The site limits how often it
  can be asked; told to stop, the launcher stops and says so rather than trying again and again.

- 🧺 **Mods are picked into a list.** Press "Install" as often as you like — in search, on a card, in its
  "needs alongside" and "made for this mod" lists. What you picked turns green everywhere at once. The
  list runs when you close the search window or the last card.
- 🤫 **Two mods or more install without a single question.** It used to stop at the first "this needs
  Harmony — fetch it?", "this clashes with two of yours — install anyway?", "there is no build for your
  game — take the neighbouring one?". Forty mods take an hour to download: you go and make tea and come
  back to a launcher that fetched three of them and spent fifty minutes waiting for a click. Every one of
  those questions is now answered up front — fetch it, install it — and the questions themselves are put
  up afterwards, together. Installing a single mod is unchanged: it asks.
- 🪟 **One window for the whole run, not twenty in a row.** Two bars — how much of the current mod has
  arrived, and how many mods of the list are done — and a list: what is installed, what is downloading,
  what did not make it. "Cancel" stops the list, not just the current download.
- 🧾 **At the end, an "Install finished" window.** The headline first: will the game start or not. Then
  what happened during the run, and separately what no single install could have known — how the **whole
  profile** now looks. Which mods do not work on your game, which pairs clash, which one is missing
  something that is switched off. Problem mods carry a "switch off" tick; the whole run carries "remove
  everything installed just now" — if the mod you came for did not make it, the other nineteen are of no
  use.
- ⛔ **"Cancel" cancels, it does not install.** Only "Install selected" starts the run.
- 🎵 **Add-ons go inside the mod they were made for** — music, textures, scenes, compatibility patches.
  Only the one-button install used to manage that; anything picked into a list was unpacked into a folder
  of its own, which the launcher opened in Explorer without a word.
- 📄 **When the files really cannot be placed, it says why.** Either the archive holds no mod data folders
  and the author expects you to copy things by hand, or it carries program files — those are never written
  into somebody else's mod. Both used to end with a folder opening and nothing said.
- ⚠️ **Clashes are raised before the download.** If a new mod describes the same game records as ones you
  already have, the launcher lists them and asks. Sometimes that is deliberate, so it is a question, not a
  refusal.
- 🛑 **A mod known not to run is raised before the download too,** rather than after the files are on
  disk. And what the launcher works out for itself, it remembers: whether a mod needs game code your build
  does not have can only be told from its files, i.e. after fetching them. There is no need to pay for
  that answer twice. A new version of the mod clears the note — nobody has looked at that one.
- ⬇️ **The launcher decides where to fetch from** — GitHub, the Steam Workshop, Nexus, ModDB.
- 🔑 **A Nexus key (it is free) makes installing quicker.** Where the address does not name a file, the
  launcher asks Nexus which one it should be and opens that.
- 🖼️ **Mod artwork now appears in every list** — search, updates, translations, recommended mods and "add
  an installed mod".
- ⏹️ **Cancel means the same thing everywhere — stop.** Installing one mod cancels that mod; installing a
  list, our own mods or a batch of translations stops the whole run, not just the row it landed on. In our
  own mods a cancel during a copy used to be swallowed, and the launcher then started downloading the very
  mod you had just stopped.
- ⏹️ **Cancel now stops the unpacking too, not only the download.** While an archive was unpacking, or a
  Workshop mod was being copied into the profile, the button did nothing — and that is the long wait:
  gigabytes of unpacking and copying. It stops now, and takes the unpacker with it.
- 🛑 **Cancelling is an answer, not an error.** Press Cancel while a mod is unpacking and the launcher used
  to say "Mod installation error: The operation was canceled", with the review screen listing that mod as
  one that failed to install. It now says what happened — the install was cancelled; the row is marked as
  skipped, and the rest of the list stops, the way it was meant to.

### Which build of a mod your game needs

- 🩹 **The card names the NEWEST build that runs on your game, not the oldest.** The reference keeps one row
  per branch and it holds the earliest file that passes there: on 1.5 that was Crash Doctor v1.4.0.7 from
  June, while v2.0.3.7 from August is checked and working on that same 1.5. People install current builds, so
  a current build is what they need compared; and somebody on an older game wants to know the newest build
  that still goes on it. Both the branch row and the "what do I install" answer now name the newest checked
  and working one. Where no clean build was checked at all, the one that runs with reservations is named —
  and said to be exactly that.
- 🎨 **What the author says is readable now.** The answer was printed in the muted grey used for things you
  may skip, and on the darker skins the block simply could not be read. The answer now takes the body text
  colour, the author's quote is larger, and repeated entries of one kind (some authors list the languages
  twice) sit under a single caption instead of two identical headings in a row.
- 📏 **The list of checked builds is no longer a wall.** Crash Doctor has twenty-two of them on branch 1.5,
  all equally green. Ten newest are shown and the rest are counted on the line below.
- ↕️ **The newest branches of the game are at the top now.** The list ran 1.0, 1.1, 1.2 … and the row about
  your own game — the one row the card is opened for — sat at the very bottom, under four rows about games
  nobody runs any more.
- 📐 **The branch rows line up in columns.** The row for your branch carries "— installed", which makes it
  longer than the rest, and that pushed its mod version, badge and explanation a centimetre to the right, so
  the table stopped reading as a table. All rows now share their columns, and the list of checked builds got
  the same treatment.

- 🆕 **A mod card now carries the author's own word: does it need a new campaign, is it safe to remove, where
  it goes in the load order.** The reference collected these from the mods' own pages — 11 714 of them across
  4 268 mods, translated into all six languages. The one that matters most is lifted to the top and
  highlighted: **461 mods require a new campaign**, so adding one to a save in progress is pointless, and the
  launcher used to say nothing about it. Beside it, in as many words: this is the author speaking, unverified,
  not a finding of the launcher's.
- 🆕 **And the list of every build of the mod checked on YOUR branch of the game.** The card used to show one
  row per branch, chosen by rules invisible from outside — which is how a 1.2 game was offered a Harmony from
  2022, and how Crash Doctor's July build was called the newest while an August one sat in the same database.
  Now every checked version is listed with its verdict and date, and the one you have is marked. The list
  appears once the new reference database ships.
- 🎚 **Branches of the game nobody plays any more are muted** — the whole early-access line and the releases
  below 1.2. Muted, not hidden: a mod checked only on 1.0 is not unchecked, and dropping the row would say it
  was.

- 🩹 **A mod card no longer calls an old build "the latest".** Crash Doctor's card said 1.8.4.4 while the very
  same reference database held the file "CrashDoctor v2.0.3.7", uploaded on 29.08. The database was not stale:
  "newest" was read from the per-branch table alone, and that table is rebuilt from checks and lags behind the
  file list — 795 mods in the base are affected. The files are now counted too.
- 🩹 **And it no longer recommends a build that was never released for your branch.** For some mods the branch
  row is not "the build for it" but simply the oldest one that happens to run there — the reference marks
  those. The card was presenting that as the answer to "what do I install". It now says plainly that the
  reference knows no build made for your branch, names the newest it does know, and links to the mod's page
  instead of handing over a number.

- 🎯 **The build that suits your game is installed, not the newest one.** MCM on 1.4 is 5.12.2 and on e1.7
  is 4.7.11; Harmony on 1.2 is 2.3.6.0, not 2.4.2. On an older game the newest build does not load and
  says nothing about it: no crash, no line in the log, the mod is simply not there.
- 💬 **It says why that build.** When the newest one is the right one, nothing is said — that needs no
  explanation.
- 🧾 **The card names the build your game needs** — "your game is 1.2, take 1.5.7" — with a button to that
  exact file.
- 📂 **Files from the mod's page are marked with the one for your game.** On Nexus the right build is
  usually buried under OLD FILES; the row opens it directly.
- 🧷 **If there is no build for your game at all, a neighbouring one is offered — and said to be one.**
  The choice is yours.
- ⚠️ **False "this mod is for another version" warnings are gone.** 1.2.10 and 1.2.12 are the same version
  of the game, and a mod for one runs on the other. And where we have checked a mod against your game
  ourselves, our finding outranks a line in the mod's own files.

### What is known about compatibility

- ⚓ **“This mod needs a game add-on you do not have” is now said before the launch.** War Sails shipped
  with 1.4, so on a 1.2 install a mod that requires it cannot work and no tick will help. The launcher reads
  the requirement from the mod's own manifest and compares it with what this copy of the game actually holds —
  the reference is often silent about such dependencies, the file on disk is not. It comes up before the
  start, like the other notices that precede a crash.

- ⛵ **Only the parts your build of the game can use are fetched.** The first version of the button queued
  everything the reference links to the mod — War Sails patches onto game 1.2, where that DLC does not exist,
  Europe 1500 from another century, and a page key with no module behind it. A part is now offered only when
  the reference says “works” on your branch: broken, risky and “nobody checked” are not a yes. The rest stays
  available by hand, from the mod's card, where you can see what it is.

- 🧰 **The pre-launch window now has something to press besides “play anyway”.** When parts of a set are
  missing, the first button is “Fetch the parts (N)” — installed as an ordinary batch, with the review screen
  and the rollback people already know. When the parts are on the disk but unticked, it is “Switch the parts
  on (N)”. And Cancel is always there: in the first version of this window it was invisible, because the
  button's label arrived empty.

- 🛑 **Three notices ask before the launch again — and only three.** The rule about not throwing a wall of
  text at somebody reaching for Play stands: clashes and “part of this mod will misbehave” still wait behind
  the button beside PLAY. But “not one part of this set is installed”, “a part of the set is switched off”
  and “a module of the game itself is off” now come up before the start: they predict a crash rather than
  describe a quirk, and each carries an action — fetch, tick, restore. Buttons: play anyway, or cancel.

- 📦 **The launcher names the parts of a set you do not have — before the launch.** A big mod rarely lives
  alone: it has add-ons, and without them the world is built incomplete and the game dies on the campaign map
  saying nothing useful. When the reference knows three or more parts for a mod and the profile has none of
  them, they are listed before the game starts. The moment even one is there — installed, or merely unticked —
  the launcher goes quiet: from then on it is your call. Translations do not count as parts.

- 🔤 **A typo in a manifest no longer looks like a missing mod.** UIExtenderEx requires both
  “Bannerlord.ButterLib” and “Bannerlord.ButterLub” — the second does not exist, yet it is the one marked as
  required. The launcher dutifully warned in red, before every launch, that Bannerlord.ButterLub was not
  enabled, while the real ButterLib sat enabled one row above. A requirement no catalogue knows that differs
  by a single letter from an enabled mod now reads as the author's typo and is left out. With the real mod
  absent, the requirement is still named.

- 🧩 **“Part of the set is switched off” is now said before the launch.** When a mod has add-ons or
  patches that sit in the profile installed but unticked, the launcher names them before the game starts.
  This is exactly how an evening is lost: Empires of Europe 1700 launched without its own parts, the game
  died at the first tick of the campaign map, and its log held 1 611 “no such object” lines about troops and
  bandits — with nothing on screen connecting the two. Translations are left out of this: playing in the
  original language is a choice, not a fault.

- 🧩 **A switched-off module of the GAME is no longer passed over in silence.** Many mods will not start
  without `SandBoxCore`, `Sandbox`, `StoryMode` or `CustomBattle` — the reference carries 3 373 such
  requirements. When one of those is off in the list, the launcher says so before the launch and names the
  mods that need it. It is worded apart from “a mod is missing”: nothing has to be downloaded, the tick just
  goes back on.

- 🟡 **Four answers instead of two:** works, loads but one feature will fail, in question, will not run.
  The colours are the reference's own: green, amber, red.
- 🛑 **The launcher will not install a mod built for a newer game — on any path.** A mod states in its own
  files which game it needs, and that question is now asked everywhere: updating, installing a pack, an
  RLink set, installing by hand, adding a mod you already downloaded, and the check before launch.
  Previously five libraries (Harmony, ButterLib, UIExtenderEx, MCM and MBOptionScreen) were never asked at
  all — and a profile on game 1.2 was offered an update of Harmony to the 1.3+ build, after which no mod in
  it works at all.
- 🔍 **It names what the mod is missing** — not "will not run" but "reaches for something this version of
  the game does not have", with the names. That is something you can take to the author.
- 🎯 **And it names the part of the mod responsible.** A large mod carries a dozen other people's mods
  inside it, and usually one of them is what breaks — for "Empires of Europe 1700" it is a stale copy of
  CustomSpawns, while the Custom Spawns API itself works. Instead of "this mod will not run", the launcher
  says what exactly is in the way.
- 🗣️ **Where the answer comes from is in words:** "by reading the mod's code", "on the author's word",
  "the mod carries no code — there is nothing to break".
- 🚦 **Clashes and incompatibility show in the mod list itself**, not only on the card. Clashes are with
  your profile's mods only.
- 🧩 **One line per clash, and it says what is being claimed twice:** "the same settlements — 458, troops
  — 132". A mod that clashed over both items and troops used to appear as several identical lines with
  different numbers, which read as the launcher stuttering.
- 🎨 **Red is only for what will definitely not run.** A clash over records is amber however large: the
  mod still loads and plays, and plenty of clashes are deliberate — that is what compatibility patches do.
- 🎮 **The check knows six builds of the game: 1.2.10, 1.3.15, 1.4.5, 1.4.7, 1.4.8 and 1.5.1.** On 1.5 the
  launcher used to say nothing about mods at all — it had nothing to say. It now answers for itself on
  any of these builds, offline, and names what the mod is missing.
- 🩹 **A clash comes with an answer** where somebody has published a patch for that exact pair.
- 🦠 **If a scanner on the mod's page flagged its file, that is said** — exactly that, not "this is a
  virus".

### What a mod needs alongside
- 🪪 **A dependency is looked for under every name the mod may have installed under.** A mod asks for
  `EoE1700`; the mod that answers to it unpacks as `Europe1700` on game 1.4 and as `Europe 1700` — with a
  space — on 1.2. The launcher writes those pairings down itself but asked only for the first one, and on 1.2
  it switched off a working mod, naming a dependency the player had never heard of. Every known name is tried
  now.

- 🚪 **A mod switched off for a missing dependency no longer reaches the game.** The launcher took the tick
  off but wrote it nowhere: the profile still listed the mod, the next rebuild put the tick back, and the
  launch — assembled from the ticks at that moment — took it along. The journal shows the loop: switched off
  at 06:00, at 06:10, at 06:12, and twice more after the game had already started with it. The tick is now
  saved the moment it comes off, and the launch list refuses a mod whose requirement is missing whatever the
  tick says: the engine looks for it by name and loads nothing without it.

- 🔁 **The pre-launch window no longer offers to switch on what cannot be switched on.** A mod missing a
  requirement is switched off by the launcher itself — and the launcher then offered to tick it back on. The
  tick came straight off again, and the same window returned on the next launch. Such mods are out of the
  offer now: a tick is not what they are short of.

- 🧾 **One line per switched-off part, not one per link.** An add-on written for three mods of the same
  family announced itself three times over — “installed but switched off, it was made for…” with a different
  tail each time. The news is the part, not the pairing.

- 🪪 **“The mod is not installed” when it plainly is — now explained.** “EoE1700 Polish Troops” requires a
  module named `Europe1700`, while the mod sitting next to it calls itself `Europe 1700`, with a space. The
  game matches these literally and will not pair them, so the warning is right — but it read as a launcher bug,
  with that very mod shown installed and ticked one row above. The launcher now says plainly that the mod is
  here under another name and that downloading will not help: the same folder would arrive again. This is the
  mod author's mistake and only they can fix it.
- ⚓ **A part of the game is no longer offered as a download.** “EOP Blood Seas” requires `NavalDLC` — that is
  War Sails, a part of the game rather than a mod. On 1.2 it does not exist and cannot, yet the launcher listed
  it among missing mods behind a “download and enable” button with nothing behind it. Parts of the game are now
  recognised by name, installed or not.

- 🔁 **The pre-download window no longer warns about what it is about to fix itself.** It judged the picked
  mods without looking at the profile or at its own plan: it said “this mod needs Polish Winged Hussar and it
  is not enabled” — and promised, in its own footer, to fetch that very mod. A missing dependency is no longer
  listed when it is already installed or already queued to be fetched.
- 🧱 **The dependency chain now has a ceiling — 25 mods.** Depth was already bounded (six passes) and cycles
  were guarded by the tried-already set, but width was not: a mod needing three mods that each need three more
  is a legitimate chain and nothing said where it ends. The launcher now stops at the twenty-fifth, names what
  is still missing in the log, and says so. Only what a mod cannot run without is ever fetched — optional
  add-ons are never pulled in.

- 🩹 **"Load me after this one" is no longer counted as a requirement.** The reference holds 1 312 such rows —
  load-order wishes, not "will not run without it" (ButterLib asks to load after Native, which does not mean
  Native has to be fetched). They inflated the card's "N of your mods need this" and could make a pack install
  pull in mods nobody asked for.
- 🏷 **The "Needs alongside" tab is called "Dependencies".**
- 🧹 **And it no longer lists the optional.** RTS Camera Universal had "The Old Realms — Russian — optional"
  and "War Sail DLC — optional" on it: mods the author merely mentions. Three rows where one mattered, and
  the reader had to work out which. What is left is what the mod does not run without, plus the "do not run
  these two together" warnings.

- 🩹 **"These mods cannot load" no longer appears over a game that runs.** The pre-launch check compared your
  framework library against a single row of the reference — "which build does your branch of the game take" —
  and called everything else incompatible, in red. On game 1.2 with Harmony v2.3.6.220 that was simply untrue:
  press "launch anyway" and it all works. The reference's row for 1.2 turned out to be junk (a build from June
  2022 — the very same one recorded for the pre-release branch e1.8), while the OLDER branch 1.1 is answered
  with a NEWER build. The launcher now asks the whole table instead of one row: which branches of the game does
  the reference name THIS LINE of the library for? Line 2.4 is named for 1.3 and 1.4 only, so it has no business
  on a 1.2 game and is still flagged. Line 2.3 is named for 1.0 and 1.1 — an older build of the library, and the
  game runs it. One bad row can no longer condemn a working install.
- 🔁 **The launcher no longer argues with itself about frameworks.** In the log it looked like this: at 20:14:56
  the pre-launch check demanded Harmony v2.2.1.79 and installed it; at 20:15:37 the update pass offered
  v2.3.6.220 from the pack and put it back. Forty-one seconds, and both sides of the argument were ours. The
  update pass now asks exactly the question the pre-launch check asks: a build from a line the reference names
  only for later branches of the game is never offered at all.

- 🩹 **A mod installed only in part is now visible, and offers to put itself right.** When a mod names a
  library of its own that is not on the disk, the game starts, shows an error box on the loading screen and
  carries on — while the mod does nothing at all, because its code was never there. The launcher had noticed
  this for a long time but only wrote it to the log, since it does not stop the launch. It now says so before
  the start and, when the profile came from a pack, offers to reinstall THAT MOD alone — the rest of the
  pack is not touched at all. Asked once per mod set, not on every launch. When there is nothing to
  repair from, the window says so instead of showing a button that would refuse when pressed.
- ❓ **The launcher asks before fetching a dependency again — and says why.** The question was dropped
  because Harmony, ButterLib and MCM are a few megabytes and the extra window was just in the way. But the
  launcher does not decide the size: down that same path 3.6 GB of a total conversion once went over the wire
  in silence, in answer to a window being closed. It now always asks, and the question spells the reason out
  line by line: "AD1259 — required by 'AD1259 Russian Translation'". One look is enough to tell a sensible
  fetch from a nonsensical one. Press "Download and install" in the pre-launch window and it will not ask
  twice — that question has already been put.
- ⏳ **While another install is running, the pre-launch window offers to wait rather than to download.**
  Start a mod update, switch to another pack that turns out to be missing files, and the launcher cheerfully
  offered "Download and install". Pressing it would have started a second job writing into the same folders
  the first one was working in. The window still says exactly what is missing, but in place of the button
  there is now a line: this job is running, wait for it to finish and open the profile again. "Launch
  anyway" stays where it was. No button that would refuse when pressed — the same rule as everywhere else.
- 🛠️ **The "these mods cannot load" window now fixes it instead of only reporting it.** It used to name the
  missing library, name the mod that provides it — and offer nothing but "launch anyway". There is now a
  **Download and install** button: the launcher fetches what is missing and looks again.
- 🩺 **And it checks that a library already installed is the one this branch of the game takes.** A Harmony
  installed by hand from the wrong page stops the game exactly like a missing one while looking perfectly
  fine. The list now says "you have build 2.4.2, this branch takes 2.3.6" — and the same button fixes it.
- 🎯 **But only for the libraries that really do differ between builds of the game.** Harmony is one: older
  games take 2.3, newer ones 2.4. ButterLib, UIExtenderEx and MCM ship a single build for every version, and
  for those "newer" does not mean "from the wrong branch". The rule used to be the same for all of them, so
  an ordinary ButterLib update left the launcher refusing to start the game.
- 🔢 **A mod's version is no longer left over from the previous one.** Some mods arrive without a version
  number of their own, and the one from the last install stayed behind in the folder — so the launcher
  showed a version that was no longer there and kept demanding the fix it had just applied, however many
  times you reinstalled.
- 🧹 **One line per reason.** A mod made of several files used to repeat the same complaint three times over.
- 🧷 **The libraries a mod needs are fetched straight away, whichever way it was installed.** A mod added
  through "recommended" or brought in by a pack could arrive without Harmony — and the launcher would then
  switch it off before launch for the very library it never offered to get. Every route asks now, and for
  the build your branch of the game takes.
- 🔍 **And it asks the mod's code, not only its manifest.** Many authors mark every dependency "optional" so
  the game starts regardless, which means a mod that cannot run without Harmony formally requires nothing.
  The launcher now reads what the mod actually calls into.
- 🧩 **Harmony, MCM or anything else that is missing installs with one button,** in the build your game
  needs. The launcher used to know four libraries by name and leave the rest to you.
- ✅ **What it fetches is read against your game like any other mod.**
- ✅ **"A mod you already have" now lists only what is not already switched on.** It used to ask whether a
  row existed rather than whether the mod was on, so things already added kept being offered. A mod that is
  in the profile but switched off is offered too — and picking it simply switches it on, with no second copy.
- 🚢 **The game's own add-ons — War Sails and the rest — are now where people look for them.** Such an
  add-on lives in the game folder and has always been a row of its own in the mod list, but among thirty
  others nobody found it: they opened "add a module" and looked there. Now it is there too, under "a mod you
  already have (from profiles, packs, the game)".
- 💾 **A mod that is in the game folder is no longer copied.** Anyone who added War Sails by hand got a
  thirty-two-gigabyte copy the launcher then ignored — the game loaded the original from its own folder
  regardless. Such a mod is now simply switched on where it lies.
- 🧷 **"Load me after this mod" no longer reads as "does not work without it"** — those are different
  things in a mod's files, and the launcher treated them alike, demanding a mod you did not need.
- ⛔ **A mod that is missing another mod is no longer switched on for nothing.** The game looks such mods
  up by name and, failing to find them, simply does not load whatever asked for them. The launcher used
  to tick the box anyway and show a dialog with a single "Understood" button — reporting a problem and
  doing nothing about it. The box now stays off, the row carries a ⛔ with the reason, and the dialog
  offers to **download the missing mod** — after which the mod switches itself on.
- 🗂️ **When a link from the reference turns out not to be a mod, the launcher says so** — and does not
  leave a stranger's files in your folder. It used to unpack them into `UnrecognizedMods` and open
  Explorer, as though you had brought an odd archive yourself; but it chose the address, not you. The
  same file is not downloaded twice, and instead of an empty button you are offered to **open the mod's
  page** — the reference usually has one even when it has no file to fetch.
- 🧹 **Mods already switched on with something missing are switched off when the mods list opens** — and
  the launcher says plainly which ones and why. Cancel puts everything back.
- 🟡 **Before launch you are also told when a mod will load but one of its features will not work.**
- 🚫 **Decline to launch and there is no crash report any more.** Pressing Cancel in that window used to
  bring up a crash analysis for a game nobody had started: the launcher was reading a mark left in the
  game's settings by a real crash earlier on. The analysis now runs only if the game actually started.

### Mod translations

- 🔎 **A translation that arrives as its own mod is now checked like any other mod.** It was the one install
  path in the launcher without that check: a translation built for another branch of the game was installed
  and switched on unread. From the outside that looks like "I installed the translation and the graphics
  broke". Its files are now read against YOUR game exactly as an ordinary mod's are, and an unsuitable one is
  left uninstalled instead of quietly breaking the mod it was written for.

- 🛑 **A translation can no longer rename the mod it translates.** Some translations are packed as a copy of
  the mod's folder — `SubModule.xml` and all. Installing a pack copied such an archive over the mod whole, and
  a 331-byte file took the place of the mod's own 11 KB manifest: the 3.6 GB "Anno Domini 1259" started
  telling the game it was `AD1259_Russian` and required `AD1259` — itself. The profile switched to the new
  name, every mod that needed `AD1259` was left with nothing, and the launcher went off to fetch 3.6 GB of a
  mod that was already on the disk. An overlay now writes only its own files: the mod's name, version and
  dependencies stay its own. A translation shipped as its own module installs exactly as before.
- 🌍 **The "Translations" button installs translations for all your mods at once.** The launcher works out
  which of them have one in the launcher's language and offers a list with tick boxes. The button appears
  only when there is something to install.
- 🔴 **Only translations for THIS profile's mods are offered.** Mods sitting in the game's folder or in
  another profile used to get into the list — you cannot see them in the profile, yet translations for
  them were offered.
- 📄 **A translation that is a set of files rather than a mod installs too** — into your copy of the mod,
  so the other profiles do not get it.
- ↩️ **One button takes it back out:** the green language tag on the mod's row restores the mod exactly as
  it was.
- 📁 **A translation packed as "just the RU folder" is placed for you.** Plenty of authors do not pack the
  `ModuleData\Languages\RU` chain — they write "drop this folder into the mod" on the page instead. Those
  translations downloaded and then installed nothing: the window said "Installed: 0". The missing folders are
  now worked out — from the language folder in the archive, or, when there is none, from the language the
  files themselves name. Removing such a translation is still one button.
- 🖐️ **And when it really cannot be placed, the files are not lost.** They are kept in a folder named after
  the translation, the launcher says where, and opens it: the translation is downloaded, all that is left is
  copying it in by hand as its page describes. That case used to say only "could not be fetched".
- 🧷 **A mod that already carries its own translation is left alone.**
- 🎭 **A mod with a similar name is no longer passed off as a translation.** The reference links some
  translations "by family of names", and once that produced "No Fog Of War" as "the Russian translation of
  Fog Of War" — two different mods by two different authors, with opposite purposes. Such a guess is now
  accepted only when the translation itself names your language ("…Ru", "…RUS", "Simplified Chinese") or the
  reference really does file it as a translation.
- 🏷️ **The line under a translation no longer claims more than it knows.** Every link the author had not
  declared used to read "link worked out from the files" — even when no files had been looked at. Three
  honest answers now: stated by the author, worked out from the files, guessed from the names.
- 🛡️ **A translation no longer replaces the mod it translates.** Some translators pack a copy of the mod's
  own `SubModule.xml`, id and all. Such an archive installed AS the mod: it landed on top of the real copy
  and took its `bin` folder with it — so installing a text translation stopped the mod from working. It is
  now laid inside the mod like any other translation, and the mod's name and version stay its own.
- 🚫 **There is a "stop offering a translation for this mod" button.** The refusal is remembered, and can
  be undone from the history.

### Mod updates
- ⚖️ **Our mods come from wherever the version is newer.** GitHub and our server are filled by different
  hands and drift; the launcher used to take whichever answered first. Now it asks both, compares the
  numbers and fetches the newer one; the "new version" tag and the "from where" label in the updates list
  say the same.


- 🎯 **A build is only offered as a replacement when the installed one does not work.** The first version of
  this check treated “risky” as a reason too: somebody on Fire And Sword 1.2.12.3 was offered a “fix” of
  1.2.12 — an older build, itself only risky, listed among updates. The reason is now “will not run on your
  game”, and the replacement must be a build the reference CHECKED on your branch and calls working. If there
  is none, the launcher says nothing.

- 🩹 **The launcher now offers a working build even when it is OLDER than the installed one.** Every check
  used to answer the same question — “is there anything newer?”. Sometimes it is the other way round: the mod
  is on its newest release and that is precisely what will not run on your game. Empires of Europe 1700 is
  exactly this — every build is broken except 1.2.9 on game 1.2. When the reference calls your build unusable
  on your branch and knows a file checked for that branch, it is offered and labelled “the build for your
  game”. Nothing is offered for a mod nobody checked, for an unreadable installed version, or for a pinned mod.

- ⏹️ **Cancel works while the link is still being resolved.** Finding the right build and asking the site
  for an address ran with no connection to the Cancel button — and those are the calls that hang, on a Nexus
  or ModDB page that never answers. Pressing Cancel then did nothing until the request finished. One
  cancellation now covers the whole mod, taken before the first network call.

- 🔑 **The Nexus account is asked about before an update run, not after its first failure.** When updates
  come from Nexus and there is no session, the launcher says so BEFORE the first download, with a "Sign in
  to Nexus" button in the question itself. It used to start blind: the site opened its login form, the
  launcher said nothing about it, and the run sat frozen for a minute and a half. A premium key raises no
  question at all — Nexus hands such an account direct links, with no browser and no session involved.
- 🔓 **A Nexus login form now always appears.** The "show the browser" tick in Settings is about DOWNLOADS
  ("download by yourself, do not throw a browser at me"); signing in cannot happen without a window at all,
  because somebody has to type. The login form comes up whether the tick is set or not; everything else — a
  Cloudflare check, a manual click on a download button — still obeys it.
- 🛑 **Closing the download window means stop, and every following mod hears it.** Cancel used to stop the
  file in flight while the list carried on: with the window gone, the next steps were told "nobody
  cancelled". The next mod then met an invisible login form and hung there holding the lock — and with it
  the PLAY button, for a game that was doing nothing.

- 🛑 **"Cancel" now stops the whole update list, not just one download.** When the progress window went
  away — deleting the profile a run was downloading into, for instance — only the download in flight was
  cut, and the list walked on: no window, no progress bar, no Cancel. That is how 3.1 GB of a mod update
  came down into a profile that no longer existed, and why closing the launcher reported "the mod work did
  not stop within five seconds". One cause underneath all of it: a dismissed window went on answering "not
  cancelled" — not "cancelled", but "there is nothing to cancel", for ever. A dismissed window now means
  stop, and every step sees it at once.
- 🎮 **Our mods can now come from the Steam Workshop too.**
  With GitHub unreachable and the mirror silent, the launcher fetches the mod from the Workshop — provided
  Steam is already signed in (it will not ask you to sign in for this). And when the copy in use came from
  the Workshop, that is where updates are watched: until now our mods were only ever compared against our own
  releases, and such a copy went unwatched.

- 🔢 **The update badge no longer offers the version already installed.** Some mods under-report themselves in
  their own `SubModule.xml` — Improved Garrisons publishes 4.2.0.7 while the manifest still reads 4.2.0.5. The
  launcher records the real number at install and shows that on the row, but the on-disk pass and the Steam
  Workshop check compared against the manifest alone. A copy of the very same build therefore looked newer,
  and an "↑ 4.2.0.7" arrow appeared beside a version already reading 4.2.0.7. Both passes now compare against
  the number the launcher displays — as the online checks have always done.

- 🏷️ **An update row names the source the file will really come from.** A mod that lives only on our server
  has no repository, yet the row said "new release (GitHub)" purely because the "download from GitHub"
  setting was on. The label and the download now answer that question the same way.

- 🛠️ **Our own mods can be updated again.** Crash Doctor, RTS Camera Universal, the Russian TOR translation
  and Lore Hardcore never updated at all: the window said "one job at a time — mod updates are running" and
  then "could not update". The launcher was waiting for itself — the update run holds the one-job-at-a-time
  claim, and installing one of our mods, which is how that update is applied, asked for the same claim and
  was refused. Any such refusal is now written to the log too: it used to leave no trace at all, which made
  it look like the mod simply would not download.
- 📉 **An update to a version LOWER than the installed one is no longer offered.** Nexus can prove that your
  file was superseded, but the version there is free text and authors type the GAME's version into it. That
  put "SiegeAIFix v1.7.3 → 1.2.0" in the list. Such a number is no longer shown at all: the update stays,
  labelled "a newer file" — which is exactly what is known about it.
- 🎯 **A build recorded for another game version says so in the list.** When the reference knows the offered
  number is the build for 1.5 and your game is 1.4, the row says so. That used to surface only after the
  download, when the launcher read the files.
- ❗ **It is now clear why the same update keeps coming back.** Some authors forget to bump the version
  inside the mod: Improved Garrisons publishes 4.2.0.7 while its files still say 4.2.0.5 — and the launcher
  offered the update again and again, however many times you accepted. The downloaded release version is now
  recorded at install, the loop stops, and a "!" mark appears beside the number: clicking it says whose
  mistake this is and what to do about it.

- ⚡ **Updates already found appear the moment you switch to a profile.** Asking every source takes
  seconds; the launcher now shows what it found last time and corrects the list when the check finishes.
  The other profiles are checked in the background, out of the way of the game and of shader builds.
- 🔴 **Mods that never offered an update now do.** Some authors write a date where the version goes —
  "15.08.2026". The launcher read that as a version number, which came out higher than any real one, so
  such a mod was permanently "newer than anything there is".
- 📉 **A build known not to work is not fetched:** where that exact build is known not to run on your
  game, the launcher asks before downloading.
- 🔴 **ModDB updates were not found at all — now they are.**
- 🔴 **An update no longer breaks a mod pack or leaves the mod stored twice.**
- 🔴 **A mod that came with a pack is no longer offered an "update" to itself.**
- 🔢 **A Workshop update shows a version, not just a date.**
- 🔄 **An update where the author renamed the mod is no longer treated as a failure.**
- ⏹️ **"Cancel" works during installing too,** not only while downloading. And when the work is done the
  button says so — "Done".

### History and undo

- 🕘 **A "History" button in the mods window:** what the launcher did to this profile — what it installed,
  updated, removed, which translation went where, what failed and why.
- ↩️ **Undo with one button** beside every entry that can be undone. Entries that no longer apply are
  dimmed and labelled.

### Profiles and shaders

- 🗃️ **The launcher no longer keeps quiet about shaders it set aside.** When it first gives the game its
  own cache and finds a real one already in place, it cannot merge the two blind — so it moves what it found
  aside, into a `Shaders_backup_…` folder. Until now it never mentioned that folder again: the game compiled
  shaders from scratch while gigabytes of them sat beside the cache unexplained. It now says how much is
  there and from when, and offers to put them back into the profile's cache, delete the folder, or leave it
  for now. The answer is remembered, and the profile menu → “Shaders set aside” brings the question back.
- 🎯 **The shader items in the profile menu now clear the cache of the profile you clicked.** “Clear shader
  cache (for crashes)” and “build from scratch” worked on the folder shared by the whole game version — but
  since 21 August every profile has its own. The launcher said “deleted” while deleting something else. The
  question is now the same one the panel button asks: how many files, how many gigabytes, and which other
  profiles lose them when the cache is still shared.
- 🧯 **Another build's shaders inside YOUR mods: the launcher asks instead of deleting.** Some mods ship
  ready-made shaders built for a different build of the game — the engine reads them and dies a second and a
  half in, before the menu. In our own copies of mods the launcher clears such files itself; in mods you
  installed into the game by hand it now asks, naming the mod and the build the file was made for, and
  offers to move it out of the way by adding “.off” to the name. Nothing is deleted, and taking the suffix
  off puts it back.

- 🩹 **A mod carrying a shader cache from an older game build no longer kills the launch.** Some mods ship
  their shaders already compiled. When those were built for a different game build, the engine reads the
  header, writes "Shader cache version of the external module (…) is invalid" — and then faults in native code
  **before the main menu**, a second and a half in, with nothing catchable behind it: there is no .NET
  exception to see. The advice going round the mod pages is "clear the cache after installing this or it will
  not start". The launcher now does that itself: before a launch it compares each mod's cache version against
  the one YOUR game writes and removes the ones it cannot read. Only the cache goes — the engine builds its
  own again, and no mod file, setting or save is touched. When the game has nothing to compare against,
  nothing is touched at all.
- 🎨 **"Mods changed — rebuild your shaders" now appears only where shaders are built at all — in a profile
  with The Old Realms.** "Built" is remembered per game installation rather than per profile, so a profile of
  libraries, a camera and a voice pack inherited someone else's reproach and was offered an evening's work.
  Baking itself already refused for such a profile; the notice simply never asked the same question.
- 🎨 **And mods with no graphics stopped counting as graphics mods.** Any mod with
  an `AssetPackages` folder counted as a graphics mod — and RTS Camera keeps one for a 40 KB interface icon,
  Mod Configuration Menu for a 60 KB one. A profile of libraries, a camera and a voice pack was being asked
  to rebuild its shaders, which is an evening's work. What counts now is how much is in the folder, not that
  it exists: a real art mod runs to hundreds of megabytes. A mod shipping its own shaders still counts at any
  size.

- 🖱️ **A desktop shortcut — one profile, straight into the game.** The profile menu now has "Desktop
  shortcut": double-click it and the game starts with those mods, without opening the launcher. The launcher
  still starts, but stays minimised in the taskbar — while the game runs it is what keeps the mods attached
  and your Documents folder redirected to the profile's own, and it is what puts everything back afterwards.
  If it needs to ask something, its window appears by itself. After a normal exit it closes on its own;
  after a crash it stays and shows the diagnosis. Shaders are raised exactly once — when they have never been
  built for TOR: build, launch anyway, or cancel (with no cache the game compiles shaders at the loading
  screen for minutes and can die there). Choose to build and the launcher stays open afterwards, with the
  game one press away. A cache that already exists is left alone on this route: neither a changed mod set nor
  a changed quality is asked about. The same shortcut can be added to Steam as a non-Steam game, which puts
  the profile within reach of a gamepad.
- 🔁 **A shortcut clicked right after closing the launcher no longer goes nowhere.** A copy on its way out
  still holds the "a launcher is already running" handle for a moment, and its window can still be found —
  so a click at that moment handed the request to a dying process and quit silently: no game, no window, not
  a line in the log. The new copy now waits for that handle to be released and simply becomes the launcher
  when the old one has gone. And every such exit — "handed over to the running copy", "the running copy did
  not take the request" — is written to the log: that path used to leave no trace at all, which left "I
  clicked the shortcut and nothing happened" with nothing to explain it.
- 🖥️ **The game always runs on the powerful graphics card — there is no longer a question about it.** On a
  two-GPU laptop the launcher used to ask "switch to the discrete card?" There is nothing to ask: heavy setups
  die on the integrated chip with `create_texture_array`, and an hour of shader building is spent for nothing.
  The card is now switched automatically, the same on launch and on a build, and the launcher simply says in
  the status line which one it is.
- 🆕 **A new profile really is empty now.** It used to arrive with every mod lying in the game folder
  already switched on, so the launcher thought it had nothing to offer and said nothing about the
  recommended mods.
- 🩹 **Switching a mod off no longer removes it from the profile.** When the mods live in the game's own
  folder rather than in a profile or pack vault, the tick was the only thing keeping them in the profile:
  take it off and the row left the list altogether, with no way to put it back. It showed worst on "switch
  off what depends on it too" — turn Harmony off, say yes, and Harmony and every mod that asked for it
  disappeared at once. The files were untouched and so was the profile's own order, but the list was empty
  and there was nothing to be done about it. The profile now remembers its own set: a switched-off mod stays
  where it is with an empty tick and goes back on with one click. Taking a mod out of a profile still works —
  that is what "Remove from profile" is for.

- 🔴 **Each profile now has shaders of its own.** They used to be shared by every profile of one copy of
  the game — so deleting shaders in a copied profile wiped them for the original: it was the same folder.
  It was also wrong in principle: shaders are built for one screen resolution, one quality setting and one
  list of mods.
- 🧬 **Copying a profile asks whether to copy the shaders,** naming the size and the free space on the
  drive. Copy them and the new profile is ready to play; skip and it builds its own when they are needed.
  Not enough room — it says so before the copy starts.
- ⚠️ **Where shaders ARE still shared** (profiles made earlier), deleting them says which other profiles
  will lose theirs.
- 🧊 **Copying a profile no longer hangs.** The shader question appeared behind the copy window — it could
  be neither read nor answered, and the copy waited for an answer indefinitely.
- 🎛️ **No more shader questions out of nowhere.** The game leaves a small housekeeping file behind, and the
  launcher took that for a shader cache: on an empty profile it offered to copy 0.0 GB.

### Languages

- 🇫🇷 **French has arrived** — the interface, the crash window and its report, the pack editor and the
  whole manual.
- 🌐 **Mod translations are looked for in ANY launcher language,** not only our six: a language can be
  added as a file, and that file can also state what the language is called in the game.
- 🈯 **Crash details are in your language.**
- 🇹🇷 **On Turkish Windows a mod's name is no longer printed twice.** The line "the mod's name in your
  language" hides itself when it merely repeats the name already on screen — and that comparison followed
  Windows' own language rules. Under Turkish rules "i" and "I" are different letters, so "Improved
  Garrisons" did not match itself and the name stood on two lines in a row: on the mod card, in search, in
  the "add an installed mod" window and in the mod list. For Turkish players only, which is why it never
  came up.

### Journal

- 🛑 **"Go to page N" no longer leaves the reader empty.** If the first thing you pressed in the journal
  window was a mod's arrow or a line of the contents — rather than "Read" — the reader simply sat on "…".
  The launcher says two things to the page in a row: "open this issue" and "scroll to page nine", and while
  the page was still loading the second overwrote the first. The page woke up, was told to scroll, and had
  nothing to scroll. No error, no line in the log. Everything said now waits, in the order it was said.
- 📑 **The contents no longer belong to the previous issue.** They are read out of the PDF itself, and
  picking a different issue off the shelf did not re-read them: the previous issue's lines stayed on the tab,
  still clickable — and pressing one jumped into the NEW issue at the OLD issue's page. Switching issues now
  empties the tab, and it fills again when the reader opens what was picked.
- ⚠️ **The progress bar stops when the reader reports a failure.** The line underneath said the issue could
  not be opened while the bar above it went on running — "still working", the opposite of what was just said.
- 🧹 **An interrupted issue download no longer leaves four megabytes behind.** Pressing Cancel mid-download —
  or a connection that died — left a `….pdf.part` file in the journal folder that nothing read and nothing
  would ever have removed.
- 📖 **The launcher now carries a magazine about mods.** A new issue arrives as a card in the right-hand
  column of the main screen: cover, issue number, date and the mod it is built around. The ✕ puts the card
  away until the next issue, and Settings can switch it off for good — the journal stays in the menu. Nothing
  opens by itself.
- 📚 **An issue is read inside the launcher** — paging, zoom and printing — and it opens on the page you left
  it on. "Open outside" and "Save as…" are there too, and past issues sit in the journal window with their
  covers; you can fetch them all to read with no network.
- 🌍 **The issue comes in your language — and in no other.** Switch the launcher to English and the shelf
  and the card hold English issues; a Russian one is never handed over instead. With nothing published in
  your language there is simply no journal, and the launcher asks the mirror at once rather than waiting for
  its daily check — an edition can be added hours after the issue itself. Turkish, French and both Chinese
  will be met the same way when they come out.
- ⟳ **A refresh button in the journal window.** The list checks itself once a day; the button asks the
  mirror right now — for "an issue has just come out and I am already here". Whatever you were reading stays
  open.
- 🔗 **Mods written about in an issue open as launcher cards.** The magazine carries ordinary Nexus and
  Workshop links — they work on a phone like any other link — while in the launcher the same click opens the
  mod's card. Beside the list of issues there is a table of contents by mod: how many the issue covers, which
  page each is on, and a button straight to its card.
- 📦 **The PDF itself is only fetched when you press Read** — four megabytes do not go to people who never
  opened the journal. The list of issues and the covers are kilobytes and refresh quietly, once a day.

### Windows and looks
- 🟢 **Verdant skin: the Play button is green now** — in tune with the journal's "Read", a shade deeper,
  with a dark caption; brass on a green skin looked like a stranger's colour.

- 🔍 **A stopped game scan no longer loses what it found.** A full-drive scan found four games, Cancel was
  pressed — none was added, and the window ignored the button for another twenty seconds. Now every find
  is handed to the launcher the moment it is made, after the first new game the button reads **“Stop and
  add (N)”**, and on the press the window closes at once — the finds are in place, the drive walk winds
  down by itself in the background. While the card leaves, the button goes quiet (“Stopping…”) so a second
  press cannot break anything.
- 📏 **The profile banner is shorter — seven more mods on screen.** The title and subtitle took a quarter of
  the window; now exactly what they need. The ⚔ emblem moved to the background of the whole pane.
- 🖱️ **The scrollbar is wider and has a track:** 14 pixels instead of 10, a rounded thumb that brightens
  under the cursor and takes the skin's colour while dragged. In every window.
- 🌫️ **The mod list hints that there is more below:** while the list is longer than the screen and not at
  its end, the last rows fade into the ground colour; scroll to the end and it goes.

- 📖 **Manual: bold words in screenshot legends no longer turn into gold circles, and the five sections of
  the “Mod set in one line” page have their text.** The number-circle style caught any bold tag inside a
  legend entry; and the paragraphs under the RLink headings sat in a field the reader never drew. Turkish
  and both Chinese manuals also gained the sections they lacked against the Russian one (“Dependencies
  and conflicts”, “Launch arguments and cheats”, “What happens on the first run” and others); the manual
  check now compares section counts with Russian and rejects an unknown field.

- 🔤 **Captions on the main buttons (“Install”, “Read”, “Save”) are now the colour the skin gives them.**
  The caption took the page's general text colour rather than the one assigned to the button: no
  difference on a dark skin with a dark button, but on Verdant's light-green button a light caption could
  not be read. A light button now carries a dark caption — as every skin intended.
- 📐 **A narrow window no longer runs into itself.** The skin pills in the title bar ran into “Donate”,
  and the links at the bottom right were drawn over the magazine cover. When the skin row has no room it
  now folds into one pill, “Verdant ▾”, with a menu, and the links have a row of their own under the
  cards — the cards scroll, the links stay put.

- 🌲 **A new skin, “Verdant” — pine and moss.** A fourth pill in the title bar: a deep green ground, a
  light-green accent, a brass “Play” button, serif headings. The pack editor knows it as well.
- 🎨 **The “pack / personal / Workshop” tags and the coloured stripe beside a mod now recolour with the
  skin.** The colour used to be taken once when the row was first drawn, so after switching skins the mod
  rows stayed in the previous skin's colours: invisible on the dark skins, on a light one the “pack” tag
  vanished altogether.

- 🔢 **The "Our mods" and "Translations" buttons no longer open onto nothing.** Their counts came from a
  cache refreshed only when the profile changed, so after an install the button stayed lit over a profile
  with nothing left to offer. The count is recalculated after every install, and a button pressed in vain
  puts itself right.

- 📜 **The mod card's scroll bar no longer lies on the panel beside it.** It is drawn at the edge of the
  scrolling area, and that edge ran straight into the facts panel — it read as a line drawn over it. The bar
  has a gutter of its own now.

- 🔕 **The compatibility read-out no longer stands between you and the game.** A long list of record clashes
  opened by itself before every launch and frightened people for no reason. There is now a ⚠️ button beside
  Play and the read-out opens from it: amber when it is merely worth knowing, red when a mod will not be
  there when you play. A window still appears by itself when the game genuinely will not start.

- 🔍 **The mod list has a search box.** A profile built from a pack runs to thirty or forty rows, and
  scrolling for one mod is not finding it. The line above the list filters it in place: what is on screen is
  exactly what was asked for, and the ticks and the drag-ordering still work on it. It searches the name and
  the id alike — the list shows "RTS Camera Universal" while the folder, the crash report and every forum post
  say "RTSCameraUniversal". Spaces, hyphens and underscores are ignored on both sides.
- ⚡ **The launcher no longer freezes at start-up while it tidies up after itself.** The vaults of deleted
  profiles are whole copies of somebody's mods, and they were removed in the middle of the launch: the
  window stopped answering for three seconds on every start that found leftovers. That cleanup now happens
  on its own, away from the window.
- 🖱️ **The menu closes at once instead of after the action has finished.** "Find games" asked Windows about
  the drives before the menu had a chance to leave the screen, so it stayed painted over the search that had
  just opened — a sleeping disk answers in seconds.
- 🗂️ **A collapsed game stays collapsed.** The list of games is rebuilt after every mod installed, and
  collapsed rows sprang open again. Collapsing, selecting and scrolling are decisions about the window, and
  rebuilding the list no longer undoes them.
- 🎨 **"Shaders will be compiled again" is only asked where TOR is.** The question was about the whole game,
  so a profile without a single graphics mod was warned about a rebuild that has nothing to do with it.
- 🧾 **When mods disappear from a profile there is now something to explain it.** Every change to the list of
  enabled mods is written down, and the last few versions of the profiles file are kept — a case like that
  used to leave no trace at all.

- 🪟 **The pack gallery no longer opens after every update.** It appears on the first run — and after that
  only when the bundled packs actually change: one added, one rebuilt by its author, one removed. It used to
  be tied to the launcher's version, so it popped up on every update even when the packs were the same ones.
  The launcher tells them apart by the files' contents, not their dates: an update rewrites every file and
  moves every timestamp while the packs themselves stay put.

- 📖 **The changelog reads as paragraphs instead of a ragged ladder.** The "what's new" text arrives from a
  file wrapped to the file's width, and the window wrapped it again to its own — sentences broke mid-phrase
  and continuations sat at a different indent. Paragraphs are now glued back together and only the window
  decides where to wrap. The first bullet also stopped sitting left of the rest.
- 📏 **…and stands tight.** Half-screen holes gaped between the "what's new" items: the blank lines that
  separate the list in the file itself were drawn as they stood — and where already-seen items were taken
  out of the list, their blank lines stayed behind and stacked up. The items now follow one another, and a
  blank line is left only where it means something: around a section heading.
- 📜 **Long version notes no longer push the window off screen.** In the versions list a description was
  drawn whole, and a long one took the rows below it — and the buttons — out of sight. It scrolls now.

- 📐 **The "Will be launched" list is even.** A row was exactly as tall as the tallest badge in it, so a mod
  carrying a language tag or an update mark pushed its neighbours apart — and the gaps between mods came out
  in three different sizes. Every row is now one height, and the list is no longer for it: the pitch is the
  one a tagged row already took.

- 🧪 **A BETA VERSION mark has appeared in the title bar.** The 2.x line has not been released yet, so every
  copy of it is a pre-release. The mark sits beside the version number so that both you and whoever receives
  your report can see it: half an evening goes into hunting a bug that simply does not exist in the released
  build.
- 🖥️ **The launcher fits a small screen.** Every window is fitted to the monitor it opened on; on a
  1366×768 laptop at 125% Windows scaling the buttons along the bottom no longer fall off the edge.
- 🪟 **The window can be made narrow without anything falling apart.**
- 🎨 **Changing the theme changes the whole window, not part of it.** Every window in the launcher was gone
  through.
- ⚠️ **Windows that ask something have a tone:** a coloured edge and a mark — `!`, `⚠️` or `?`. "Cancel"
  is left only where there is something to cancel, and where the question is "install anyway?" the second
  button now says "Do not install".
- ✂️ **Long lines are no longer cut off mid-word.** Five places asked for their text to wrap while sitting
  in a panel that does not allow wrapping — so the line was simply clipped at the edge, with no ellipsis and
  no way to read the rest: the status line on the main screen ("switched off, because the game will not load
  them: …"), the verdict in the batch-review and pre-launch windows, a mod's description and its "will this
  run on your game" line in the pack install window, and the finding title on a mod card.
- 🔢 **The "Will launch" caption carries the number of mods.** On a short window that list was squeezed to a
  single line — six mods in the profile, one on screen, and it read as "only that one will launch". The list
  did scroll, but a hairline scrollbar is not an answer. The caption now says "Will launch · 6".
- ⏱️ **The ⚠️ mark on a mod row holds its tooltip as long as the marks beside it.** It was the only one left
  on Windows' own timing: its explanation — a whole sentence — vanished after five seconds while the marks
  either side of it stayed up for a minute.
- 🔎 **The "about this mod" button can be seen,** and the quiet refusal buttons no longer look like an
  invitation.
- 🧰 **The action bar on the main screen wraps to a second row** when there are many buttons.
- ✅ **The end of a pack install is impossible to miss.** After twenty minutes and several gigabytes, one
  line of small grey text used to change at the bottom and nothing else — it was not clear whether anything
  had installed. Now a banner appears: green "The pack is installed", or amber "installed, but not all of
  it" with the number of mods left to fetch by hand. The Install button steps aside and Close becomes Done.
- ⚙️ **Settings are split into categories:** a list on the left — General, Accounts, Mods and the reference,
  Downloads, Launcher updates, Data — and only what belongs to the chosen one on the right. It used to be a
  single long scrolling column.
- 🧪 **On a beta build, "receive beta versions" is ticked from the start.** The build was a beta while the
  setting pointed at the stable line, so the launcher offered a beta user an "update" to a lower number, or
  said nothing was new — and they never received another beta. A beta build now follows the beta line by
  default. **Your choice still wins:** touch the tick either way and the launcher stops deciding for you,
  including when you deliberately leave the beta line while running a beta build.
- 🧪 **You can take beta versions — and come back.** A tick in Settings → Launcher updates. Betas come out
  often and are the first to carry fixes as well as mistakes; the launcher says plainly how big the
  downloads are and that the point of a beta is your reports. **Turn it off at any time:** the launcher
  puts the stable version back, even though its number is lower than the beta — that is what going back
  looks like.
- ↩️ **Coming back from a beta is now safe.** Before a beta first touches your bookkeeping, the launcher puts
  a copy aside — profiles, packs, what was installed from where (under two hundred kilobytes all together).
  Return to the stable line and the copy goes back in place. Your mods are not touched at all: they have no
  format that could drift apart.
- 🔔 **The install report waits in its own profile instead of appearing over another.** Minimise a download,
  move to a different profile, and the summary window used to land there, describing mods you cannot see.
  The report now belongs to the profile it is about: that profile's row in the list gets a **✔ mark** with
  "the install has finished, open it", and the report opens when you go back. If you never left, nothing
  changes — the window appears as before.
- 💾 **Out of disk space is now said plainly.** The launcher used to read it as a connection failure and
  start the same multi-gigabyte mod again, onto the same full drive. It now says the drive is full and does
  not repeat a download that cannot end differently.
- ✋ **Cancel on an `nxm://` link really cancels.** Pressing Cancel was taken for a broken API, and the
  launcher started fetching the same file again. Nothing more is downloaded now.
- 🎚️ **Pick which build to install when a mod has several.** If the address does not say which file is
  wanted and the mod is published as several builds, the launcher no longer decides for you. A window lists
  them all — name, version, size, date — with the reference's verdict **for your game**: "built for your
  line", "built for another line, most likely will not load", or "the reference has not checked this build".
  The fitting one is preselected, but what you pick is what gets installed. One build, no window.
- 🎯 **The file named in the address wins.** With several files flagged "main", the first one the API
  happened to list was taken — and a mod page routinely keeps a build for the current game next to an old one
  for a previous branch. Hence "asked for 1.6, got 1.1". The file id in the address is now the law; "the
  newest" survives only where no id was given at all.
- 🖥️ **A Nexus link no longer drops the launcher out of full screen.** Windows restores a window "to its
  previous size" from maximised as well as from minimised — only the minimised case is touched now. It used
  to stick, too: window bounds are saved on exit, so the next start came up un-maximised as well.
- 📶 **A download from a Nexus link is as visible as any other.** It used to be one line of text at the
  bottom — no bar, no speed, no size, no Cancel, and the download could not be stopped at all. It is the
  usual window now. And when the launcher is already busy, the link is refused politely instead of taking
  over somebody else's window.
- ❓ **If the mod from the link is already installed, you are asked.** Files used to be unpacked over the top
  in silence, including replacing a version with an earlier one. The installed version is now named before
  anything is downloaded.
- 🧾 **The record for a mod names the file that was actually downloaded.** When a different file was installed
  than the address named — a stale address, or a build you chose yourself — the database kept the id from the
  address, and the next update check compared this copy against the wrong file.
- 🔗 **A stale link in the reference no longer sends you to a web page.** The reference names not just a mod
  but a specific file on Nexus. When that file is gone, the launcher used to substitute a placeholder with
  the same id, ask for a download link for it, get nothing — and announce that as **a free account**, even on
  a paid one. That is how translations ended up opening pages with a working premium key. Now, when the named
  file is gone, the launcher asks for the mod's main file and downloads it directly.
- 🔎 **When Nexus refuses, the log says what it actually answered** — a 404, a refused key, an exhausted
  hourly quota. All of those used to look identical: "no file", with the reason left to guesswork.
- 🗝️ **The launcher now says whether your Nexus key is a paid one.** It used to answer "key saved and checked"
  and nothing more — so somebody with a free key had no idea why a page still opened asking them to sign in.
  Said plainly now: a paid account downloads directly; with a free one the key is still used — it is how the
  right file is found — but Nexus hands direct links to paid accounts only, so the download itself needs a
  sign-in in the browser window. That is Nexus' rule, not the launcher's.
- 🈯 **The profile's History no longer slips into English.** Some entries carried a note written for the log —
  in English — and that same note was shown in the History window. The English diagnostic stays in the file
  where it is read, and the screen shows your language. Error messages from Windows cannot be translated, so
  those read "did not work — the log has the details" instead.
- 🎯 **The game can no longer load the wrong copy of a mod.** If you once dropped a mod into the game folder
  by hand and later installed the same mod through the launcher, `Modules\` ended up holding **two folders
  declaring one module id**, under different names. The launcher hands the game a list of ids and the game
  picks the folder itself — so it could load the old copy while the launcher showed the new version. That is
  how a player's Crash Doctor read as updated in the launcher and ran old in the game. The stranger with the
  same id is now moved out of the way before launch and put back afterwards — nothing is deleted, it is yours.
- 🎯 **…and a folder moved aside really stops being a mod.** It used to be merely renamed, but the game does
  not look at folder names — it reads inside, and the displaced copy went on declaring the same id. Its
  module manifest is now hidden for the duration of the run and restored with the name.
- 🔑 **The Nexus key is now used everywhere something is downloaded.** Updating a mod never asked for it —
  **not once** — and opened a page in the browser instead, while already holding the game domain, the mod id
  and the file id, which is exactly what is needed. The "Nexus goes through the browser" rule dated from when
  the key was only used to CHECK for updates, and it outlived its reason. The key is asked first now: a
  premium account gets the file straight from seven mirrors with a progress bar, and the browser stays the
  answer where nothing else works — Nexus will not hand a free account a direct link. Same for a mod added
  by pasting its address.
- 🌍 **The translation you picked is the one that gets installed.** The launcher took the first address it
  had: if the reference held a page of its own for that mod, your chosen translation was discarded — and the
  Nexus address went with it, which is why the key was skipped and a page opened. Your choice is the address
  now, and it outranks everything else.
- 🔧 **A dependency that is present but switched off now gets switched on.** The launcher counted such a need
  as met — the mod is right there — but the game only loads what is enabled. So Crash Doctor and RTS Camera
  installed, Harmony stayed off, and the pre-launch check then disabled the mod itself over the very library
  the launcher had just decided it had. No second copy is downloaded: the one already there is switched on.
  And the pre-launch check can finally see our own mods — it used to ask only the reference, which knows
  nothing about Crash Doctor or RTS Camera.
- ⏳ **And it no longer freezes after UPDATING mods either.** A different culprit here, and a more galling
  one: the "Build shaders" button appears based on "has the mod set changed since the last bake", and working
  that out re-read **every** module of the game and looked inside five folders of each. The property is bound
  in the window, so it is re-read on every notification — and right after an update the module cache has just
  been dropped, making each of those reads a full walk of the mod tree on the drawing thread. The answer is
  remembered now, and worked out again only when the mods on disk could have changed. Updating several of our
  own mods no longer rebuilds the list once per mod either.
- ⏳ **The launcher no longer freezes after installing mods.** The window closed and nothing could be clicked
  for five to ten seconds. Three things were to blame, all of them done on the thread that draws the window:
  recording a mod's contents walked every one of its files (tens of thousands for an art overhaul), the
  profile tree was rebuilt from scratch **after every single mod** — seventeen mods, seventeen rebuilds — and
  then the folder watcher ordered one more, because it did not know the launcher itself had done the writing.
  Now the file walk happens out of the way, the tree is rebuilt once for the whole install, and the watcher
  keeps quiet while the work is ours. Undoing an install no longer rebuilds the tree per mod removed either.
- 🚫 **The Install button on a mod's card appears only where installing is the point.** It is one card on
  every screen, and its buttons travelled into the update list, the translations list and your own profile's
  mod list — so mid-update you could pile on more mods and start a second download on top of the running one.
  A card opened from the reference search offers to install; everywhere else it explains, and nothing more.
- 🔢 **Version numbers are no longer trimmed anywhere.** The button offered "Beta 2.1.0" while 2.1.0.5 was
  what arrived — the fourth number is the build counter, and without it two different builds looked like the
  same version: on the button, in the confirmation window, and in the settings line that says which line you
  are on. Now exactly as many numbers as there are: four for a beta, three for a stable release — padding
  that one with a zero would invent a number.
- 🌐 **The update button changes language with everything else.** It was built once and then held as a
  finished string, so after a language switch it kept the old one until the next start.
- ☑️ **The beta tick cannot be toggled twice in a row.** While the launcher asks for your agreement and looks
  at what the chosen line holds, the tick is unavailable. It used to stay live, and a second click silently
  undid the first: the choice was overwritten, and after a restart the wanted and installed lines agreed
  again — so the button back vanished, as if there were no way back.
- ⚡ **The update button opens its window at once.** Pressing the "Update" pill used to fetch the list of
  changes first and draw the window afterwards — where GitHub is unreachable that was twenty to forty seconds
  in which nothing happened at all. The list is now read ahead of time, while the pill is blinking, and the
  window opens instantly; if the text is still on its way it is added to the window already on screen.
- 🎛️ **The beta tick takes effect at once.** It used to be merely written down, and the launcher only noticed
  it on the next start — which looked like the tick doing nothing. Going back was the worst of it: you
  cleared the tick and no stable build arrived. Now the launcher looks at the chosen line straight away and
  shows the banner — looks, does not download.
- 🖼️ **Pictures show up on any Windows.** Some players saw none at all — no mod artwork, no screenshots in
  the card, no pack banners, not even the Steam sign-in code. The internet had nothing to do with it: the
  pictures downloaded and sat in the cache (1 666 files, 224 MB, on one machine) and Windows itself refused
  to open them. That happens on builds shipped without the system's codecs — N/KN, LTSC, "lite" builds — and
  on Windows 10, which does not understand WebP: which is exactly what Nexus serves, from addresses ending
  in `.png`. The launcher now decodes pictures itself instead of relying on the system.

### Crash diagnosis

- ⏱️ **The launcher says a crash happened at once, not a minute later.** A native fault does not kill the
  process immediately: Windows holds it while the dump is written, and a dump can run to hundreds of
  megabytes. The launcher spent all of that waiting on the process and saying "the game is running" — 45
  seconds of silence for a game that died in its second second. It now notices the crash folder the game
  creates straight away and says so: "crashed — Windows is writing a dump, the report opens as soon as it is
  done". The report itself is still built after the process is really gone; there is no data before that.
- 🩺 **Two more campaign crashes are now named.** The first happens while creating a new game: a minor
  faction refers to a character that does not exist in its files, and the game dies before the map. The
  second happens while loading a campaign: a mod's equipment file was written for an older version of the
  game, and it trips over an equipment flag it does not know. Both were worked out from real player reports
  and checked against the game's own files on 1.2.10, 1.3.15, 1.4.7, 1.4.8 and 1.5.1 — in each case the
  launcher names the mod behind it and what to do about it.

### Tidiness and reliability
- 🗂️ **The store picker grew up:** with no language chosen yet it offers the language first — and shows
  the rest in it; the picked store has **“Delete everything in the selected one”** with a progress bar (one
  question naming the size — and 180 GB go); the settings' Data section gained a **“Data store”** block
  with “Choose a store…” — attach another, move it here or delete it, the launcher restarts itself. The
  block shows only when there is something to choose from; on a switch the current data goes nowhere — it
  is set aside next to the launcher and stays in the list.

- 📦 **Moved the launcher folder — it asks which data to attach.** The catalog of a copy that lived in
  OneDrive sits in `%LOCALAPPDATA%\RickLauncher\Catalog` behind a link; move the folder and the link does
  not come along, so the launcher opened empty — the profiles intact but seemingly gone (owner,
  11.09.2026). Now, on the first start from a new folder with no data of its own while other copies'
  stores exist on the machine, the launcher lists them — the folder they belonged to, profiles, games, last
  run, size — and offers **“Attach”** (instant, the data stays where it is) or **“Move here”** (into the
  launcher's folder, on this disk, with a progress bar). The choice is remembered — from then on the
  launcher always works with that data. Nothing is deleted: the empty first-start catalog is set aside.


- 🛡️ **The whole launcher no longer closes because one window slipped.** Ten places ran without a net:
  opening the contact window and sending a message, preparing a backup, showing the Steam sign-in code, two
  timers in the built-in browser, copying a mod's name and id, and the version-mismatch note. Anything small
  there — the clipboard held open by another program, a dropped connection, a window closed while a request
  was in flight — went to the global handler and took the launcher with it. It is a line in the log now, and
  the window stays where it was.

- 📝 **The log now shows what YOU did, not only what the launcher did.** Lines marked `USER`: which
  question was asked and which button was pressed, mods installed and updated, ticked on and off, removed
  from a profile or deleted from disk, shader caches deleted, the game launched. Without it a diagnosis hit
  a wall: five mod folders were gone, the log held nothing, and "the launcher lost four gigabytes" could not
  be told from "somebody deleted them" until the owner was asked.
- 🧹 **The log no longer grows without end:** a week is kept, and no more than 10 MB for the whole folder.
  The oldest go first; today's file is never removed.

- 🗄️ **The backup window's ✕ stops the work instead of hiding it.** It used to close the window while the
  archive — or the RESTORE, which writes over your data — carried on in the background: no bar, no messages
  and no way left to stop it. ✕ and Alt+F4 now mean what the Cancel button means.

- 🔒 **While the launcher is touching mods, the game cannot be started.** You could press Play in the middle
  of a write — and get "these mods cannot load", then find half the mods missing in the mods window. They had
  not gone anywhere: the list was built while a mod's folder was renamed for the update, and they came back
  by themselves once the window was closed. Play now becomes the download indicator for the duration and the
  mod buttons grey out. It covers every profile of the same pack — they launch out of the same folders.
- 🎯 **The `!` and `zz` prefixes in a mod's name work again.** Plenty of mods declare no load order at all —
  instead the author puts `!` at the front to load above everything, or `zz` to load below. The launcher did
  not read that and dropped such mods in the middle.
- 📚 **It is now visible when two enabled mods carry different builds of one library.** The game loads only
  one of them and the load order decides which; that now reaches the log instead of staying a mystery.

- 🧩 **A pack no longer goes missing from the records while sitting on the disk.** Deleting a profile
  dropped the registry record for its pack whenever that pack's vault was *listed* for deletion — whether
  the deletion actually worked was never checked. The folder would not go (a file held by the game, the
  launcher, OneDrive), the mods stayed, and the one line pointing at them disappeared. The profile then
  launched without its pack layer: "Vanilla+ 4" had 27 mods switched on, 17 of them the pack's, and ten
  reached the game. The launcher explained it as "ButterLib needs Harmony, which is not enabled" — about a
  Harmony that was switched on and present. The record is now dropped only when the folder is really gone,
  and a failed deletion is written to the log: only success used to be, so a surviving vault left no trace.
- 🔧 **And a lost record repairs itself.** When a profile names a pack the registry has forgotten but whose
  vault is still on disk, the launcher rebuilds the record from the folders, reading each module's id and
  version from its `SubModule.xml`. Nothing is downloaded: the files are already there — only the pointer
  to them was missing.
- 🗑️ **Deleting a profile with its mods now shows that it is happening.** "Delete profile and mods" on
  54 GB takes minutes, and all of it ran on the thread that draws the window: you confirmed, and the launcher
  simply stopped answering with nothing on screen. The profile itself now disappears from the list at once —
  that part is bookkeeping and is instant — while the folders go in the background behind a progress window:
  the bar counts down the very gigabytes the question quoted, and the line under it names the mod being
  removed right now.
- 📡 **A dropped connection no longer looks like a frozen launcher.** When no byte arrives for 45 seconds the
  download stops and says so instead of sitting on a stalled bar — and it resumes where it left off. Only
  two downloads out of five did this before; the rule is now the same for all of them: direct links, the
  mirror, the multi-connection download, old Workshop mods and files the built-in browser fetches.

- 🔴 **The launcher no longer closes when an action fails.** Thirteen buttons — undoing an install,
  installing a mod from its card, removing a translation, paging through screenshots, moving your data —
  were wired so that any hiccup (a file in use, a dropped connection, a disk that stops answering) closed
  the whole launcher. Now it is a line in the log and a message, and the window stays where it was.
- 📦 **A big mod unpacks faster.** The unpacking bar re-measured the whole folder four times a second; on a
  19 GB mod that is tens of thousands of reads on the very disk being unpacked to. The measurement now
  paces itself — same bar, quicker unpack.
- ⚡ **Mods from Nexus download noticeably faster.** The site shapes each connection separately, and it hands
  a premium key seven addresses for one and the same file — the shared CDN and six mirrors. The launcher now
  uses all of them and hands out the pieces by speed: a fast mirror simply takes more, so the file never
  waits for the slowest one. A dead address on the list no longer costs the download — the piece moves to the
  next one, and if the first address is silent too, a second is tried instead of giving up on fast
  downloading altogether.
- 🛡️ **And it checks that what arrived is what was asked for.** Nexus publishes no checksums, so a piece is
  accepted only when the server itself says which bytes these are and which size of file they come from; the
  assembled zip is then opened as a test, and if it will not read, it is fetched again over a single
  connection. A file of the right size with a spoiled middle is the one failure of assembling from several
  sources, and it no longer passes quietly.
- 🗃️ **A pack can no longer install an old archive instead of the new one.** When a pack names neither a
  checksum nor a version for a mod there is nothing to tell two archives apart, and the first one ever
  downloaded was installed for good, however many times the author re-published it. Such a mod is now
  fetched afresh.
- 🧹 **The launcher clears up after itself.** Downloaded archives used to stay on disk after installing,
  for good: a tester's folder had built up **16 gigabytes** — a hundred and twenty-five copies of mods
  that were long since installed. The archive is now removed as soon as the mod is in, and leftovers from
  interrupted installs are swept at start-up, in the background. Unpacked "this is not a mod" no longer
  piles up either: one folder per archive instead of a fresh copy per attempt.
- 🔴 **A damaged settings file no longer wipes your profiles:** it is set aside as a copy, the launcher
  starts on defaults and says so.
- 🔴 **Installing a pack onto another drive can no longer lose files.**
- 🛟 **The launcher warns when its own data sits inside OneDrive and offers to move it out** — whole mod
  folders have gone missing from there.
- 🗄️ **If the mod reference will not open, the launcher offers to delete it** so it can be fetched again
  from the settings. A damaged file used to sit there quietly while the launcher ran without cards,
  clashes or translations.
- 🔁 **A second launcher no longer just hangs:** the window already open is raised, and if there is none,
  you are offered to close the stuck process.
- 🔗 **Housekeeping links in the game folder no longer vanish silently.**
- 🧹 **If shaders could not be deleted, it says so.**
- 🇹🇷 **Fixed for systems set to Turkish.**

### Installing packs
- 🔑 **With a premium Nexus key a pack install no longer shows a sign-in window.** The launcher demanded a
  browser sign-in even with a paid key in Settings: it would only ask the API about a mod whose exact file
  the pack names, and went straight to the page for everything else. Now it asks the mod page for its main
  file, and follows the author's chain when a file has been withdrawn — no sign-in needed at all. A FREE key,
  on the other hand, no longer counts as "signed in": Nexus hands it no direct links, and you are told so
  before the install starts.
- 🚪 **Close the Nexus sign-in window and the install asks what you meant.** Closing it used to read as "that
  one mod failed", and the run carried on downloading in silence. The install window now comes forward and
  asks: "Cancel the install" or "Sign in to Nexus" — and carries on from the same mod if you sign in.
- 🧩 **A translation is laid inside its mod instead of being refused.** A translation that arrives as a set of
  files looked for its mod only in the list on screen — and during a run that list is not rebuilt yet, so a
  mod installed twelve seconds earlier was not in it. The review screen then said the address "holds no mod".
  The host mod is now looked for on disk as well.
- 🔢 **A pack installs in the author's order.** The game's own optional parts (Birth & Death, War Sails, Fast
  Mode) were left out of the profile's order and ended up at the very bottom of the list — under the mods
  that patch them. They keep their place now. And a translation installed after the pack lands directly
  behind the mod it translates, which is the only place its texts win.

- 🏷️ **The same pack on another game no longer gets a "2" in its name.** Profiles are grouped under the game
  they belong to, so identical names under different games are already told apart. A second copy under the
  SAME game is still numbered.

- 🎮 **The game's own modules no longer pass for broken mods.** `Native` declares PlayStation and Xbox
  libraries that a PC copy of the game does not ship and never did. The "a mod is installed only in part"
  window took that for damage and appeared before every launch, and its repair button led to an empty install
  window with no mod in it at all: the launcher cannot reinstall the game, and there is nothing to reinstall.
  The game's own modules and official DLC are now left out of this check entirely.
- 🔘 **The repair button appears only when there is something to repair.** It is offered only for mods the
  pack actually carries, and only where downloading again could change anything: a mod that put its library
  in another platform folder will arrive exactly the same, and asking about it leads nowhere.
- ⚡ **Repairing one mod no longer checks the whole pack's availability.** The launcher asked Nexus about
  every pinned mod before starting — one request per page, twenty-seven waits to repair one. It now asks
  about the mod it is repairing.
- 🧾 **Repairing one mod no longer erases the record of the others.** A pack's record is the list of folders
  it owns, and a profile reads exactly that. The installer always rewrote the list with what it had just
  installed — which for a one-mod repair would say "this pack has one module", and the other twenty would drop
  out of the profile while their folders sat on disk. A subset repair now merges into the old list and does
  not claim the pack's version: one mod is no reason to say the whole pack is up to date. When there is no
  record at all (a copy from an older install), the launcher does not invent one — the mod is installed, and a
  full reinstall rebuilds the bookkeeping.
- 🔁 **A gutted copy of a mod is no longer spread from profile to profile.** When a mod's folder was once
  overwritten by its own translation, what stays is the `SubModule.xml` — byte for byte the mod's own — and
  what goes is everything that file describes: no `bin\`, no `GUI\`, no `ModuleData\`. Every check read the
  manifest and agreed it was the mod, so a pack install took the "copy on disk" instead of downloading and
  carried the wreckage onward — and the game met the loading screen with "Cannot find: …\CharacterReload.dll",
  every single start. A copy now counts only if it carries the libraries it declares. If it does not, the mod
  is downloaded again and the log says exactly what was missing. A mod with no libraries at all (textures,
  scenes, a language pack) is still whole: it never had a `bin\`.
- ⏳ **The shader-cache check shows its progress.** It walks every mod's folder, and on a set with tens of
  gigabytes of shaders that is a noticeable pause. It now reads "Checking the mods' shader caches — 12 of 37"
  with a bar on the taskbar button, instead of a window saying nothing.
- 📅 **"The last install did not finish" no longer shows an empty "(from )".** The install date was stamped
  only after a successful return, and Cancel left before it — so the window that by construction appears
  ONLY after an unfinished attempt never once had a date to show. The stamp is now written on every outcome,
  cancellation and failure included. And when there genuinely is no date — a record left by an older build —
  the window says a sentence without one instead of drawing an empty bracket.
- 🧹 **"Clear and install cleanly" on the unfinished-install window.** Carrying on from what is there is right
  when the files are sound and useless when the files are the reason the last attempt died: a half-written
  archive, a mod that unpacked badly, a pack the author has re-uploaded since. The third button removes the
  pack's vault, its record and **all of its downloaded archives**, the browser's scratch folder included.
  Nobody else's downloads are touched — the cache is shared. ⚠️ Mods of the same version sitting in other
  profiles are still taken from the disk; only what does not match by version is fetched, so a clean install
  can finish surprisingly fast.
- 🔑 **The pack window says whether you have a Nexus API key.** A bright line at the top: no key — "add the
  free one, packs install far more reliably with it"; a key Nexus refuses — "until it is replaced the
  launcher works as if there were none". The second is worse than the first: everything inside believes the
  key works.
- 📊 **A mod's row shows the percentage and the speed again.** An 8 GB file was downloading under a plain
  "Downloading…" with no numbers at all — the bar still, no speed — which reads as a hang at the exact moment
  everything is working (2 GB of 8.8 were already on the disk). The row was matched by object identity, and
  the window's list and the installer's are not always the same objects: no match, every progress report
  thrown away. It now matches by module id as well. The embedded-browser path also stopped calling itself
  "finding the source" — it is an ordinary download, and now says so.
- 🔁 **A second pass over the failed mods, at the end of the same install.** A run learns as it goes: Nexus'
  game number arrives with the first mod that downloads, and a mod that needed it earlier never had a chance.
  Those are asked again at the end — no second run of the install.
- ⚡ **A mod with nothing left to try is given up in seconds, not a minute.** Without the game number both the
  Nexus widget and clicking the page are pointless, yet the launcher clicked forty times anyway. It now stops
  at once and moves on; the second pass comes back to it.

- 🙈 **The browser no longer appears unless you ticked the box in Settings.** It used to surface on its own —
  a Nexus sign-in, a Cloudflare check, automation out of moves — in the middle of an install nobody is
  watching. The gate now sits at the door itself rather than at each of the nine places that called for the
  window, so a tenth added later cannot reopen the hole. The cost, stated plainly: a sign-in that genuinely
  needs a human will not get one and the mod is reported as unavailable — signing in lives in Settings, where
  it is your decision rather than an ambush.
- 🔢 **The launcher now remembers Nexus' game number, and works it out when it doesn't.** A signed link is
  issued for a file-and-game pair; the game number comes from the page's markup, and an archived file whose
  mod page is gone has none. It lived on the browser object — and a fresh browser is built for every mod, so
  what one learned died with it; in a continued install the early mods come off the disk, so the launcher
  reached the archived one having learned nothing. The number now lives in a file beside the browser's data,
  and when even that is empty the page reads it off the game's own front page in one request, without leaving
  the file behind.

- ⏱️ **"Finding the source" can no longer spin for ever.** On a page with no download control at all — which
  is what an archived file looks like once its mod page is gone — the driver clicked at nothing every one and
  a half seconds and never stopped: every escape hatch hung off a counter that only moves when a button *was*
  found and led nowhere. The search now has a budget of its own, about a minute, after which the browser
  window is handed to you for a single click — the signed link it produces is still captured automatically.
- 🔢 **The game number is no longer lost on pages that do not carry it.** Nexus signs a download link for a
  file-and-game pair, and the launcher read the game number only from the page's markup — an archived page
  has none, so the request went out with it blank. That number is the same for the whole pack, and mods
  fetched minutes earlier in the same run already reported it, so it is now remembered for the session and
  used when a page has none of its own.

- 🔑 **Settings now has a "Clear the key" button beside the Nexus API key.** The key changes what the
  launcher can do at all: with it Nexus answers questions about files and hands premium accounts direct
  links; without it everything goes through the browser. Asking "how does this behave without a key" used to
  mean guessing what was in a masked box and emptying it. The button shows only when there is a key to clear.
  It does not touch the Nexus sign-in — that is a separate button and a separate thing.

- ▶️ **An unfinished pack install can be carried on instead of started over.** When a previous attempt
  stopped, the launcher saw its vault on the disk and answered "this pack is already installed" — about the
  player's own interrupted run, which has no profile at all. Both answers that question offered threw the
  work away: "replace" deleted the vault, "another copy" started an empty one. "Installed" now means "there
  is a profile", and an unfinished run offers **"Carry on installing"**: mods already on disk that match by
  version are taken from there, only the rest is fetched, and nothing is deleted.

- 🔎 **A pack checks what is still on Nexus BEFORE the first download.** An author can delete a file or
  archive it at any time, and a pack names the exact file. That used to surface in the middle of an install,
  with gigabytes already fetched and everything stopped. The launcher now asks Nexus about every pinned file
  up front and puts one question on screen: these mods are gone — install the pack without them? The question is asked ONLY about deleted files. One the author archived downloads like any other — through
  the slow button on a free account, straight through on premium — so there is nothing to raise an alarm
  about: that stays a line in the log.
  ⚠️ The check needs a key: Nexus answers no such question without one, so nothing changes without it — a
  mod that cannot be fetched is still caught as the install reaches it.

- 📖 **Mod descriptions in the install window are folded, and the mod card is one click away.** A pack of
  a dozen mods with three-paragraph descriptions fitted on no screen: reaching the next mod meant
  scrolling past somebody else's prose. A description now takes two lines, and a click on it unfolds and
  folds it back. Beside the Nexus and ModDB links there is now a "Mod card" button — it opens the mod's
  page inside the launcher, and only for mods the reference actually knows something about.
- 🤫 **A pack install no longer stops to ask.** Every mod that read as built for another build of the game,
  and every mod nothing could fetch, used to raise its own modal window mid-install — with the run stopped
  until somebody came back to the keyboard. The launcher now installs everything it can and shows one list at
  the end: which mod may not start, which was skipped and what relied on it. The one question left is about a
  suspicious archive — that is safety, and it is not a decision to make on your behalf.

- 🧩 **A pack now enables only the mods it ships.** A pack's load order is written out from the profile it was
  built in, and a mod removed from the pack afterwards stayed in that order: "europe-1100_1.3.15" and
  "vanilla-plus_1.3.15" still named ArenaOverhaul and TournamentsXPanded, which neither pack contains. The
  installer enables everything the order names — so on a machine that merely had those mods on disk, the pack
  switched them on, and the profile became a mixture of the pack and whatever else was lying around. Only
  what the pack actually installs is enabled now (plus the game itself and its DLCs); anything else is
  reported in the log. The pack editor no longer leaves a removed mod in the load order.

- 🎮 **"This pack is already installed" is no longer said about a pack for another build of the game.** One
  author publishes "Vanilla+" for 1.2, 1.3 and 1.4 — one title, a different file each time. The launcher also
  matched on the title (needed when an author re-exports a pack under a new id), so installing the 1.3 pack
  was met with "you already have this one" when what was there was the 1.2 pack. The install record now keeps
  which build of the game the pack was made for, and a title match only counts when the branch is the same.
  A pack profile belonging to another build is likewise no longer mistaken for a lost profile of this one.

- 🧮 **The "N of M will not run" line no longer counts blind.** The pack install window said "1 mod of 0 will
  not run" and marked no row at all — the count ran before the mod list existed, so the mod at fault stayed
  invisible. The list is now built first, the offending row is marked, and the number comes from the check
  itself. And one mod is spoken of in the singular.

- 🎯 **"Will not run" is now said only about the file the pack actually carries.** The reference keeps one
  verdict per mod per branch of the game and remembers which build of the mod it was measured on. A pack
  pinning v1.2.12.10 was handed a verdict taken from v1.3.0 — so the window said "this mod simply will not be
  in the game" about a file nobody had checked. Such a verdict now shows on the mod's row as "version 1.3.0 would not
  run on this game — yours is a different one, and nobody checked it", and is left out of the count.

- ⏳ **A mod's bar now crawls on steps with no size to show** — checking, clearing Windows' download mark,
  copying into the vault. It used to vanish on those, and a row with one line of still text read as a row
  that had finished.

- 🛟 **Deleting a profile can no longer take a neighbour's mods with it.** A pack vault is shared: it goes
  only when no other profile on the same game still uses that pack. The install path was compared as text,
  so `C:/Games/Bannerlord` and `C:\Games\Bannerlord` counted as two different places — the remaining
  profile went unseen and its mods were deleted along with the one being removed. Paths are now compared as
  paths.

- 🇬🇧 **English is first in the first-run language list.** The interface is English until that question
  is answered anyway, and for somebody whose own language is not on the list English is the likeliest
  fallback. The guess from Windows comes next, as a hint.
- 🌍 **A pack is no longer shown in a language you do not read.** With no description in your language
  the English one is used, and only if that is missing too does the launcher fall back to whatever
  language the author wrote in. It used to reach for the author's language first, so a French player
  read a Russian summary with the English one sitting in the same file.

- 🎯 **The launcher now checks a pack against your game mod by mod.** It used to compare one line: the pack
  is built for 1.4, the game is 1.4.7, fine. That is a coarse answer — "built for 1.4" says nothing about
  whether the eleventh mod in it runs, and it is that mod the evening is lost to. Every mod is now checked
  separately, and a line above the list says it plainly: "2 of 14 mods will not run on 1.4.7". You can still
  install — those mods simply will not be in the game.
- 🎮 **With several copies of the game installed, the right one is picked for you** — the one the pack fares
  best on, not the first in the list.
- 🛒 **Where a mod is fetched from is the launcher's decision.** First whatever needs no account at all
  (GitHub, a direct link), then the platform you are already signed into — Steam or Nexus.
- 🔁 **A dead link no longer breaks the install.** If an address does not answer, the next one the pack
  carries is used. One file deleted by its author used to stop the install on that mod.
- ❓ **When a mod cannot be fetched from anywhere, the question is asked properly.** The launcher tells you
  the thing that matters — what skipping costs: it names the mods in the pack that are built on it, or says
  outright that nothing depends on it. If the mod lives on a platform you are not signed into, it names that
  too. You can open the mod page straight from the window and look for yourself before choosing between
  skipping it and stopping the install.

### Pack editor and manual

- 🪄 **A pack made from your profile opens already filled in.** From the reference come the mod's name and
  author, its description **in every language the launcher speaks**, every proven page as a download
  address, a translation for each language (the most-used one where there are several) and the mod's
  artwork. Only blank fields are filled: nothing you wrote is touched, on the first open or any later one.
- 🔗 **A mod can have several addresses.** The same mod often lives on Nexus, in the Steam Workshop and on
  GitHub at once. A pack used to carry one — and if the player had no account there, or the link had gone
  stale, the install stopped at that mod. A pack now carries every known address and the launcher picks at
  install time: first whatever needs no account at all, then whatever the player is already signed into.
- 🚫 **Mods that are switched off, and parts of the game itself, do not go into a pack.** An enabled DLC
  such as War Sails used to be listed as a mod to download — and there is nowhere to download it from. It
  is now only named in the recommended load order, so the player's profile turns it on too.
- 🧱 **Empty required fields are outlined in red,** and the reference fills in for the author everything it
  knows itself.
- 🔗 **An address can be added by hand, by pasting a link.** Copy the mod's address out of your browser and
  press "Add address" — the editor works out whether it is Nexus, the Steam Workshop, GitHub or a direct
  link to an archive.
- 🩺 **A "Check the links" button.** It walks every address in the pack and says which ones no longer
  answer: the mod gets a red line in the list and the address gets a mark beside it. Nothing is downloaded
  and it takes seconds. It proves the page is alive; whether the file needs an account is a separate
  question.
- 🛠️ **The pack editor starts from the launcher's menu.** There used to be one way in: make a pack out of a
  profile and answer "open it". Coming back to yesterday's work meant hunting for the .exe beside the
  launcher.
- 🗂️ **"Open project…" lists the packs you worked on last** — eight of them, newest first, with the ordinary
  file picker as the first entry. A pack you moved or deleted simply drops off the list.
- 📖 **A new "Mod reference" chapter in the manual** — the card, the search, what is known about
  compatibility.
- 🇫🇷 **The manual is translated into French in full** — for the launcher and for the pack editor,
  screenshots included: a French reader now sees French windows rather than English ones.
