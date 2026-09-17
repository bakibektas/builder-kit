# Roadmap

Version 2.1.1 ships instruction files for Claude Code and Codex, seven shared skills,
and standalone project memory in five files.
The assistant follows these text files; the kit includes no background program.

## Next: repeatable installation and release validation

An installer program could track which files belong to the kit, create backups and
compare old kit files, user edits and updated kit files before merging changes. Before
replacing installation by the assistant, it needs tests for previewing changes, repeating
an install without duplicates, custom paths and restoring backups. Tests across supported
command-line application versions should use separate test configuration folders and
confirm that each assistant actually finds the installed instructions and skills.

## Localization

Personal language already governs conversation and entries. Translating structural file
names, headings and ritual names needs a stable mapping so mixed-language teams can
still share records and commands. Keep English structural names until that exists.

## Other assistants

Add instruction files for other assistants people use, including local models. Verify
that each assistant finds the instructions and skills and can save project records.
Reuse the shared protocol instead of maintaining separate copies of the same rules.
An assistant that reads text can follow the habits;
tool access and enforcement still need separate verification.
