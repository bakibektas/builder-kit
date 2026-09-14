# How to check the kit

BuilderKit is a set of instructions. File checks show whether the package is consistent;
tests in an assistant session show whether it follows the instructions in that scenario.
Neither guarantees that every session will follow every rule. Do not report a scenario
as passed unless you ran it.

## Package checks

- Both assistant instruction templates point to builder-protocol.md; INSTALL copies
  PROTOCOL.md to that name.
- Project CLAUDE.md points to the shipped project AGENTS.md.
- Seven skill directories each contain SKILL.md with matching name and a non-empty
  description. Skill bodies work from their installed location without links back into
  an unavailable kit checkout.
- Markdown links to shipped files resolve. Version markers agree. No private absolute
  paths, frozen vendor tier requirements or obsolete commit syntax enter the package.
- User-wide and project-only installations preserve existing content and give the
  assistant a file reference to every required instruction file.
- Personal preferences ask for the name or nickname the assistant should use. The
  README keeps release details together in its version history without a duplicate 2.0 section.
- Keep the package standalone: instructions and skills use the five project files and
  artifacts/. No external service, private deployment or central task registry is required.
- Run `git diff --check` and review the exact changed paths.

When the Codex skill-creator validator is available, run its quick_validate.py on each
skills/* folder. It checks metadata, not behavioral correctness.

## Scenarios to test in an assistant session

Use disposable project directories and explicitly isolated test configuration. Never
overwrite a real user home or use paid APIs for a basic installation check.

| Scenario | Expected observable outcome |
|---|---|
| Fresh Codex | AGENTS + shared protocol identified; seven skills found; session-start reads or creates records only for this project |
| Fresh Claude | Claude instruction file loads protocol; project CLAUDE reads AGENTS; same records used |
| Existing task in startup request | Context restored, task owner recorded in STATUS and work continues without another approval gate |
| Existing active collaborator | Their task status and uncommitted edits stay untouched |
| Checkpoint then resume | Identity, exact task and next step survive; checkpoint did not close the task |
| File write fails | No success claim; exact unsaved update and handoff reported |
| Codex override takes precedence | Installer identifies override, preserves it, reports that kit loading is unresolved |
| Repeat identical install | No changes, duplicate read lines or extra backups |
| Custom instruction or modified skill | Concrete merge/conflict presented; unrelated content preserved |
| 1.x direct update | Personal block preserved verbatim; entry + shared protocol correctly deployed |
| 1.x imported update | Custom instructions preserved; one reviewed reference change; personal block moved into builder-kit-entry.md |
| Project-only installation | Local AGENTS explicitly reads local protocol; local skills discovered; globals untouched |
| Protected instruction file | Target preserved; unresolved conflict reported without changing permissions |

Record which assistant/version and scenarios were actually tested in the release review.
Use current official documentation for claims about assistant behavior. Distinguish what
you observed in one installation from what the product guarantees for all users.
