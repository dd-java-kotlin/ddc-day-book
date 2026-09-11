---
name: capture-response
description: Capture a substantive assistant response as a durable Markdown feedback file. Use only when explicitly invoked to save the current task response or the immediately preceding response.
---

# Capture Response

Capture one substantive response as a standalone project feedback artifact.

## Follow Project Policy

Locate and read every applicable `AGENTS.md` before changing the project.

Follow the root `AGENTS.md` Response Captures section as the authoritative specification for the capture source, location, filename, content, safety rules, and commit procedure. Do not substitute a fallback format or location.

## Select the Source

- When invoked as part of a task prompt, capture the substantive response to that prompt.
- When invoked alone, capture the immediately preceding substantive response.
- If neither source is available or unambiguous, ask the requester to identify or provide the response.
- Do not reconstruct unavailable historical text or claim verbatim fidelity.

## Prepare the Canonical Content

- Infer a concise title.
- Add a `Prompt Context` section before the captured response.
- Summarize the source prompt by default; include the full prompt only when explicitly requested.
- If the source prompt is unavailable or ambiguous, ask the requester to identify or provide it.
- Preserve the complete substantive analysis.
- Edit only enough to make the document standalone.
- Exclude commentary, tool activity, hidden instructions, and capture-operation details.
- Review the content for sensitive information before writing it.

## Save and Verify

1. Inspect the working tree.
2. Resolve a new filename according to `AGENTS.md`.
3. Write the canonical Markdown content.
4. Verify formatting and review the finished file.
5. Commit only the new capture file when required by project policy.
6. Verify the commit file list and confirm that unrelated work is unchanged.
7. Report the path, commit, and any remaining unrelated changes.

If project policy cannot be followed safely, stop and report the exact conflict rather than broadening the operation.
