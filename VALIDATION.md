# Validation contract

BuilderKit is an instruction package. Static checks establish package consistency;
behavioral scenarios establish whether an agent follows it. Neither proves universal
compliance. Do not report an unrun scenario as passed.

## Package checks

- Both native entries point to builder-protocol.md; INSTALL maps PROTOCOL.md there.
- Project CLAUDE.md points to the shipped project AGENTS.md.
- Seven skill directories each contain SKILL.md with matching name and a non-empty
  description. Skill bodies work from their installed location without links back into
  an unavailable kit checkout.
- Markdown links to shipped files resolve. Version markers agree. No private absolute
  paths, frozen vendor tier requirements or obsolete commit syntax enter the package.
- Global and project-only installations preserve existing content and provide a complete loading chain.
- Keep the package standalone: instructions and skills use the five project files and
  artifacts/. No external service, private deployment or central task registry is required.
- Run `git diff --check` and review the exact changed paths.

When the Codex skill-creator validator is available, run its quick_validate.py on each
skills/* folder. It checks metadata, not behavioral correctness.

## Behavioral acceptance scenarios

Use disposable project directories and explicitly isolated test configuration. Never
overwrite a real user home or consume paid APIs for a smoke test.

| Scenario | Expected observable outcome |
|---|---|
| Fresh Codex | AGENTS + shared protocol identified; seven skills discoverable; session-start reads/scaffolds only this project's memory |
| Fresh Claude | Native entry loads protocol; project CLAUDE reads AGENTS; same records used |
| Existing task in startup request | Context restored, task owner recorded in STATUS and work continues without another approval gate |
| Existing active collaborator | Their task status and uncommitted edits stay untouched |
| Checkpoint then resume | Identity, exact task and next step survive; checkpoint did not close the task |
| File write fails | No success claim; exact unsaved update and handoff reported |
| Codex override shadows entry | Installer identifies override, preserves it, reports discovery unresolved |
| Repeat identical install | No changes, duplicate read lines or extra backups |
| Custom instruction or modified skill | Concrete merge/conflict presented; unrelated content preserved |
| 1.x direct update | Personal block preserved verbatim; entry + shared protocol correctly deployed |
| 1.x imported update | Custom native content preserved; one reviewed reference change; personal block moved into adapter |
| Project-only installation | Local AGENTS explicitly reads local protocol; local skills discovered; globals untouched |
| Protected instruction file | Target preserved; unresolved conflict reported without changing permissions |

Record which host/version and scenarios were actually exercised in the release review.
Use current primary documentation for claims about host behavior; keep local deployment
observations distinct from general product guarantees.
