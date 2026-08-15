# OS_Nowa

**Личная операционная система для работы с ИИ-агентом.** · **A personal productivity operating
system any coding agent can run.**

---

## Установка

Откройте Claude Code (или другого агента) и вставьте этот текст одним сообщением:

```
Set up OS_Nowa for me.

1. Ask me where to put it. If I don't care, use a folder called "os-nowa" in my home directory.
2. Get the files into that folder. If git is available:
       git clone https://github.com/surfstories/os-nowa.git os-nowa
   If git is NOT installed, don't try to install it — download the archive instead:
       curl -L https://github.com/surfstories/os-nowa/archive/refs/heads/main.tar.gz -o os-nowa.tar.gz
       tar -xzf os-nowa.tar.gz
   That unpacks a folder named "os-nowa-main". Rename it to "os-nowa" and delete the .tar.gz.
   If neither works, tell me plainly what failed and what to try — don't guess.
3. Make that folder your working directory, read AGENTS.md in it, and start onboarding by
   following system/procedures/onboarding.md.

Talk to me in the language I am writing to you in, from your very first reply.
```

**Команда на английском — это нормально.** Ассистент прочитает её и заговорит с вами на вашем языке
с первого же ответа. Ничего устанавливать не нужно, ключи и пароли не нужны.

*The command block is in English on purpose — it is one copy, so it cannot drift between the two
halves of this page. Paste it as-is; the agent will reply in your language.*

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
- **Шесть команд:** `onboard` — настройка · `explain` — объяснит, как всё устроено, в любой момент ·
  `os-health` — проверит, не разъехалось ли что-то · `level-up` — раз в неделю превращает рутину в
  автоматику · `create-skill` — новая команда · `backtrack` — если агент что-то не нашёл, чинит
  причину, а не симптом.

### Честные границы

- **Проверено** в Claude Code — установка и настройка пройдены целиком.
- **Файлы системы работают в любом агенте**, потому что это просто markdown: `AGENTS.md` читают и
  Codex, и Cursor, и Gemini.
- **Но команды, которые вы создадите сами, работают только в Claude Code.** Шесть встроенных команд
  выше — это правила в `AGENTS.md` и `system/`, они работают везде. А новая команда, созданная через
  `create-skill`, — это файл в `.claude/skills/`, который читает только Claude Code. Если вы
  откроете папку другим агентом, ваши собственные команды не сработают. Всё остальное — сработает.
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
- **Six commands:** `onboard` — setup · `explain` — explains how any of this works, at any moment ·
  `os-health` — checks whether anything has drifted · `level-up` — turns one weekly chore into
  something automatic · `create-skill` — a new command · `backtrack` — when the agent fails to find
  something, it fixes the cause rather than the symptom.

### Honest boundaries

- **Tested** in Claude Code — install and setup run end to end.
- **The system's files work in any agent**, because they are just markdown: `AGENTS.md` is read by
  Codex, Cursor and Gemini alike.
- **But skills you create yourself are Claude Code only.** The six commands above are rules living in
  `AGENTS.md` and `system/`, and they work anywhere. A new command made with `create-skill` is a file
  in `.claude/skills/`, which only Claude Code reads. Open the folder in a different agent and your
  own commands will not fire. Everything else will.
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
