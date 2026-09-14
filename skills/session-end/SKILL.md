---
name: session-end
description: Close owned Builder tasks, persist deliverables and lessons, and save a verified handoff in the configured backend. Use when wrapping up a working session.
---

# session-end

Use the backend declared by the project. The user controls the scope; this ritual
does not itself authorize publishing, pushing or deleting files.

1. Reconcile only tasks you own. Mark verified work done, blocked work with its actual
   reason, and unfinished work todo with an exact resume step. Preserve other owners.
2. **Files:** update STATUS, prepend a JOURNAL entry (date/model/codename plus Summary,
   Decisions, Blockers, Files/assets, Next), and record relevant decisions and research.
   Save deliverables in artifacts/. Archive older entries without losing them.
3. **Collective:** update tasks through MCP, save/revise deliverables through the artifact
   tools, log the action, and call agent_checkpoint_session with the actual session ID
   and absolute repo. Include unfinished work, decisions, checks and handoff. Inspect
   responses for errors; report any unsaved state. Do not write competing docs/ memory.
4. Review corrections and useful discoveries. Search and merge lessons in the selected
   backend with actionable mitigations. Promote proven recurring rules through managed
   rule tools in Collective mode; in files mode update the canonical project instruction
   file rather than duplicating rules across both harness files.
5. Inspect the diff and validation results. If a commit is in scope, add new files by
   explicit path. For exclusively owned files use `git commit -m "<message>" -- <paths>`.
   For mixed ownership, stage only your hunks and commit without a pathspec. Use a distinct
   committer and a final `Codename: <Two Words>` trailer. Recheck the resulting commit.
6. Clean only your own known scratch files within verified project paths when appropriate.
   Never sweep a shared .tmp directory or another contributor's edits.

Report what was delivered, where it lives, what was checked, limitations, persistence
failures if any, and what remains. Distinguish local edits, committed work and published
work. Do not call the task complete merely because the session is ending.
