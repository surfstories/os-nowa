# OS_Nowa

**Личная операционная система для работы с ИИ-агентом.** · **A personal productivity operating
system any coding agent can run.**

---

## Установка

Откройте Claude Code (или другого агента) и вставьте этот текст одним сообщением:

```
Set up OS_Nowa for me.

1. Ask where to put it. Default: a folder called "os-nowa" in my home directory.
2. Get it there, then disconnect it — the workspace is mine, the local git history is my undo:
       git clone https://github.com/surfstories/os-nowa.git os-nowa
       cd os-nowa && git remote remove origin
   No git? Don't install it. Download instead, then rename "os-nowa-main" to "os-nowa":
       curl -L https://github.com/surfstories/os-nowa/archive/refs/heads/main.tar.gz -o os-nowa.tar.gz
       tar -xzf os-nowa.tar.gz
   If neither works, tell me what failed — don't guess.
3. Work from that folder: read AGENTS.md, then follow system/procedures/onboarding.md.

Talk to me in the language I write to you in, from your very first reply.
```

**Команда на английском — это нормально.** Ассистент прочитает её и заговорит с вами на вашем языке
с первого же ответа. Ничего устанавливать не нужно, ключи и пароли не нужны.

*Paste it as-is — the agent will reply in your language. Nothing to install, no keys, no account.*

---

## Русский

### Что это

OS_Nowa — это папка с текстовыми файлами, устроенная так, что ИИ-агент может с ней работать: знает,
кто вы, над чем вы работаете и куда что класть. Она заполняется вашими собственными материалами и
становится тем полезнее, чем дольше вы ей пользуетесь. Всё лежит у вас на компьютере обычным
текстом — ни аккаунта, ни подписки, ни синхронизации.

### Что произойдёт после установки

Агент проведёт вас через настройку — минут десять, разговором, без единой команды. Он спросит, чем
вы занимаетесь и что для вас сейчас важно, и вместе с вами заведёт первую тему и запишет первое
решение. В конце у вас будет не пустой каркас, а рабочее пространство с вашим собственным
содержимым.

### Что внутри

- **Три уровня памяти.** Небольшой всегда загружаемый слой — кто вы и что важно. Каталог по каждой
  теме. И сами материалы, которые открываются по одному. Смысл в том, чтобы агенту не приходилось
  читать всё сразу.
- **Четыре рабочих цикла.** Знания (по темам, с каталогом), задачи (один файл, только открытые),
  проекты (сначала спецификация, потом код) и решения (только дополняется, никогда не переписывается).
- **Шесть вещей, которые можно попросить.** Просто скажите их обычными словами — ничего не нужно
  вводить особым образом, никаких слэшей и меню:
  - *«настрой меня»* — первичная настройка (`onboard`)
  - *«как это устроено?»* — объяснит любую часть системы, в любой момент (`explain`)
  - *«проверь систему»* — скажет, не разъехалось ли что-нибудь (`os-health`)
  - *«level up»* — превращает еженедельную рутину в автоматику (`level-up`)
  - *«сделай из этого команду»* — создаёт новую такую команду (`create-skill`)
  - *«почему ты это не нашёл?»* — если что-то не нашлось, чинит причину, а не симптом (`backtrack`)

  Короткое имя в скобках тоже работает, если вам удобнее одно слово.

### Честные границы

- **Проверено** в Claude Code — установка и настройка проходят целиком, от вставки команды до
  готового рабочего пространства.
- **Структура и правила переносятся в другие агенты.** Здесь всё — обычный markdown, а `AGENTS.md` —
  файл, который кодовые агенты читают по общему соглашению. Измерено в **Codex** (v0.146.0): новая
  сессия на вопрос «на чём мне сегодня сосредоточиться» сама открыла три файла в `me/` и ответила по
  ним — три запуска из трёх. **Cursor и Gemini следуют тому же соглашению, но не проверялись** —
  считайте это вероятным, а не доказанным.
- **Пять команд из шести работают в любом агенте, одна — нет.** Каждая из них — письменная процедура
  в `system/procedures/`, на которую `AGENTS.md` указывает любому агенту. Исключение — *«сделай из
  этого команду»*: она создаёт файл-скилл для Claude Code, поэтому имеет смысл только там, и **любая
  команда, которую вы создадите сами, тоже работает только в Claude Code.** Всё остальное — кто вы,
  над чем работаете, четыре рабочих цикла, правила хранения и остальные пять команд — переносится.
- **Никаких интеграций в этой версии.** Ни почты, ни календаря, ни облака. Только папка с текстом.

---

## English

### What it is

OS_Nowa is a folder of plain text files, arranged so that a coding agent can operate it: it knows who
you are, what you are working toward, and where things belong. It fills up with your own material and
gets more useful the longer you use it. Everything lives on your own machine as plain text — no
account, no subscription, nothing synced anywhere.

### What happens after you install it

The agent walks you through setup — about ten minutes, as a conversation, with no commands to type.
It asks what you do and what matters to you right now, and together you create your first subject
area and log your first decision. You finish with a workspace holding your own content, not an empty
skeleton.

### What is inside

- **Three levels of memory.** A small always-loaded layer — who you are, what matters. A catalog per
  subject. And the material itself, opened one file at a time. The point is that the agent never has
  to read everything to answer something.
- **Four working loops.** Knowledge (by subject, catalogued), tasks (one file, open items only),
  projects (spec before build) and decisions (append-only, never rewritten).
- **Six things you can ask for.** You just say them in ordinary words — there is nothing to type in a
  special way, no slash, no menu:
  - *"set me up"* — first-time setup (`onboard`)
  - *"how does this work?"* — explains any part of it, at any moment (`explain`)
  - *"check my system"* — tells you whether anything has drifted (`os-health`)
  - *"level up"* — turns one weekly chore into something automatic (`level-up`)
  - *"make this a command"* — creates a new one of these (`create-skill`)
  - *"why didn't you find that?"* — when something was missed, fixes the cause rather than the
    symptom (`backtrack`)

  The short name in brackets works too, if you prefer typing one word.

### Honest boundaries

- **Tested** in Claude Code — install and setup run end to end, from a cold paste to a finished
  workspace.
- **The structure and the rules travel to other agents.** Everything here is plain markdown, and
  `AGENTS.md` is the file coding agents read by convention. Measured in **Codex** (v0.146.0): a fresh
  session asked "what should I focus on today" opened the three `me/` files on its own and answered
  from them, three runs out of three. **Cursor and Gemini follow the same convention but have not been
  measured** — treat them as likely, not proven.
- **Five of the six commands work in any agent; one does not.** Each is a written procedure in
  `system/procedures/`, which `AGENTS.md` points any agent at. The exception is *"make this a
  command"* — it writes a Claude Code skill file, so it only means anything in Claude Code, and **any
  command you create yourself is likewise Claude Code only.** Everything else — who you are, what you
  are working toward, the four loops, the filing rules and the other five commands — travels.
- **No integrations in this version.** No mail, no calendar, no cloud. Just a folder of text.

---

## Licence and author

**MIT** — free to use, modify and distribute, **including commercially**, for anyone, with no fee and
no permission needed. The full text is in [LICENSE](LICENSE).

**MIT** — можно свободно пользоваться, изменять и распространять, **в том числе в коммерческих
целях**, кому угодно, бесплатно и без отдельного разрешения. Полный текст — в файле
[LICENSE](LICENSE).

Built by **George Kachanouski**.

- LinkedIn — https://www.linkedin.com/in/georgekachanouski
- Facebook — https://www.facebook.com/george.kachanouski
