<p align="center">
  <img width="1020" height="156" alt="minecraft_title" src="https://github.com/user-attachments/assets/06d79e02-641a-439a-bb4b-462911869f7b" />
</p>

<h1 align="center">qackEngineMod</h1>

<p align="center">
  <b>Движок сюжетных историй для Minecraft · Story engine for Minecraft</b><br>
  Forge 1.20.1 · GeckoLib 4 (встроен / bundled) · v1.5
</p>

<p align="center">
  <a href="#-русский">🇷🇺 Русский</a> · <a href="#-english">🇬🇧 English</a>
</p>

---

## 🇷🇺 Русский

**qackEngineMod** — мод для создания сюжетных карт, RPG-систем и кат-сцен прямо в игре. Сцены и диалоги, NPC с моделями из Blockbench, квесты, фракции, свои интерфейсы, оверлеи HUD, частицы и переменные. Всё собирается во встроенном редакторе (клавиша **K**), без перезапуска игры и без программирования.

### ✨ Возможности

| | |
|---|---|
| ✉ **Сцены и диалоги** | Три вида одной и той же сцены: **граф** (узлы со связями), **конструктор** (блоки-пазлы как в Scratch) и **код qackScript**. Переключаются в любой момент. |
| ✎ **Диалоги** | 13 тем окна: Кино, Классика, Пиксель, Субтитры, Визуальная новелла, JRPG, Комикс, Стекло, Терминал, Пергамент, Неон, Карточка и **«Свой»**. В «Своём» можно поставить свои текстуры и перетаскивать части окна мышью прямо в предпросмотре. Разметка текста: цвет, жирный, волна, дрожь, радуга, паузы. Есть история реплик, авто-режим, пропуск. |
| ☺ **NPC на GeckoLib** | Свои модели `.geo.json`, текстуры и анимации. Отдельные анимации покоя, ходьбы, разговора и атаки, плюс случайные «доп. анимации покоя». Портрет в диалоге: 3D, картинка для каждой эмоции или без портрета. Маршруты задаются жезлом, NPC может держать предмет в руке и передавать его игроку. |
| ★ **Квесты** | Цели (убить, собрать предметы, поговорить, дойти до места, флаг, переменная), награды, журнал квестов на клавише **J**, всплывающие уведомления. |
| ⚑ **Фракции** | Отношение к игроку и отношения между фракциями: NPC защищают своих и нападают на врагов. |
| ▣ **Свои GUI** | Визуальный редактор: кнопки, надписи, панели, картинки, полосы прогресса, поля ввода, галочки, предметы, **3D-модели**. Логику кнопок можно задать прямо в кнопке (сцена, переменная, команда, условие) или собрать сценой. |
| ◫ **Оверлеи HUD** | Свои элементы поверх экрана: полосы опыта, счётчики монет, подсказки. |
| # **Переменные** | Типы число, строка, да/нет, для игрока или общие для мира. Подставляются в текст как `{var:coins}`, проверяются в условиях как `var:coins>=10`. |
| ✺ **Частицы** | Редактор эффектов из излучателей с 3D-предпросмотром. Формы: точка, сфера, кольцо, спираль, столб, линия. |
| ⊞ **Свои редакторы** | Сами задаёте поля и заполняете записи (навыки, рецепты, персонажи). Данные доступны в текстах как `{data:skills/fireball/name}`. |
| ❖ **Шаблоны** | Готовые системы ставятся одной кнопкой: прокачка, система доверия, магазин, монеты за время, свой редактор. |
| ⚒ **Предметы и блоки** | Свои предметы и блоки со своими моделями и текстурами. |
| ? **Справка** | Подробная справка внутри редактора. Интерфейс редактора на **русском** и **английском**. |

### 📦 Установка

1. Установите **Minecraft Forge 1.20.1** (47.x).
2. Положите `qackEngineMod-1.5-1.20.1.jar` в папку `.minecraft/mods`. GeckoLib уже встроен в мод, ставить его отдельно не нужно.
3. Зайдите в мир с правами оператора и нажмите **K**.

### 🚀 Быстрый старт

1. **K**, вкладка ☺ **NPC**: создайте NPC, например `guide`, и нажмите «✚ Создать этого NPC рядом».
2. Вкладка ✉ **Сцены**: создайте сцену с триггером «ПКМ по NPC» → `guide` и добавьте реплику.
3. Нажмите «💾 Сохранить» и кликните по NPC правой кнопкой.

Та же сцена в коде qackScript:

```text
on interact_npc npc=guide {
  say guide happy "Привет, {player}!"
  choice "Поможешь?" {
    option "Да"  { quest action=start id=find_exit }
    option "Нет" { say guide sad "Жаль…" }
  }
}
```

### 🎮 Управление

| Клавиша | Действие |
|---|---|
| **K** | Редактор |
| **J** | Журнал квестов |
| ЛКМ / Пробел | Следующая реплика |
| 1–9 | Выбор ответа |
| H | История реплик |
| A | Авто-режим |
| Ctrl (удерживать) | Пропуск |

### ⌨ Команды

```text
/qack editor                             — открыть редактор
/qack reload                             — перечитать всё из config/qackengine
/qack run <сцена> [игроки] · /qack stop  — запустить / остановить сцену
/qack npc spawn <id> [x y z] · /qack npc remove
/qack wand                               — жезл маршрутов NPC
/qack flag set|clear <имя> · /qack flag list
/qack var set <имя> <значение>
/qack quest start|complete <id> · /qack quest list · /qack quest reset
/qack gui open <id> [игроки] · /qack gui close
/qack overlay show|hide <id>
```

### 📝 Разметка текста

```text
[c=#ffcc00]цвет[/c]  [b]жирный[/b]  [i]курсив[/i]  [wave]волна[/wave]
[shake]дрожь[/shake]  [rainbow]радуга[/rainbow]  [p=500] — пауза 500 мс
{player} — ник игрока · {var:coins} — переменная · {item:minecraft:diamond} — сколько есть у игрока
{data:редактор/запись/поле} — данные своего редактора
```

Условия (в кнопках, триггерах и блоке «Условие») соединяются через `&`, отрицание пишется через `!`:
`flag:met_guide & var:coins>=5 & !quest:find_exit & item:minecraft:diamond>=1`

### 🦴 Модели NPC (Blockbench)

- Формат **GeckoLib**: файлы `.geo.json`, `.png` и `.animation.json`.
- Чтобы NPC держал предмет в руке, добавьте в модель кости **`right_elbow`** и **`left_elbow`**.
  - Каждая кость должна быть дочерней к кости руки.
  - Её точка вращения (pivot) ставится у кисти.
- Без своих файлов используется встроенный человечек с анимациями `idle`, `walk`, `talk` и `wave`.

### 📁 Файлы

Всё хранится в `config/qackengine/` и редактируется как JSON вручную или через редактор:

```text
scripts/    сцены            npc/        NPC (+ models, animations, textures)
quests/     квесты           factions/   фракции
guis/       интерфейсы       overlays/   оверлеи HUD
variables/  переменные       particles/  частицы
editors/    свои редакторы   items/, blocks/  предметы и блоки
gui/style.json  стиль диалогов   gui/textures/  картинки для GUI и портретов
sounds/*.ogg → звук qackengine:<имя>
```

> На сервере папка `config/qackengine` должна совпадать у сервера и у игроков: модели, текстуры и портреты загружаются на клиенте.

### 📄 Лицензия

© sp14ka. All Rights Reserved.

---

## 🇬🇧 English

**qackEngineMod** is a Minecraft mod for building story maps, RPG systems and cutscenes right inside the game. It covers scenes and dialogues, NPCs with Blockbench models, quests, factions, custom GUIs, HUD overlays, particles and variables. You build everything in the in-game editor (**K** key), with no restarts and no programming.

### ✨ Features

| | |
|---|---|
| ✉ **Scenes & dialogues** | Each scene has three views: a **node graph**, a **block builder** (Scratch-like puzzle blocks) and **qackScript code**. You can switch between them at any time. |
| ✎ **Dialogues** | 13 window themes: Cinematic, Classic, Pixel, Subtitles, Visual Novel, JRPG, Comic, Glass, Terminal, Parchment, Neon, Card and **Custom**. Custom lets you use your own textures and drag window parts with the mouse in the live preview. Text markup supports color, bold, wave, shake, rainbow and pauses. Dialogues also have a history log, auto mode and skip. |
| ☺ **GeckoLib NPCs** | Custom `.geo.json` models, textures and animations. Separate idle, walk, talk and attack animations, plus random extra idle animations. Dialogue portraits can be 3D, a per-emotion image or turned off. NPCs follow paths set with a wand, can hold items and hand them to the player. |
| ★ **Quests** | Objectives (kill, collect items, talk, reach a location, flag, variable), rewards, a quest journal on **J** and toasts. |
| ⚑ **Factions** | Each faction has an attitude toward the player and relations with other factions. NPCs defend allies and attack enemies. |
| ▣ **Custom GUIs** | Visual editor with buttons, labels, panels, images, progress bars, text inputs, checkboxes, items and **3D models**. Set button logic in the button itself (scene, variable, command, condition) or build it as a scene. |
| ◫ **HUD overlays** | Your own on-screen elements: XP bars, coin counters, hints. |
| # **Variables** | Number, string and bool types, stored per player or per world. Insert them in text as `{var:coins}` and check them in conditions as `var:coins>=10`. |
| ✺ **Particles** | Emitter-based effect editor with a 3D preview. Shapes: point, sphere, ring, spiral, column, line. |
| ⊞ **Custom editors** | Define your own fields and fill in records (skills, recipes, characters). Use them in text as `{data:skills/fireball/name}`. |
| ❖ **Templates** | One-click ready-made systems: leveling, trust system, shop, coins over time, custom editor. |
| ⚒ **Items & blocks** | Custom items and blocks with their own models and textures. |
| ? **Help** | Detailed in-editor help. The editor UI is available in **English** and **Russian**. |

### 📦 Installation

1. Install **Minecraft Forge 1.20.1** (47.x).
2. Put `qackEngineMod-1.5-1.20.1.jar` into `.minecraft/mods`. GeckoLib is already bundled, so you don't need to install it separately.
3. Join a world with operator rights and press **K**.

### 🚀 Quick start

1. Press **K**, open the ☺ **NPC** tab, create an NPC (for example `guide`) and click "✚ Spawn this NPC nearby".
2. In the ✉ **Scenes** tab, create a scene with the trigger "Right-click NPC" → `guide` and add a dialogue line.
3. Click "💾 Save", then right-click the NPC.

The same scene in qackScript:

```text
on interact_npc npc=guide {
  say guide happy "Hello, {player}!"
  choice "Will you help?" {
    option "Yes" { quest action=start id=find_exit }
    option "No"  { say guide sad "Too bad…" }
  }
}
```

### 🎮 Controls

| Key | Action |
|---|---|
| **K** | Editor |
| **J** | Quest journal |
| LMB / Space | Next line |
| 1–9 | Pick an answer |
| H | Dialogue history |
| A | Auto mode |
| Ctrl (hold) | Skip |

### ⌨ Commands

```text
/qack editor                             — open the editor
/qack reload                             — reload everything from config/qackengine
/qack run <scene> [players] · /qack stop — start / stop a scene
/qack npc spawn <id> [x y z] · /qack npc remove
/qack wand                               — NPC path wand
/qack flag set|clear <name> · /qack flag list
/qack var set <name> <value>
/qack quest start|complete <id> · /qack quest list · /qack quest reset
/qack gui open <id> [players] · /qack gui close
/qack overlay show|hide <id>
```

### 📝 Text markup

```text
[c=#ffcc00]color[/c]  [b]bold[/b]  [i]italic[/i]  [wave]wave[/wave]
[shake]shake[/shake]  [rainbow]rainbow[/rainbow]  [p=500] — 500 ms pause
{player} — player name · {var:coins} — variable · {item:minecraft:diamond} — how many the player has
{data:editor/record/field} — custom editor data
```

Conditions in buttons, triggers and the "Condition" block are joined with `&`. Use `!` to negate a condition:
`flag:met_guide & var:coins>=5 & !quest:find_exit & item:minecraft:diamond>=1`

### 🦴 NPC models (Blockbench)

- Models use the **GeckoLib** format: `.geo.json`, `.png` and `.animation.json` files.
- To let an NPC hold an item, add the bones **`right_elbow`** and **`left_elbow`** to the model.
  - Each bone must be a child of the arm bone.
  - Put its pivot at the hand.
- Without custom files, the mod uses a built-in figure with `idle`, `walk`, `talk` and `wave` animations.

### 📁 Files

Everything lives in `config/qackengine/` as JSON files. You can edit them by hand or through the editor:

```text
scripts/    scenes           npc/        NPCs (+ models, animations, textures)
quests/     quests           factions/   factions
guis/       GUIs             overlays/   HUD overlays
variables/  variables        particles/  particle effects
editors/    custom editors   items/, blocks/  items and blocks
gui/style.json  dialogue style   gui/textures/  GUI and portrait images
sounds/*.ogg → sound qackengine:<name>
```

> On a server, the `config/qackengine` folder must be the same on the server and on every player's client, because models, textures and portraits load client-side.

### 📄 License

© sp14ka. All Rights Reserved.
