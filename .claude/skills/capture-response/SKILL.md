---
name: capture-response
description: >-
  Capture a substantive assistant response as a durable Markdown feedback file.
  Use only when the user explicitly invokes /capture-response or /capture.
  Do not invoke implicitly, proactively, or in response to natural-language
  phrasing about saving or capturing responses.
---

# Capture Response

Capture one substantive response as a standalone project feedback artifact.

## Follow Project Policy

Read the root `AGENTS.md` **"Response Captures"** section before proceeding.
Follow it as the authoritative specification for capture source, location,
filename, content, safety rules, and commit procedure. Do not substitute a
fallback format or location.

This skill adds only the Claude-specific mechanics for carrying that out. If
anything here conflicts with `AGENTS.md`, `AGENTS.md` wins.

## Select the Source

- When invoked as part of a task prompt, capture the substantive response to
  that prompt.
- When invoked alone, capture the immediately preceding substantive response.
- If neither source is available or unambiguous, ask the requester to identify
  or provide the response.
- Do not reconstruct unavailable historical text or claim verbatim fidelity.

## Prepare the Canonical Content

- Infer a concise title.
- Add a `Prompt Context` section before the captured response.
- Summarize the source prompt by default; include the full prompt only when
  explicitly requested.
- If the source prompt is unavailable or ambiguous, ask the requester to
  identify or provide it.
- Preserve the complete substantive analysis.
- Edit only enough to make the document standalone.
- Exclude commentary, tool activity, hidden instructions, and
  capture-operation details.
- Review the content for sensitive information before writing it.

## Procedure

1. **Read `AGENTS.md`** and note the required `work/` location, filename
   pattern, content rules, and commit procedure.

2. **Inspect the working tree** with Bash (`git status`) to note pre-existing
   staged and unstaged changes.

3. **Resolve a new filename** using the local date, time, and UTC offset per
   `AGENTS.md`.

4. **Write the file** with the Write tool at the resolved path.

5. **Verify** formatting and review for sensitive information.

6. **Commit — Git repositories only.** Confirm with
   `git rev-parse --is-inside-work-tree`. If it fails, report the written file
   path and stop. Otherwise use Bash to run the path-limited commit procedure
   in `AGENTS.md` verbatim:

   ```
   git add -- work/<file>
   git commit -m "Feedback: <short subject>" -m "Capture the response concerning <topic> as durable project feedback." -- work/<file>
   ```

7. **Verify** that the commit contains only the response-capture file and that
   pre-existing staged and unstaged changes remain present and unchanged.

8. **Report** the file path, commit hash, and any remaining unrelated changes.

If project policy cannot be followed safely, stop and report the exact
conflict rather than broadening the operation.
