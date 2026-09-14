# Roadmap

Version 2.0.1 ships native Claude Code and Codex instructions, seven shared skills,
and standalone project memory in five files.
These are instruction-level capabilities; no background runtime is bundled.

## Next: repeatable installation and release validation

An executable installer could make ownership tracking, backups and three-way updates
deterministic. It needs dry-run, idempotence, custom-path and rollback tests before it
replaces the agent-driven contract. Runtime acceptance across supported CLI versions
should use isolated homes and real discovery, not just check for files on disk.

## Localization

Personal language already governs conversation and entries. Translating structural file
names, headings and ritual names needs a stable mapping so mixed-language teams can
still share records and commands. Keep English structural names until that exists.

## Other assistants

Add adapters for hosts people actually use, including local models, with verified
instruction discovery, skill delivery and persistence checks. Reuse the shared protocol
instead of multiplying doctrine copies. A host that reads text can follow the habits;
tool access and enforcement still need separate verification.
