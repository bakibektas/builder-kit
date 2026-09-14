# Builder Collective adapter

Compatibility reference, reviewed 2026-09-14. This kit distributes instructions; the
Builder MCP backend, hooks, model board, tracked wrappers and AgentHub are separate
infrastructure. Do not advertise them as installed by copying BuilderKit.

## Adopt the current authority

For a managed project, set `Memory backend: collective` through its governance tools.
Keep the generated native instruction file. The live DB brief overrides this static
compatibility reference. Fetch with the absolute project path, actual role and the
correct audience (`codex` for Codex). Activate relevant domain packs before domain work.
Write rule audience and role scope as real schema fields, not tags containing those names.
Promote a translated rule through `agent_upsert_rule`, then the site's managed writeback.
Do not copy personal paths, session IDs or a private full brief into a public template.

## Lifecycle and memory translation

| Portable ritual/record | Collective operation |
|---|---|
| session-start / STATUS | `agent_get_brief` + task board + `agent_get_latest_checkpoint` |
| Session identity | Reuse hook/wrapper session; `agent_start_session` only when needed |
| next-task | Real plan via `agent_save_plan`; task via `agent_upsert_task`, then `agent_claim_task` |
| JOURNAL | `agent_log_action` |
| DECISIONS | Use the live decision tool schema or record rationale in the plan/checkpoint |
| log-lesson / LESSONS | Search lessons, then `agent_log_lesson` |
| research-method / RESEARCH | Search prior research, then `agent_save_research` |
| artifacts | Search first; `agent_push_artifact`, revise the existing record when appropriate |
| checkpoint | `agent_checkpoint_session` with actual session ID, summary and handoff |
| Standing rules | `agent_upsert_rule` with explicit audience and role scope |
| session-end | Close owned tasks, log results, checkpoint and verify successful responses |

These are conceptual operations, not copy-paste argument schemas. Inspect the exposed
tools before calling them. A client may namespace an `agent_*` tool; use the callable
name it exposes. Always pass `repo` as an absolute path when supported. Verify the result,
including nested error content, before claiming a write succeeded.

## Codex bootstrap

The deployed Collective supports Codex lifecycle hooks. Verify all four birth parts
contain actual content: identity, rules/digest, repo brief, checkpoint. Headings with no
payload are incomplete. Fetch missing parts explicitly. Hooks are an optimization;
the fallback must work without them, and must not create a second identity.

When a wrapper supplies `AGENTHUB_SESSION_KEY`, `AGENTHUB_PARENT_KEY` and
`AGENTHUB_TASK_ID`, retain those bindings on session registration using the corresponding
`session_key`, `parent_session_key`, `task_id` fields, plus its session ID when supplied.
Use the identity returned by the backend if it unifies with an existing run. Never
manufacture a second session to get around a missing tool or claim conflict.

Check the installed CLI's help before using headless flags. Local deployment instructions
can require a particular approval mode, but copying a flag into a portable kit does not
make it available or authorized everywhere. Never bypass a tool denial through raw HTTP.

## Capabilities and limits

| Capability | September 14 deployment evidence | Portable treatment |
|---|---|---|
| Audience/role filtered brief and lazy packs | Served by Builder MCP | Fetch live; do not embed a full registry snapshot |
| DB state and generated thin instruction stubs | Current Collective governance | MCP owns updates; no file-memory fallback on outage |
| Codex hooks and claim tracking | Installed local hook/config pipeline | Detect real injection; kit installs no hooks |
| Codex tracked execution | `scripts/codex-run.js` uses model-board selection and run bindings | Use the deployed wrapper and its help; not bundled here |
| Task-class model routing | `agent_resolve_model` and wrapper validation | Resolve at launch; no frozen model slug list |
| AgentHub Codex route | Board-runs route remains feature-gated in the reviewed deployment | Verify enabled status and a real registered run before relying on it |
| Guards | Coverage depends on host and hook installation | Distinguish policy from enforcement; absence of a denial grants nothing |

For Codex, the reviewed Collective uses ChatGPT-plan subscription runs and prohibits
metered API-key runs. That is local billing policy, not a claim that every Codex user
has the same access. Never read credential stores to check it. Follow the live policy.
Tracked workers carry a real task ID, parent session binding, role and validated model
selection. They report to their parent, do not speak on the operator's voice/comms channel,
and do not restart infrastructure. Do small tasks inline when delegation is unnecessary.

## Health and migration

Discover the configured endpoint instead of assuming every installation uses Baki's ports.
The reviewed deployment uses 4071 for the dashboard and 4072 for the MCP aggregator.
Check server health separately from client tool discovery: a healthy service with missing
client tools can mean a stale client snapshot. Do not restart a shared stack from a worker.
If state tools fail, report what failed and what was not saved. Preserve the intended
handoff in the response; resume persistence when the authorized service is available.

To migrate file memory: inventory existing records, map them to the DB, preserve source
provenance, verify imported records can be retrieved, then change the declared authority.
Keep the old files as an archive; do not silently maintain both stores. This kit does not
perform migrations automatically.

## Official Codex references

Checked against the official documentation on 2026-09-14:

- [Instruction discovery and overrides](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
  establish the native entry points; a closer override can shadow a base file.
- [Skills](https://learn.chatgpt.com/docs/build-skills) document repository and user
  `.agents/skills` locations. The reviewed Collective also exposes legacy `.codex/skills`
  locations; verify discovery and avoid installing duplicate copies across both.
- [Configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference)
  documents lifecycle hook configuration. Availability does not prove hooks are enabled.

Local deployment claims above come from the live audience-filtered Collective rules,
not from OpenAI documentation, and must be rechecked before a deployment change.
