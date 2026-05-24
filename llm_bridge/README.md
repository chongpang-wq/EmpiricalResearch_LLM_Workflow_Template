# LLM Bridge README

`llm_bridge/` is a temporary, explicit-trigger communication layer between the human researcher, research-oriented LLMs, and coding LLMs/Codex.

It is not general project memory, not a task archive, and not a replacement for `!llm_record.md` or `tasks/`.

## Default Non-Reading Rule

Agents should not read `llm_bridge/cache_to_codex/`, `llm_bridge/cache_to_research_llm/`, `llm_bridge/inbox.md`, `llm_bridge/status.md`, or archived bridge messages during normal project startup.

These files may contain stale, temporary, or task-specific messages. They should be consulted only when:

- the human sends exactly `llm`; or
- the current task explicitly instructs the agent to inspect the bridge.

This rule is intended to prevent context pollution.

## Command: `llm`

When the human sends exactly `llm` and nothing else, the receiving agent should:

1. Read `llm_bridge/README.md`.
2. Check the relevant bridge inbox/cache location for open messages addressed to that agent.
3. Act only within the stated permission boundary.
4. Report completion, advice, or questions to the human.

`llm` is never approval to run code, modify data, modify result files, or change empirical specifications.

If the bridge request asks a coding LLM/Codex to perform a sensitive action, the coding LLM/Codex must not execute it immediately. It should send the human a short risk notice and wait for `au` or `uau`.

Allowed `To` values:

- `research_llm`
- `coding_llm`
- `codex`
- `both`
- `human`

## Cache-File Relay

`llm_bridge/` supports temporary cache files because a research-oriented LLM may be able to create new files but may not be able to update existing `inbox.md`.

Cache folders:

- `llm_bridge/cache_to_codex/`
- `llm_bridge/cache_to_research_llm/`

These folders are not general memory and should not be read during normal startup.

### Research LLM to Coding LLM/Codex

When the human sends exactly `llm` to a research-oriented LLM, that LLM may create a new temporary Markdown file under `llm_bridge/cache_to_codex/`.

The file should contain a self-contained message for the coding LLM/Codex. The research-oriented LLM must not modify existing project files, data, results, code, or `inbox.md` unless the human explicitly approves that action.

### Coding LLM/Codex Receiving `llm`

When the human sends exactly `llm` to a coding LLM/Codex, it should:

1. Read `llm_bridge/README.md`.
2. Check `llm_bridge/cache_to_codex/` for open temporary messages.
3. Read the newest open message addressed to the coding LLM/Codex.
4. Transcribe the message into its working context or completion report.
5. Act only within the stated permission boundary.
6. Delete the cache file or move it to `llm_bridge/archive/` after processing, if that is allowed by the project rules.

The coding LLM/Codex must never treat `llm` as approval to run code, modify data, modify results, or change empirical specifications.

If the cache message asks for a sensitive action, the coding LLM/Codex must first show the short sensitive-action risk notice and wait for `au` or `uau`.

### Cache File Template

```markdown
# Temporary Bridge Message to Coding LLM/Codex

Status: open
From: research_llm
To: coding_llm
Created:
Task ID:

## Message

## Requested Action

## Permission Boundary

## Sensitive Action Check

## Expected Coding LLM/Codex Response

## Disposal Rule
```

## Sensitive Actions

A sensitive action is any action that involves:

- running code;
- modifying data;
- modifying, creating, deleting, or overwriting result files;
- changing empirical specifications;
- changing sample restrictions, controls, fixed effects, clustering, estimators, or treatment definitions;
- changing variable definitions or output paths.

## Command: `au`

When the human sends exactly `au` and there is a pending sensitive action, the coding LLM/Codex may execute only that pending sensitive action.

The coding LLM/Codex must not expand the action beyond the stated files, commands, or scope.

After completion, it must report:

- files changed;
- commands run;
- outputs generated;
- whether the action stayed within the approved scope.

## Command: `uau`

When the human sends exactly `uau` and there is a pending sensitive action, the coding LLM/Codex must cancel the pending action.

It should not modify files or run code. It should update `llm_bridge/status.md` to indicate that the sensitive action was rejected, if it has permission to update that file.

## Sensitive Action Risk Notice

If approval is needed, the coding LLM/Codex should send only a very short risk notice:

```text
Sensitive action pending.

Files affected:
- ...

Reason:
...

Reply `au` to approve or `uau` to reject.
```

Allowed short reasons include:

- `debug`
- `generate new results`
- `update specification`
- `rerun analysis`
- `overwrite results`

## Command: `renew`

When the human sends exactly `renew` and nothing else to a coding LLM/Codex, it should reset the temporary bridge state:

1. Reset `llm_bridge/inbox.md` to the blank template.
2. Reset `llm_bridge/status.md` to an idle / no-open-request state.
3. Move old bridge messages to `llm_bridge/archive/` only if the protocol already provides for it or the human explicitly approves.

`renew` must not delete or modify:

- `!technical_readme.md`
- `!llm_record.md`
- `project_inventory.md`
- `external_dependencies.md`
- `tasks/`
- `code/`
- `data_raw/`
- `data_intermediate/`
- `data_final/`
- `result/`

`renew` is not approval to run code, modify data, modify results, change empirical specifications, or delete general project memory.

## Bridge Request Fields

Bridge requests should include:

- Status
- From
- To
- Priority
- Created
- Task ID
- Message
- Context
- Requested Action
- Permission Boundary
- Pending Sensitive Action
- Pending Action Summary
- Files Affected
- Reason
- Approved by Human
- Expected Response
- Response

## Roles

### Human Researcher

The human researcher is the approval authority.

The human decides whether to:

- run code;
- modify data;
- generate or overwrite results;
- change empirical specifications;
- accept or reject coding LLM/Codex changes;
- forward bridge messages between agents.

### Research-Oriented LLM

A research-oriented LLM supports research design, empirical strategy, interpretation, code-review guidance, documentation advice, and coding-agent prompt design.

It should read bridge files only when the human sends exactly `llm` or explicitly asks it to inspect the bridge. If it believes a coding LLM/Codex should act, it should provide a self-contained bridge message for the human to forward or approve.

### Coding LLM/Codex

A coding LLM/Codex is the implementation-oriented agent.

It may modify files only within explicit human-approved scope. It should not silently change empirical specifications, sample restrictions, controls, fixed effects, clustering, estimators, data definitions, or result files.

If it needs research-design judgment, it should write a clear request for research-oriented LLM review in `llm_bridge/inbox.md` or report the question to the human.

