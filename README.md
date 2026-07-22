# RickLauncher

A launcher for **Mount & Blade II: Bannerlord** — one place to run several game versions (1.2, 1.3, 1.4.5 …), each with several mod sets (“packs”), with separate saves, configs and shaders.

**Latest version: 1.1.3.5** · [⬇ Download the latest release](https://github.com/Phxc2v/RickLauncher-Releases/releases/latest) · [English](#english) · [Русский](#русский)

> This repository hosts the **public releases** of RickLauncher (the app itself + changelog). The source code lives in a separate private repository.

---

## English

### What it is
RickLauncher keeps your Bannerlord setups apart: one tree of **game → packs**, where every game version has a clean “Native” profile and its own mod sets, each with isolated saves, mod settings (MCM) and shaders.

### Download & run
1. Download `RickLauncher-v1.1.3.5.zip` from the [latest release](https://github.com/Phxc2v/RickLauncher-Releases/releases/latest) and unpack it anywhere.
2. Run `RickLauncher.exe` (no .NET install needed — the build is self-contained).
3. Let it find your installed games (or add a game folder via “＋”), pick a game and pack, then press **PLAY**.

### Features
- **Multiple game versions and mod packs** side by side, each fully isolated (saves, MCM, shaders).
- **Import from the game:** pulls your existing saves, mod settings and enabled-mod order into a profile so you can continue right away.
- **Mod management:** enable/disable, load order, auto-ordering by dependencies, conflict checks.
- **Install mods** from an archive, folder or link (GitHub/ModDB/Nexus/direct), with automatic dependency download (Harmony/ButterLib/UIExtenderEx/MCM). Already-on-disk copies (other profiles, game folder, Steam Workshop) are reused, newest version first.
- **Mod updates:** the launcher compares versions and flags “↑ new version” when a newer copy exists on disk or a new release is published online (GitHub, mirror fallback), with a one-click “Update mods”.
- **`.rickpack` mod packs** — share a ready mod set as a single file; build one from a profile; a separate `RickPackEditor.exe` is bundled.
- **Fully non-invasive:** added mods live in the launcher’s own folder and are linked into the game only while it runs — your game folder and existing setup stay untouched.
- **Pre-build TOR shaders** ahead of time, with a progress bar.
- **Auto-update:** checks for a new version on launch — GitHub first, our backup server when GitHub is unreachable.
- **Interface languages:** English and Russian (add your own via the `Lang` folder).

### Requirements
- Windows 10/11 (64-bit). **No .NET install required** — the build is self-contained.
- An installed copy of Bannerlord.

### For users in Russia
GitHub is often blocked in Russia, so the launcher also self-updates from a **backup mirror** automatically. Just run the app — it falls back to the mirror on its own.

### Changelog
Full history: [CHANGELOG.en.md](CHANGELOG.en.md) · [CHANGELOG.ru.md](CHANGELOG.ru.md).

---

## Русский

### Что это
RickLauncher держит ваши сборки Bannerlord раздельно: одно дерево **игра → сборки**, где у каждой версии игры есть чистый профиль «Native» и свои наборы модов, каждый со своими сейвами, настройками модов (MCM) и шейдерами.

### Скачать и запустить
1. Скачайте `RickLauncher-v1.1.3.5.zip` из [последнего релиза](https://github.com/Phxc2v/RickLauncher-Releases/releases/latest) и распакуйте в любую папку.
2. Запустите `RickLauncher.exe` (устанавливать .NET **не нужно** — сборка автономная).
3. Дайте найти установленные игры (или добавьте папку игры через «＋»), выберите игру и сборку и нажмите **«ИГРАТЬ»**.

### Возможности
- **Несколько версий игры и сборок модов** рядом, каждая полностью изолирована (сейвы, MCM, шейдеры).
- **Перенос данных из игры:** подтягивает в профиль ваши сейвы, настройки модов и список включённых модов с порядком — чтобы сразу продолжить игру.
- **Управление модами:** вкл/выкл, порядок загрузки, авто-порядок по зависимостям, проверка конфликтов.
- **Установка модов** из архива, папки или по ссылке (GitHub/ModDB/Nexus/прямая), с авто-докачкой зависимостей (Harmony/ButterLib/UIExtenderEx/MCM). Копии, уже лежащие на диске (другой профиль, папка игры, Steam Workshop), переиспользуются — берётся самая новая версия.
- **Обновления модов:** лаунчер сверяет версии и помечает «↑ новая версия», когда на диске или онлайн (GitHub, запасной сервер) есть копия новее, и предлагает кнопку «Обновить моды».
- **Сборки модов `.rickpack`** — поделиться готовым набором модов одним файлом; сборку можно создать прямо из профиля; отдельный редактор `RickPackEditor.exe` идёт в комплекте.
- **Полная автономность:** добавленные моды хранятся в папке лаунчера и подключаются в игру только на время запуска — папка игры и существующие настройки не меняются.
- **Сборка шейдеров TOR** заранее, с прогресс-баром.
- **Автообновление:** при запуске проверяет новую версию — сначала GitHub, при недоступности — наш запасной сервер.
- **Языки интерфейса:** русский и английский (можно добавить свой — файлы в папке `Lang`).

### Требования
- Windows 10/11 (64-бит). Устанавливать .NET **не нужно** — сборка автономная.
- Установленная игра Bannerlord.

### Для пользователей из России
GitHub в России часто заблокирован, поэтому лаунчер умеет автообновляться с **запасного зеркала** сам. Просто запустите приложение — при недоступности GitHub оно переключится на зеркало автоматически.

### Что нового
Полная история изменений: [CHANGELOG.ru.md](CHANGELOG.ru.md) · [CHANGELOG.en.md](CHANGELOG.en.md).
