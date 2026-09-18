# RickLauncher

**Latest version: 2.4.1** · [⬇ Download the latest release](https://github.com/Phxc2v/RickLauncher-Releases/releases/latest) · [English](#english) · [Русский](#русский)

> This repository hosts the **public releases** of RickLauncher — the installer, the archive and the changelog. The source code lives in a separate private repository.
>
> Two downloads, same contents: `RickLauncher-Setup-v2.4.1.exe` for a first install (per-user, no admin rights), or `RickLauncher-v2.4.1.zip` to unpack anywhere. What changed: [CHANGELOG.en.md](CHANGELOG.en.md) / [CHANGELOG.ru.md](CHANGELOG.ru.md) — the full list of everything in 2.4.0: [CHANGELOG-2.4.0-full.en.md](CHANGELOG-2.4.0-full.en.md) / [CHANGELOG-2.4.0-full.ru.md](CHANGELOG-2.4.0-full.ru.md).

---

## English

A launcher for **Mount & Blade II: Bannerlord**, for when you have more than one version of the game and
more than one set of mods.

Keep 1.2, 1.3 and 1.4 side by side, each with its own sets of mods, its own saves and its own settings.
Switching between them takes one click, nothing has to be moved by hand, and nothing gets mixed up.

What's new is in `CHANGELOG.en.md`. The "Unreleased" section describes what is coming in the next release.

---

## What it is for

Bannerlord cannot keep several sets of mods. Every time you want to play something different you end up
moving folders about by hand, editing the list of mods and watching that saves from one set do not end up
in another. One slip and the game will not start — and it will not tell you why.

RickLauncher takes that over. Your mods live in its own folder and are put into the game **only while it
runs** — the game's folder stays as it was. Close the launcher and everything starts the way it used to.

---

## What it does

### Sets of mods

- **Several sets per game.** Every game it finds has a "Native" — the clean game with no mods — and as many
  of your own sets as you like. Each has its own saves and its own mod settings.
- **Load order** — in Bannerlord it decides whether a set works at all. There is an "Auto-order" button:
  the launcher knows where things belong — combat, factions, graphics, the map, the interface — and puts
  mods in their place rather than in alphabetical order. Where the order could be better, ▲/▼ hints appear
  beside the mods.
- **Copy a set in one click** — try something new without touching the one that works.
- **Move a set to another copy of the game.** Drag it onto another game in the list on the left. The
  launcher finds each mod's files wherever they live and shows a report first: what comes from where, how
  much it weighs, how much room will be left. Sets can move within the same version of the game.
- **A whole set as one file.** You can share a set: it becomes a single file that unpacks into the same set
  on somebody else's machine. Several ready-made sets ship with the launcher.

### Mods

- **Install from anywhere** — an archive, a folder, or a link to Nexus, GitHub, ModDB or the Steam
  Workshop. Just paste the link.
- **Steam Workshop mods** download inside the launcher, with no browser and no wrestling with archives.
  Sign in to Steam once — by QR code from your phone, or with a login and password. The password is never
  stored.
- **A reference covering nine thousand mods** — a base of its own that works offline. On first run the
  launcher offers to download it (about 330 MB), and when a newer one comes out it shows a card with an
  "Update" button. The reference answers the question no mod page answers: **which build of the mod your
  version of the game needs**. For many mods the newest build is made for the newest game and simply will
  not load on an older one — silently, with no message at all. On Nexus the build you need is usually
  buried in a collapsed "old files" section; the launcher takes you straight to it and explains why it is
  not offering the newest. The check knows six game versions — from 1.2.10 to 1.5.1.
- **Four answers about every mod:** works; loads but one feature will fail; in question; will not run. Red
  is used only for what will certainly not run — and it says when the mod will fall over: at start, on
  loading a save, in battle or on the campaign map.
- **A mod built for a newer game is not installed.** Not by an update, not from a pack, not from a link,
  not by hand: the question is asked on every path.
- **A card for every mod** — the **ⓘ** button in the list. What the mod does, pictures from its page,
  which versions of the game it runs on, what it clashes with, what it needs alongside, what other people
  made for it, what has changed in it.
- **Search for mods you do not have yet** — in your own language, inside the launcher.
- **Searching your own list of mods.** In a set of forty, the one you want is not found by scrolling: the
  line above the list filters it in place, and searches the name and the id alike — the list says "RTS
  Camera Universal" while the folder and every discussion say "RTSCameraUniversal".
- **A mod you already have is not downloaded again.** The launcher recognises it by its address before the
  download starts; and when the same mod came from a pack under a different address, it says so and asks
  whether to replace it or leave things as they were. Two copies of one mod are never left on the disk —
  the game would load only one of them anyway.
- **Translations of your mods** install with one button for the whole set, and come back out the same way.
- **Mod updates** are found for you — on disk and at the sources — but nothing is installed without you.
  The previous version is kept; undo is one button.
- **A mod set travels as one line — RLink.** The profile menu has "Copy the mod set (RLink)": the
  clipboard gets a short block of text with every mod, its order and its version. Send it in a chat and
  the other player gets a "Paste a mod set (RLink)" button — the launcher then rebuilds the same set:
  downloads what is missing, switches on what is already there, and puts it all in the same order, with
  builds picked for THEIR game. Even a 150-mod set fits in a single Discord message.
- **History** — what the launcher did to this set: what it installed, updated, removed, what failed and
  why. Anything that can be undone has a button beside it.

### What keeps the game from breaking

- **Before launch it checks that the set will hold together.** A mod missing a library brings the game down
  at start-up — before the main menu, leaving no crash files and nothing in the log. From inside the game
  that cannot be caught. The launcher sees it in advance, says which mod is missing what, and fetches what
  is missing with one button — exactly the build your game needs.
- **A green or red bar beside mods.** The launcher remembers which set of mods last reached the game
  itself and closed normally. If the game crashed after that, everything that appeared or updated since is
  marked red — with a "Switch these N off" button. The load order is left alone.
- **Two mods claiming the same records.** Two mods can describe the same troops or the same items — the
  game says nothing, one version simply disappears. The launcher shows those pairs, and where somebody has
  published a patch for that exact pair, it names it.
- **Crashes explained in plain words.** If the game falls over, the launcher reads its files and says what
  happened in words: out of memory, the graphics card stopped responding, damaged shaders, a clash between
  mods. The technical detail is tucked behind a button — you need it only if you are sending us a report.
- **A check of your machine before long work** — free memory, disk space, graphics settings — with a "fix
  it" button wherever that is possible.
- **A mod carrying somebody else's shader cache.** Some mods ship their shaders already compiled. When those
  were built for another version of the game, the engine faults on them **before the main menu** — a second
  and a half in, with no crash window and nothing in any log. The mod pages treat it with "clear the cache
  after installing this or it will not start". The launcher does it itself: before a launch it compares each
  mod's cache version against your game's and removes what your game cannot read. Only the cache goes; the
  engine builds its own again.
- **A mod installed only in part.** When a mod is missing a library it declares itself, the game puts an
  error box on the loading screen and carries on — while the mod does nothing at all. The launcher says so
  before the launch and, when the mod came from a pack, offers to reinstall **just that mod**.

### Shaders

Big graphical sets stutter badly on the first run: the game is preparing shaders while you play. The
launcher can prepare them in advance, with one button, a progress bar and honest numbers. If it runs out
of memory along the way it saves what is done, restarts the game and carries on from the same place.

Each set of mods has shaders of its own — they are built for your screen resolution, your settings and your
list of mods, so the sets do not interfere with each other.

The shader quality is your choice: the window before the build offers three, and it opens on low —
the recommended one. The game then plays at the same setting, and the higher it goes the longer the
build takes and the more memory it needs.

### Small things that help

- **An illustrated manual inside the launcher** — the "Help" button. No internet needed. Each chapter is a
  picture of the window with numbered circles: hover over a circle to see what that button does.
- **Six languages** — Russian, English, French, Turkish, Chinese simplified and traditional. You can add
  your own. On the first run the launcher asks which one to speak to you in.
- **The game always runs on the powerful graphics card.** On a laptop with two of them the launcher switches
  the game to the discrete one itself, before a launch and before a shader build alike. It asks nothing:
  there is nothing here to choose.
- **A desktop shortcut** starts one profile straight into the game, with no launcher window. The launcher
  itself stays minimised in the taskbar: it holds the mods and saves together for the session and puts
  everything back when you quit.
- **A magazine about mods.** A new issue arrives as a card on the right of the main screen: cover, number,
  date. It is read inside the launcher — paging, zoom and printing — opens on the page you left it on, and
  comes in the language of the interface. The PDF itself is fetched only when you press Read; the mods it
  writes about open as launcher cards. The card can be put away until the next issue, or switched off for
  good.
- **Themes to choose from**, and all your settings save to one file so you can carry them to another
  machine.
- **It updates itself** in one click. If GitHub is unreachable, from a backup server.

---

## Installing

Two ways, same contents:

- **The installer** — the ordinary route. Installs for your account only, never asks for administrator
  rights, creates shortcuts. You can choose the folder.
- **The archive** — unpack it anywhere and run it. Nothing else needs installing.

The program deliberately does not install into "Program Files": all your data sits next to it, and writing
there needs administrator rights — self-updating would break.

**What you need:** Windows 10 or 11, and Bannerlord installed. Nothing else.

## Getting started

1. Run the launcher.
2. Let it look for your games — or add the game's folder by hand with "＋".
3. Pick a game and a set of mods on the left.
4. Press **"PLAY"**.

Stuck? Menu → **"Help"**.

---

## Where your data lives

Everything the launcher knows about you — sets of mods, saves, downloaded mods — is in a `RickLauncherData`
folder beside the program itself. Move that folder along with the program and you have moved everything.

When you uninstall, the launcher asks whether to delete it. The default is **no**: your saves and sets stay.

### If your Documents folder is in OneDrive

Whole mod folders have gone missing from there, so the launcher warns you and offers to move its data out.
Either way it keeps the game's own settings separately for each set and puts them in place before launch.

---

## How mods are removed

The launcher remembers who installed what, and does not touch anybody else's files:

- **A mod you installed through the launcher** is deleted from disk — but only this set's copy. It stays in
  your other sets.
- **A mod that was already in the game's folder** (put there by hand, came with a repack, installed from
  the Steam Workshop) is simply taken out of the set. The files stay: the launcher never deletes what it
  did not install.
- **Parts of the game itself** are never touched.

The button works out which of those it is and says so before you press it.

Deleting a whole set together with its mods runs **in the background**: the set leaves the list at once
while its folders go behind a progress bar — on tens of gigabytes that is minutes, and the launcher stays
usable throughout.

---

## Support the project

The launcher is free and will stay free. Donating unlocks nothing and changes nothing — but hosting the
releases and the backup download server come out of our own pocket.

- By card, in a browser: https://web.tribute.tg/d/Owd
- The same page inside Telegram: https://t.me/tribute/app?startapp=dOwd

In the launcher this is the **"♥ Donate"** button — there is a QR code there for paying from a phone.

## If something does not work

Tell us what you did, what you expected and what happened instead. After a crash the easiest thing is to
send the whole report folder — the window that explains the crash opens it for you.

- Telegram: https://t.me/CodeRickTg
- Discord: https://discord.gg/ZDJZFxQeMV

Links to all our places are along the bottom of the launcher's main window.

---

## Русский

Программа для запуска **Mount & Blade II: Bannerlord**, если у вас не одна версия игры и не один набор
модов.

Держите рядом 1.2, 1.3 и 1.4 — у каждой свои наборы модов, свои сохранения, свои настройки. Переключение
между ними в один клик, ничего не надо переносить руками и ничего не перемешивается.

Что нового — в `CHANGELOG.ru.md`. Раздел «Готовится» описывает то, что выйдет следующим выпуском.

---

## Зачем это нужно

Bannerlord не умеет держать несколько наборов модов. Каждый раз, когда вы хотите поиграть в другое,
приходится вручную перекладывать папки, править список модов и следить, чтобы сохранения от одной сборки
не попали в другую. Одна ошибка — и игра не запускается, а почему, она не скажет.

RickLauncher берёт это на себя. Ваши моды лежат в его собственной папке и подставляются в игру **только на
время запуска** — папка игры остаётся такой, какой была. Закрыли лаунчер, и всё запускается «как раньше».

---

## Что он умеет

### Наборы модов

- **Несколько наборов на одну игру.** У каждой найденной игры есть «Native» — чистая игра без модов, — и
  сколько угодно ваших наборов. У каждого свои сохранения и свои настройки модов.
- **Порядок загрузки** — в Bannerlord от него зависит, заработает набор или нет. Есть кнопка
  «Авто-порядок»: лаунчер знает, где чему стоять — боёвка, фракции, графика, карта, интерфейс, — и
  расставляет моды по местам, а не по алфавиту. Если порядок можно улучшить, рядом с модами появляются
  подсказки ▲/▼.
- **Копия набора в один клик** — попробовать что-то новое, не трогая рабочий.
- **Перенос набора на другую копию игры.** Перетащите его мышью на другую игру в списке слева. Лаунчер сам
  разыщет файлы каждого мода, где бы они ни лежали, и покажет отчёт: что откуда берётся, сколько весит,
  сколько останется на диске. Переносить можно в пределах одной версии игры.
- **Готовый набор одним файлом.** Своим набором можно поделиться: получится один файл, который у друга
  развернётся в такой же набор. Несколько готовых наборов едут вместе с лаунчером.

### Моды

- **Установка откуда угодно** — из архива, из папки, по ссылке на Nexus, GitHub, ModDB или Мастерскую
  Steam. Просто вставьте ссылку.
- **Моды из Мастерской Steam** качаются прямо в лаунчере, без браузера и возни с архивами. Один раз
  войдите в Steam — по QR-коду с телефона или логином и паролем. Пароль нигде не сохраняется.
- **Справочник по девяти тысячам модов** — своя база, которая работает без интернета. При первом запуске
  лаунчер предложит её скачать (около 330 МБ), а когда выйдет новая — покажет карточку с кнопкой
  «Обновить». Справочник отвечает на вопрос, которого нет ни на одной странице мода: **какую версию мода
  ставить именно на вашу версию игры**. У многих модов свежая версия собрана под новую игру и на старой
  просто не запускается — молча, без единого сообщения. На Nexus нужная версия обычно спрятана в
  свёрнутом разделе старых файлов; лаунчер ведёт прямо к ней и объясняет, почему предлагает не самую
  новую. Проверка знает шесть версий игры — от 1.2.10 до 1.5.1.
- **Четыре ответа про каждый мод:** работает; запустится, но одна возможность откажет; под вопросом; не
  запустится. Красным написано только то, что точно не запустится — и сказано, когда именно мод упадёт:
  на старте, на загрузке сохранения, в бою или на карте кампании.
- **Мод собран под более новую игру — лаунчер его не поставит.** Ни обновлением, ни из сборки, ни по
  ссылке, ни руками: вопрос задаётся на каждом пути.
- **Карточка мода** — кнопка **ⓘ** в списке. Что мод делает, снимки со страницы, на каких версиях игры
  работает, с чем спорит, что ему нужно рядом, что к нему сделали другие, что в нём менялось.
- **Поиск модов, которых у вас ещё нет** — по-русски, прямо в лаунчере.
- **Поиск по вашему списку модов.** В наборе из сорока модов нужный не находится прокруткой: строка над
  списком фильтрует его на месте, и ищет как по названию, так и по идентификатору — в списке «RTS Camera
  Universal», а в папке и во всех обсуждениях «RTSCameraUniversal».
- **Мод, который у вас уже стоит, не скачивается заново.** Лаунчер узнаёт его по адресу ещё до закачки, а
  если тот же мод пришёл из сборки с другого адреса — говорит об этом и спрашивает, заменить или оставить
  как было. Двух копий одного мода на диске не остаётся: игра всё равно загрузит одну.
- **Переводы модов на ваш язык** ставятся одной кнопкой сразу для всего набора и снимаются так же.
- **Обновления модов** лаунчер находит сам — на диске и у источников, — но ничего не ставит без вас.
  Предыдущая версия сохраняется, откат в одну кнопку.
- **Набор модов передаётся одной строкой — RLink.** В меню профиля «Скопировать набор модов (RLink)»: в
  буфер обмена ложится короткий текст со всеми модами, их порядком и версиями. Отправьте его в чат — у
  другого игрока появится кнопка «Вставить набор модов (RLink)», и лаунчер соберёт тот же набор: скачает
  недостающее, включит то, что уже есть, и выстроит в том же порядке. Версии подбираются под ЕГО игру.
  Даже набор из 150 модов влезает в одно сообщение Discord.
- **История** — что лаунчер делал с этим набором: что поставил, что обновил, что удалил, что не получилось
  и почему. Любое обратимое действие отменяется кнопкой рядом.

### Что не даст сломать игру

- **Перед запуском проверяется, соберётся ли набор.** Мод, которому не хватает библиотеки, роняет игру на
  старте — до главного меню, не оставляя ни файлов вылета, ни записей в журнале. Изнутри игры такое не
  поймать. Лаунчер видит это заранее, говорит, какому моду чего не хватает, и докачивает недостающее
  одной кнопкой — именно той версии, что нужна вашей игре.
- **Зелёная и красная полоса у модов.** Лаунчер запоминает, с каким набором модов игра в последний раз
  нормально дошла до самой игры. Если после этого она упала, всё, что появилось или обновилось с тех
  пор, помечено красным — и есть кнопка «Выключить эти N». Порядок загрузки не трогается.
- **Споры за одни и те же записи игры.** Два мода могут описывать одних и тех же воинов или предметы —
  игра об этом молчит, просто чей-то вариант исчезает. Лаунчер показывает такие пары и, если кто-то
  выпустил патч именно для них, называет его.
- **Разбор вылета человеческим языком.** Если игра упала, лаунчер читает её файлы и объясняет причину
  понятными словами: мало памяти, зависла видеокарта, испорченные шейдеры, конфликт модов. Технические
  подробности спрятаны под отдельную кнопку — они нужны, только если вы отправляете отчёт нам.
- **Проверка системы перед долгой работой** — свободная память, место на диске, настройки видеокарты — и
  кнопка «исправить» там, где это можно исправить.
- **Чужой кэш шейдеров внутри мода.** Некоторые моды везут с собой уже собранные шейдеры. Если они собраны
  под другую версию игры, движок падает на них **до главного меню** — за полторы секунды, без окна вылета и
  без строчки в журнале. На страницах модов это лечат советом «почисти кэш, иначе не запустится». Лаунчер
  делает это сам: перед запуском сверяет версию кэша каждого мода с версией вашей игры и убирает то, что
  она не прочитает. Убирается только кэш — движок соберёт свой заново.
- **Мод, установленный наполовину.** Если у мода нет библиотеки, которую он сам объявляет, игра покажет
  окно с ошибкой на загрузке и пойдёт дальше — а мод не будет делать ничего. Лаунчер говорит об этом перед
  запуском и, если мод пришёл из сборки, предлагает переустановить **только его**.

### Шейдеры

Крупные графические сборки при первом запуске подолгу «подвисают» — игра готовит шейдеры прямо во время
игры. Лаунчер умеет подготовить их заранее, одной кнопкой, с полосой и понятными числами. Если по дороге
кончится память, он аккуратно сохранит сделанное, перезапустит игру и продолжит с того же места.

У каждого набора модов свой комплект шейдеров — они собраны под ваше разрешение экрана, ваши настройки и
ваш список модов, и наборы друг другу не мешают.

Качество шейдеров выбираете вы: в окне перед сборкой три варианта, по умолчанию низкое —
рекомендуемое. Игра потом играется на том же качестве, а чем оно выше, тем дольше сборка и тем больше
нужно памяти.

### Мелочи, которые заметно облегчают жизнь

- **Руководство с картинками прямо в лаунчере** — кнопка «Помощь». Интернет не нужен. Каждый раздел это
  снимок окна с пронумерованными кружками: наведите на кружок и увидите, что делает эта кнопка.
- **Шесть языков** — русский, английский, французский, турецкий, китайский упрощённый и традиционный.
  Можно добавить свой. При первом запуске лаунчер сам спросит, на каком языке с вами говорить.
- **Игра всегда идёт на мощной видеокарте.** На ноутбуках с двумя картами лаунчер переключает игру на
  дискретную сам — и перед запуском, и перед сборкой шейдеров. Вопросов не задаёт: выбирать тут нечего.
- **Ярлык на рабочий стол** — запуск профиля сразу в игру, минуя окно лаунчера. Сам лаунчер при этом
  сворачивается в панель задач: он держит моды и сохранения на время сессии и всё возвращает после выхода.
- **Журнал о модах.** Новый выпуск приходит карточкой справа на главном экране: обложка, номер, дата.
  Читается прямо в лаунчере — с листанием, зумом и печатью, — открывается на той полосе, где вы его
  закрыли, и приходит на языке интерфейса. Сам PDF качается только когда вы нажали «Читать»; моды, о
  которых написано, открываются карточкой лаунчера. Карточку можно убрать до следующего номера или
  выключить совсем.
- **Оформление на выбор** и сохранение всех настроек в один файл, чтобы перенести на другой компьютер.
- **Обновляется сам** в один клик. Если GitHub недоступен — с запасного сервера.

---

## Установка

Два варианта, содержимое одинаковое:

- **Установщик** — обычный путь. Ставится только для вашей учётной записи, права администратора не
  спрашивает, создаёт ярлыки. Папку можно выбрать свою.
- **Архив** — распакуйте куда угодно и запустите. Ничего дополнительно устанавливать не нужно.

Программа намеренно не ставится в «Program Files»: все ваши данные лежат рядом с ней, а туда без прав
администратора не записать — самообновление ломалось бы.

**Что нужно:** Windows 10 или 11 и установленный Bannerlord. Больше ничего.

## С чего начать

1. Запустите лаунчер.
2. Согласитесь на поиск игр — или добавьте папку с игрой вручную кнопкой «＋».
3. Выберите игру и набор модов слева.
4. Нажмите **«ИГРАТЬ»**.

Что-то непонятно — меню → **«Помощь»**.

---

## Где лежат ваши данные

Всё, что лаунчер про вас знает — наборы модов, сохранения, скачанные моды, — лежит в папке
`RickLauncherData` рядом с самой программой. Перенесли папку вместе с программой — перенесли всё.

При удалении лаунчер спросит, удалять ли эту папку. По умолчанию — **нет**: сохранения и наборы остаются.

### Если ваши «Документы» в OneDrive

Оттуда пропадали целые папки модов, поэтому лаунчер об этом предупредит и предложит вынести свои данные.
Настройки игры он в любом случае хранит отдельно для каждого набора и подставляет перед запуском.

---

## Как удаляются моды

Лаунчер помнит, кто какой мод поставил, и не трогает чужое:

- **Мод, который поставили вы через лаунчер,** удаляется с диска — но только копия этого набора. В других
  наборах он останется.
- **Мод, который лежал в папке игры** (положили руками, пришёл с репаком, стоит из Мастерской Steam),
  просто убирается из набора. Файлы остаются на месте: лаунчер не удаляет то, чего не устанавливал.
- **Части самой игры** не трогаются вообще.

Кнопка сама выбирает, что сделать, и говорит об этом до нажатия.

Удаление целого набора вместе с модами идёт **в фоне**: сам набор пропадает из списка сразу, а его папки
удаляются с полосой хода работы — на десятках гигабайт это минуты, и всё это время лаунчером можно
пользоваться.

---

## Поддержать

Лаунчер бесплатный и таким останется. Донат ничего не открывает и ни на что не влияет — но хостинг
релизов и запасной сервер для загрузок оплачиваются из своего кармана.

- Оплата картой в браузере: https://web.tribute.tg/d/Owd
- То же самое внутри Telegram: https://t.me/tribute/app?startapp=dOwd

В лаунчере это кнопка **«♥ Донат»** — там же QR-код, чтобы заплатить с телефона.

## Если что-то не работает

Напишите, что делали, чего ждали и что получилось. После вылета проще всего прислать целиком папку
отчёта — её открывает то самое окно с разбором.

- Telegram: https://t.me/CodeRickTg
- Discord: https://discord.gg/ZDJZFxQeMV

Ссылки на все наши площадки есть внизу главного окна лаунчера.
