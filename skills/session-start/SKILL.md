---
name: session-start
description: Check that the session is in the right project folder, then restore that Builder project's context and session identity from its files. Use at the start or resume of a working session, or when asked where work left off.
---

# session-start

Read the installed Builder protocol. Read the project's own instructions at step 4, after
the location check. The user's existing task authorization remains valid during this
startup workflow, but only for the folder where it was given.

1. Retain your codename when resuming; otherwise announce a two-word codename.
2. **Location check. Do this before reading any other project file.**
   a. HERE = the absolute path of the nearest folder, at or above the current working
      directory, that contains `docs/STATUS.md`; if none, the working directory itself.
      Take the working directory from the host's current environment information or a
      `pwd` / `Get-Location` command, never from older messages.
   b. THERE = the project folder this conversation's earlier messages belong to: the
      project root you reported before, or the folder of the files you read or edited.
      Relative paths such as `firmware/main.c` name no folder: with only those, the
      folder is unclear, even if the same files exist in HERE.
      If the conversation has no earlier messages, THERE is unknown.
   c. Read HERE's `docs/STATUS.md` only. RECORD = its `## Project` block
      (`Project id`, `Project root`).
   d. Compare paths, ignoring letter case on Windows and macOS, slash direction and a
      trailing slash. Use the first row that matches:
      - THERE is a folder outside HERE: say "This conversation belongs to
        `<THERE>`. You are now in `<HERE>`. Start fresh here, or switch back to `<THERE>`?"
      - Earlier messages exist but their folder is unclear: say "I can't tell which folder
        this conversation belongs to (`<what you can see>`). You are now in `<HERE>`.
        Start fresh here, or tell me which folder this work belongs to?"
      - RECORD's root is a different folder from HERE: say "This folder's records say the
        project lives at `<RECORD root>`, but you are in `<HERE>`. Is this the same
        project moved, or a copy for separate work?"
      - RECORD or `docs/STATUS.md` is missing: HERE is not a registered project. Go to
        step 3 and follow the write gate.
      - Otherwise the check passes.
   e. After asking, **stop and wait**. Until the user answers, write nothing, create no
      tasks, change nothing, and read no file outside HERE. Do not continue a task from
      earlier in the conversation. An answer must pick one option or name a folder. If
      the reply is "yes", "ok", "go on", "continue" or anything else that does not
      choose, change nothing and ask the same question again with the options numbered.
      Never choose for the user.
   f. On "start fresh here", say "I will treat what I remember about `<THERE>` as
      background only. I will not act on its tasks, plans or file paths." Announce a new
      codename. Then repeat step d with THERE treated as unknown, and use only HERE.
      On "switch back", say "Reopen this conversation from `<THERE>` and run
      session-start again," then stop. On "moved", change only the `Project root` line
      to HERE. On "a copy", register HERE as a new project (step 3) with a
      `**Copied from:** <old id> at <old root>` line, and announce a new codename.
      Copied tasks, journal entries and next steps are the original's history, even
      where they name your codename: report them as background and claim none of them
      until the user chooses one.
3. **Write gate.** HERE is registered only if its Project block names HERE as root (or
   reads `any clone of this repository`). If it is not registered, do not create tasks
   or write any record in it. First say: "I'm about to `<what you will write, with counts>`
   for `<project you believe this is, or "this folder">` in `<HERE>`, which isn't set up
   as a Builder Kit project. Set it up, or stop?" On "set it up", create only the missing
   records from the project template. Set Project id to HERE's folder name plus today's
   date, and Project root to HERE. On "stop", write nothing. If records exist without a
   Project block (older kit), ask: "This folder has Builder records but no project
   identity yet. Add one for `<HERE>`?"
4. Read the project instructions. Read `docs/STATUS.md` in full and only the latest
   `docs/JOURNAL.md` entry. Search `docs/DECISIONS.md`, `docs/LESSONS.md` and
   `docs/RESEARCH.md` for the current task's keywords. Codex uses project AGENTS.md;
   Claude uses CLAUDE.md (which may point to the same AGENTS.md). Preserve existing
   instructions.
5. Inspect relevant task ownership and changed files. An in-progress task alone is not
   evidence of abandonment. Leave active owners alone; reconcile only your own work or
   work demonstrably abandoned and authorized for takeover.
6. Report `Project: <id> at <HERE>`, codename, loaded sources, last checkpoint, blockers
   and next action. Record the task and owner in STATUS before edits. Continue an already
   requested task; if the user asked only for orientation, report the recommendation
   without inventing new work.

After the assistant shortens its conversation context (compaction), run step 2 again,
then read the saved checkpoint and current project records, and continue the same task
and codename.
