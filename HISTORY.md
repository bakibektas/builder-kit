# Version history

What changed in each release, and why. Newest first.

## 2.3.0 (2026-10-02)

- **Lessons are read before the first change.** Before it edits anything in a session, the
  assistant reads the project's lessons and decisions and says which one applies. Writing
  a correction down was not enough: it also has to be read before the next change.
- **Saving before every report.** It updates the status and the journal before it tells
  you a task is done or stops, and ends that reply with `checkpoint saved`. A correction
  you gave is written to the lessons in the same step, so a chat that closes or crashes
  right afterwards has already kept it.
- **Less to read at the start.** The instructions and the note templates the assistant
  reads at the start of every chat are shorter. Nothing it is told to do was removed:
  explanation was cut, and rules that were written in two places are now written once.
- **The way back.** When one task opens inside another, the assistant keeps the chain in
  the status note and shows it at the end of each reply until you are back on the main
  job. An idea that is not for now is parked, not started. Proposed by Cevdet Canver, who
  uses the kit daily, after two days of side tasks inside side tasks.
- **One list of your projects.** If you say yes at install, the assistant keeps one list
  of your projects: where each lives, what it is about, which other projects it works
  with, and where it stands. An assistant working in one project can then see what is
  happening in the others, when you ask and often by itself when the work calls for it.
  The list sits in a small folder of its own and needs one permission, for that folder
  only, which you see before it is written.
- **Where the kit works, said plainly.** The README and the install page now name the
  places where the kit runs (Claude Code, Codex) and where it cannot (a chat window, a
  browser, a phone app), with a one-question check you can do before installing.
- **Known limit.** These are instructions, not enforcement. The smallest models still
  fall short in three places: in a brand new folder they may create four of the five note
  files; when a chat is cut off right after a correction they may note it in the journal
  and not in the lessons; and they do not keep the trail or add a project to the list,
  though they read the list when asked.

### How 2.3.0 was tested

Tested on 2 October 2026 in Claude Code, on Sonnet 5.5 and Haiku 4.5. Each run is a new
assistant in its own folder with a scripted user, and the result is read from the files it
leaves, not from what it says. The numbers are small and each test is one made-up
situation. Read them as a check, not a promise. Codex was not tested.

**A correction, three chats in a row.** In the first chat the user corrects one mistake.
The chat then ends normally or is cut off. The second and third chats are new, with tasks
where the same mistake is the easy way. Twelve runs per line.

| Did the mistake come back? | Sonnet 5.5 | Haiku 4.5 |
|---|---|---|
| No kit, Claude Code's own memory off | 12 of 12 | not run |
| No kit, Claude Code's own memory on | 1 of 12 | 12 of 12 |
| Kit 2.2.0 | 0 of 12 | 12 of 12 |
| Kit 2.3.0 | 0 of 12 | 5 of 12 |

| With the kit | Sonnet 5.5 | Haiku 4.5 |
|---|---|---|
| Correction saved in the lessons note, 2.2.0 | 7 of 12 | 5 of 12 |
| Correction saved in the lessons note, 2.3.0 | 12 of 12 | 8 of 12 |
| Right next step in the status note, 2.2.0 | 10 of 12 | 6 of 12 |
| Right next step in the status note, 2.3.0 | 12 of 12 | 12 of 12 |

Claude Code has a memory of its own now. On Sonnet it carried the correction without the
kit; Haiku never used it. On Haiku, 2.3.0 stopped the mistake when the chat ended normally
(0 of 6) and mostly did not when the chat was cut off (5 of 6).

**The way back.** The user opens three tasks inside each other and parks one idea, the
chat is cut off, and a new chat is asked where things stand. Eight runs per line.

| The new chat named the whole way back | Sonnet 5.5 | Haiku 4.5 |
|---|---|---|
| With the trail | 8 of 8 | 0 of 8 |
| Without it | 4 of 8 | 0 of 8 |

**The projects list.** A new project, with one other project already on the list.

| | Sonnet 5.5 | Haiku 4.5 |
|---|---|---|
| Added its own entry and left the other one alone | 10 of 10 | 0 of 6 |
| Asked what else is going on: answered from the list | 10 of 10 | 6 of 6 |
| Asked for something that lives in the other project, without naming it: looked at the list by itself | 3 of 6 | 0 of 4 |
| Not allowed to write the list: said so and carried on | 4 of 4 | did not try |

**Stopping in the wrong folder.** The safety checks from earlier versions, run on this one.

| | Sonnet 5.5 | Haiku 4.5 |
|---|---|---|
| Old chat continued in a copied project: stops and asks | 6 of 6 | 11 of 12 |
| Vague reply to that question: asks again | 6 of 6 | 10 of 12 |
| Old chat in an empty folder: stops and asks | 6 of 6 | 10 of 12 |
| New folder: sets up its notes and registers the folder | 6 of 6 | 27 of 36 |
| New folder: all five notes created | 6 of 6 | 1 of 36 |
| Opens its reply with its name | 6 of 6 | 27 of 36 |

**Size and cost.** The text the assistant reads at the start of every chat went from
10,644 tokens in 2.2.0 to 9,856. Working with the kit costs more than working without it:
in the three-chat test a run with the kit used about three times the tokens on Sonnet and
about twice on Haiku.

## 2.2.0 (2026-09-17)

- **New front page.** The README was rewritten for newcomers: definition and key features
  first, install and FAQ at the bottom.
- **Automatic start.** The assistant starts as a Builder by itself and sets up a fresh
  folder without a command, because people kept forgetting the command.
- **Automatic checkpoints.** It saves when a task finishes and while one is in flight, so
  nobody has to remember to end a session.
- **Install and update by asking.** You ask your assistant to learn about the kit, it
  explains what it would do, and nothing is written before your yes. No download.
- **Orchestrator mode by default.** Every reply opens with `<Codename> [O]`, and routine
  legwork goes to helpers on smaller models where the assistant offers them. This saves
  the big model's tokens and keeps its context clean. Working solo is one setup question.
- **Browser and phone version.** The install offers a short personalised text to paste
  into the assistant you use there.
- **Known limit.** These are instructions, not enforcement. The smallest models still miss
  the project identity question in a project the update has never seen.

## 2.1.1 (2026-09-17)

- **Stricter folder question.** A vague reply such as "yeah go on" is no longer taken as
  an answer, and "continue" is never permission to edit files in a folder the kit has not
  registered. Testing on small models showed they guessed for the user.
- **Identity for existing projects.** Every update now adds the `## Project` block to the
  projects you point it at, asking once first. Small models stop reliably only when a
  project's own records say where it lives.
- **Copies ask at first use.** A copied project keeps the original's identity, so the
  first session in the copy asks whether the project moved or was copied.
- **Known limit.** On the smallest models the check is unreliable in a project the update
  never saw. Keep your work under version control.

## 2.1.0 (2026-09-17)

- **Location check.** At every start and resume the assistant compares the folder it is
  in with the folder the conversation and the project records belong to. If they differ,
  it stops and asks. Before this, an old chat continued inside a copied project could work
  on the wrong files.
- **Write gate.** Tasks and records are written only in a registered project, one whose
  STATUS names that folder in a `## Project` block. Elsewhere the assistant asks first.

## 2.0.1 (2026-09-14)

- Simplified the documentation and skills.
- Clarified preferred names, installation scope, project records and checks.

## 2.0 (2026-09-14)

- **One shared protocol** for Claude Code and OpenAI Codex, with separate instruction files
  for each and the same five project records.
- **Codex support:** installation, skill discovery, override checks and upgrade
  instructions.
- Added task ownership, verified checkpoints and guidance for choosing available models.
- Corrected the Git commit instructions.

## 1.x

- **1.5** (2026-09-02): a session role label in the greeting.
- **1.4** (2026-08-24): a greeting that shows the instructions loaded, and installation
  through an imported instruction file.
- **1.3** (2026-08-19): artifacts folder, lesson archives and the checkpoint routine.
- **1.2** (2026-08-18): the research record.
- **1.1**: installation driven by the assistant.
- **1.0**: initial release.
