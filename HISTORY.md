# Version history

What changed in each release, and why. Newest first.

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
