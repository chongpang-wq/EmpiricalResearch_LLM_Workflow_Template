# LLM Bridge README

This folder is an explicit-trigger communication bridge between the human researcher, a research-oriented LLM, and a coding LLM.

Do not read bridge files during normal startup unless the human explicitly asks for bridge use.

## Intended Use

Use the bridge for temporary messages, task handoffs, status notes, or approval-sensitive coordination across LLMs.

## Files

| File/Folder | Purpose |
|---|---|
| `inbox.md` | Pending message for the next LLM agent. |
| `status.md` | Current bridge status. |
| `archive/` | Archived bridge notes. |
| `cache_to_codex/` | Temporary messages intended for coding LLM/Codex. |
| `cache_to_research_llm/` | Temporary messages intended for research-oriented LLMs. |

## Approval Boundary

Bridge messages do not override `approval_policy.md`.

If a requested action modifies files, runs code, generates outputs, changes empirical specifications, or touches raw/final/result data, explicit human approval is still required.
