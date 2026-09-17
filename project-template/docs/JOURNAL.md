# Journal

<!--
HOW TO USE THIS FILE

Append-only session log, newest first. One heading and five fields per working session.

- At session start read the TOP entry only. Do not read the rest of the file.
- At session end prepend one new entry above the others.
- Never edit or delete a past entry. If something recorded was wrong, say so in a new entry.
- Cap: ~150 lines. When it grows past that, MOVE the oldest entries: cut them from here and
  paste them into `docs/journal-archive.md`, creating that file if needed. Move content
  between files; never delete a file, and never drop an entry on the floor.
- Keep entries tight. Detail belongs in the deliverable, not in the log.
- Refer to people by role, never by name. No personal data of any kind.

Entry format:

### YYYY-MM-DD: <model used>, <session codename>
- **Summary:** <what actually got done, one or two sentences>
- **Decisions:** <decisions made, or "none"; anything direction-changing also goes in DECISIONS.md>
- **Blockers:** <what stopped progress, or "none">
- **Files/assets:** <files, documents, scenes, prefabs or artboards created or changed>
- **Next:** <the recommended next step for whoever picks this up>

Delete the EXAMPLE blocks once real entries exist. Two are shown (one research project, one
prototype project) to make the shape clear. Only one project's entries live in one file.
-->

<!-- EXAMPLE, research project: delete this block

### 2026-07-30: workhorse model (planned on the top tier)
- **Summary:** Clustered 12 session note sets into 5 themes; drafted finding statements for the top 3.
- **Decisions:** Dropped the "pricing confusion" theme: 2 of 12 mentions, too thin to lead with.
- **Blockers:** Cannot quantify drop-off without the funnel export; requested from the analytics lead.
- **Files/assets:** findings-draft.md, themes-matrix.md, docs/STATUS.md
- **Next:** Write the evidence slide for finding 1, then get a sanity read from the design lead.

-->

<!-- EXAMPLE, prototype project: delete this block

### 2026-07-30: workhorse model
- **Summary:** Built the grapple-traversal prototype scene: hook raycast, rope constraint, and a 3-platform test course.
- **Decisions:** Rope as a spring joint rather than scripted arcs: the emergent overshoot is the interesting part.
- **Blockers:** None. Controller feel is untested outside keyboard input.
- **Files/assets:** Scenes/Grapple_Test.unity, Prefabs/Hook.prefab, Scripts/GrappleController.cs
- **Next:** Test with a gamepad, then time 5 runs of the course to get a baseline before tuning.

-->

<!-- Older entries: see docs/journal-archive.md -->
