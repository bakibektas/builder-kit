# The Builder Kit

Version 1.4 (2026-08-24). Version history at the end of this file.

A portable working system for an AI assistant: project memory in five plain files, seven
session rituals, a model ladder, and a canary that proves the protocol was actually loaded. It
turns an assistant that begins every conversation knowing nothing into a partner that picks up
where the last session stopped, writes down every correction it receives, and hands off cleanly
to the next session. Everything is plain text: nothing is installed, nothing runs in the
background, nothing calls out to a service.

It is for anyone who works with an assistant most days and is tired of re-explaining the same
project: solo developers, designers, founders, researchers, writers. It ships wired for Claude,
in the terminal or the browser. Other assistants are the direction, not the current state; see
`ROADMAP.md`.

## Install

1. Get the kit: `git clone https://github.com/Threchette/builder-kit.git`, or use the Code
   button and Download ZIP, then unzip it somewhere convenient.
2. Open your AI agent in that folder: a terminal opened there running `claude`, or the folder
   opened in your editor with the Claude extension.
3. Say this:

> Install this kit for me. Follow INSTALL.md.

That is the install. The agent interviews you for the four things that are actually yours,
copies the protocol and the rituals into place, checks with you before touching anything that
already exists, and reports what it did. The detail is in "Setup, path A" below, and the manual
route is in "Setup, path B" for anyone who would rather do it themselves.

## Read before you run

`INSTALL.md` is written for the agent, but it is meant to be read by you first. It is short,
it is plain English, and it is the whole contract. What an install does:

- Copies files into your assistant's user folder (`.claude` in your home directory) and, if you
  ask for it, into one project folder that you name.
- Asks before touching anything that already exists, showing you what is there next to what the
  kit would write, and waits for your answer.
- Backs up rather than overwrites, with the date in the backup file name.
- Never deletes anything.
- Never touches credentials, keys, or any setting the file does not name.
- Never reaches the network. There is nothing to fetch: the kit is the folder you cloned.

If an agent proposes something outside that list, it has left the file, and stopping it is the
right move.

## Updating

Run `git pull`, then say the same sentence: "Install this kit for me. Follow INSTALL.md." The
installer detects the version you are already running, carries your personalized blocks across
untouched, replaces the shared protocol and the seven rituals, leaves every project's `docs/`
folder alone, and reports what changed between your version and this one.

## Why it works this way

The philosophy in one screen: a Claude session begins knowing nothing, so a project keeps its
memory in files instead of in scrollback. A Builder announces itself with a codename, reads
the project's state, does the work as an owner would, writes down every correction it receives,
verifies anything it is about to assert, and closes every loop before it signs off. Importance
buys tighter verification, never a bigger model. Nothing written is nothing remembered.

If you read one other file, read `ETHOS.md`. It is the reason the rest of this exists.

## What is in this folder

| File | What it is |
|---|---|
| `README.md` | This guide: setup, personalization, rhythm. |
| `INSTALL.md` | Instructions written for an AI agent, so it can install the kit for you. See "Setup, path A". |
| `ROADMAP.md` | Where the kit is going: direction, not dates. |
| `ETHOS.md` | The Builder manifesto. The philosophy, in nine parts. Read it once. |
| `PREFERENCES.txt` | Text for your claude.ai personal-preferences field. Personalize before use. |
| `global/CLAUDE.md` | The working protocol: identity, model ladder, docs convention, conventions, standards. Drops into your user-level Claude folder. |
| `project-template/` | A ready-to-copy project skeleton: a project `CLAUDE.md`, the five `docs/` files, and an `artifacts/` folder for deliverables. |
| `skills/` | Seven session rituals: `session-start`, `session-end`, `next-task`, `log-lesson`, `premortem`, `research-method`, `checkpoint`. |

## The idea in one paragraph

Claude starts every conversation with no memory of the last one. So each project keeps its
memory in five small files under `docs/`: **STATUS.md** (what is happening now, plus the task
list), **JOURNAL.md** (one five-line entry per session, newest first), **DECISIONS.md** (only
decisions that changed direction, each with a mandatory why), **LESSONS.md** (what went
wrong and the rule that prevents it recurring), and **RESEARCH.md** (what was found out, with
sources and dates, so nobody researches the same question twice). A session opens by reading
STATUS in full and the newest journal entry, and closes by updating them. Splitting it five
ways is deliberate: you load only the small volatile file every time and search the others
when a task actually needs them, which keeps sessions cheap.

## How memory works

Three layers, each with one job. Claude keeps its own working memory of your sessions
automatically: that layer is personal and needs nothing from you. `docs/LESSONS.md` is the
durable record: at session end the lessons worth keeping are written there deliberately, and
because the folder is committed, every future session and every collaborator inherits them.
When a lesson has proved itself as a standing rule, it graduates to a one-line entry in the
project's `CLAUDE.md`, which is read at the start of every session, so that stays short.

The input that feeds all of it is your corrections. Every time you tell a Builder it got
something wrong, that correction gets written down with a mitigation before the work continues.
It is the one habit that makes the system improve on its own.

## Setup, path A: let a Builder install it (recommended)

This is the install from the top of this file, in full. Open Claude in the kit folder and say:

> Install this kit for me. Follow INSTALL.md.

One line per surface, whichever you use: in a terminal opened at the kit folder, run `claude`;
in VS Code, open the kit folder and use the Claude extension there.

It announces a codename, reads the kit including `ETHOS.md`, then interviews you for the four
things that are actually yours: how to address you, your role, your tone, your language. It
fills those into the two personalized files, copies the protocol and the seven rituals into
place, checks with you before touching anything that already exists, verifies what it wrote,
and reports back signed with its codename. One step stays yours: pasting your preferences text
into claude.ai settings, which lives in your account rather than on your machine. Windows or
macOS makes no difference on this path, because the agent resolves the paths itself.

## Setup, path B: by hand, with the Claude Code CLI

The same install, done yourself. It also doubles as the reference for what path A does.

1. Confirm the CLI is there. Windows: open PowerShell. macOS: open Terminal. Run
   `claude --version`. If it prints a version, continue. If not, use the browser path below.
2. Find your Claude folder and create it if it does not exist.
   Windows: `C:\Users\<your-username>\.claude`. macOS: `~/.claude`.
3. Personalize `global/CLAUDE.md` first (see "Make it yours"), then copy it into that folder
   as `CLAUDE.md`. It is read at the start of every session, in every project.
4. Copy the whole `skills` folder into the same `.claude` folder, so you end up with
   `.claude/skills/session-start/SKILL.md` and six siblings. Keep the folder names exactly as
   they are: the folder name is the skill name.
5. Personalize `PREFERENCES.txt`, then paste it into claude.ai under Settings, personal
   preferences. The CLI does not read that field but the browser does, and most people use both.
6. Set up a project: copy the contents of `project-template/` into a project folder you
   actually work in. That gives you a project `CLAUDE.md` and a `docs/` folder with five files.
   Fill in the project name and the project-specific notes. Or skip the copy: in a folder with
   no `docs/`, `session-start` detects the fresh project and creates the files itself. The
   template folder just shows you what you will get.
7. Open each `docs/` file, read the instruction block at the top, and delete the blocks marked
   EXAMPLE once you have real content. Leave the instruction blocks: Claude reads them.
8. If the project is a git repository, commit the `docs/` folder deliberately. It is meant to
   be shared with your future self and with anyone else on the project, and committing is what
   turns the lessons file into a durable record instead of a local note.
9. Start working: open a terminal in the project folder, run `claude`, and say `session-start`.
   It should announce a codename, read STATUS, report where things stand, and recommend a next
   action. Close with `session-end`.
10. Repeat step 6 for each new project. One `docs/` folder per project.

## Setup in the browser only, no terminal

1. Paste your personalized `PREFERENCES.txt` into Settings, personal preferences. It then
   applies to every conversation on the account.
2. Create a Project for each real body of work. Projects are what give you persistent context
   in the browser.
3. Paste your personalized `global/CLAUDE.md` into the project's custom-instructions field. If
   it is rejected as too long, drop the section 4 bullets you need least; keep sections 1, 3
   and 5.
4. Upload the five `docs/` files into the project's knowledge, and add one line to the custom
   instructions: "The files STATUS.md, JOURNAL.md, DECISIONS.md, LESSONS.md and RESEARCH.md in
   this project's knowledge are the working memory described in section 3. Read STATUS.md at
   the start of every conversation."
5. Rhythm: start each conversation with "session-start", end with "session-end".
6. The one manual step. Claude cannot edit a project knowledge file. At session end it outputs
   the updated content; you paste it into your local copies and re-upload, replacing the old
   versions. It takes about a minute, and the whole system depends on that habit.
7. Skills in the browser depend on your setup. If they are not available, upload the seven
   `SKILL.md` files as project knowledge instead and add: "When I name a ritual (session-start,
   session-end, next-task, log-lesson, premortem, research-method, checkpoint), follow the
   matching SKILL.md in this project's knowledge."

## Make it yours

Two files contain personal content, and both mark it clearly with `PERSONALIZE` markers.
Everything outside the markers is the shared protocol: leave it alone and every Builder you
work with behaves the same way.

1. `PREFERENCES.txt`: replace the four paragraphs between `PERSONALIZE: START` and
   `PERSONALIZE: END` with your own role, form of address, tone and language. Delete the marker
   blocks before pasting into claude.ai.
2. `global/CLAUDE.md`, section 1: replace the four bullets between the `PERSONALIZE` comments
   with the same information. Leave the rest of section 1 and all of sections 2 to 5.

That is the whole personalization surface. Two minutes.

**On language.** The kit's own files stay in English: the structure, the file names, the
instruction headers, the section titles. That is what keeps it shareable and keeps the headers
matching the protocol that describes them. Your language preference governs everything the
Builder produces as content: the conversation, the reports, and the journal, decision and
lesson entries it writes into `docs/`. Set it once in the `Language:` line and it holds.

The kit ships with a solo indie game developer as the worked example. Yours might read:

- *Product designer:* "Role: product designer working across brand and interface. I judge work
  by craft, so show me options rather than one answer. Address me as <name>. Tone: direct and
  opinionated; argue for a direction and say what you would cut. Language: English."
- *Founder or PM:* "Role: founder. I need decisions, risks and dates, not implementation
  detail. Address me as <name>. Tone: crisp, front-load the answer, flag anything that slips.
  Language: English."
- *Turkish-speaking indie developer:* "Rol: bağımsız oyun geliştiricisi; tek kişilik ekip, 2B
  bir roguelike üzerinde çalışıyorum. Bana 'Deniz' diye hitap et. Ton: doğrudan, samimi,
  profesyonel; bir yardımcı değil, deneyimli bir ortak gibi davran. Dil: Türkçe. Türkçe konuş
  ve günlük, karar ve ders kayıtlarını Türkçe yaz. Komutları, dosya adlarını ve kutudan çıkan
  dosya başlıklarını olduğu gibi bırak."

That third one is the shape to copy if you do not work in English: the block itself is written
in your language, so the Builder converses and writes its `docs/` entries in Turkish, while the
file names, the shipped instruction headers and the shell commands stay exactly as they came.

## The working rhythm

- **Open with `session-start`.** You get a codename, a one-line account of where things stand,
  the open P0 and P1 tasks, any orphaned work cleaned up, and one recommended next action. Then
  it stops and waits, because you may have a priority that never reached the file.
- **Work in fresh chats, one per task.** Context is re-read on every turn, so a long thread
  gets more expensive with every message. The `docs/` files carry the continuity: that is what
  they are for. Say `next-task` to pick up the next thing by priority.
- **Correct freely.** A correction is not friction, it is the input the system runs on. Say
  `log-lesson` if you want one captured on the spot.
- **Before anything expensive or irreversible, say `premortem`.** You get the plan move by
  move with fork triggers and abort criteria, and a go / no-go verdict at the end.
- **For a real question, say `research-method`.** Several deliberately disagreeing lenses, then
  a synthesis with an explicit contradiction map instead of a comfortable average. The verdict
  lands in `docs/RESEARCH.md` with its sources before you see the report, so the next session
  searches that file instead of buying the same answer again.
- **When the conversation is filling up, say `checkpoint`.** STATUS is rewritten to the exact
  current state, a checkpoint journal entry goes in, drafts are saved, and the work continues.
  Nothing is closed. After a compaction, the first thing read is STATUS.
- **Close with `session-end`.** Tasks closed, STATUS rewritten, a journal entry prepended,
  decisions and lessons appended, deliverables saved into `artifacts/`, and a Done / Files /
  Blocked / Next report.

Keep STATUS under about 40 lines and JOURNAL under about 150. When JOURNAL passes that, the
oldest entries move into `docs/journal-archive.md` rather than being deleted.

## Where this came from

The Builder Kit distils several years of daily practice running a multi-agent working system,
where many sessions across several model tiers worked on one continuous body of work and had
to hand off cleanly to each other. Everything that depended on bespoke infrastructure has been
stripped out. What is left is the part that turned out to be portable: the five files, the
ladder, the rituals, and the ethos that holds them together. It is deliberately plain text, so
it will still work when the tooling around it has changed twice.

## Contributing

Issues and Discussions are open, and reports of the "this did not survive contact with my
setup" kind are the most useful thing you can send. Pull requests are welcome, and the protocol
is opinionated: improvements to clarity land fast, changes to the philosophy get discussed
first. If your change touches what a Builder is rather than how clearly it is described, open an
issue before you write the patch, so nobody spends an evening on a direction the kit is not
going.

Where the kit is going next is in `ROADMAP.md`. Licensed MIT: see `LICENSE`.

More about the thinking: https://baki.io/builder-kit

## Version history

- 1.4 (2026-08-24): the opening address became an explicit canary rule proving the protocol is loaded, and a missing
  greeting triggers a re-read; installing onto an already-customized setup can now keep it untouched via a one-line import.
- 1.3 (2026-08-19): deliverables get a committed `artifacts/` folder; superseded lessons move to
  an archive; memory is repository-only; a new `checkpoint` ritual saves state before compaction.
- 1.2 (2026-08-18): research record added. `docs/RESEARCH.md` joins the project files so
  findings survive sessions, and the session rituals search and update it.
- 1.1: agent-driven installation added (`INSTALL.md`). Manual setup became the secondary path.
- 1.0: initial release.
