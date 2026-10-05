---
name: "write-patch"
description: "Implement an approved Morphe patch design from smali-verified findings. Use only after target evidence exists and the user has approved the proposed source changes."
---

> Generated from `plugins/morphe-patch-creator/skills/write-patch/SKILL.md` by `.gemini/convert.py`.

## Gemini main-session handoff
The main session delegates this bounded stage to `creator-patch-writer` with resolved inputs and required approvals, then checks its evidence. When read inside a subagent, execute only your assigned stage and return to main; do not recursively delegate. The original fork/background metadata is not a Gemini skill setting.

Device changes and repository submissions are not authorized by activating this skill. Use only explicit `/morphe:test-on-device` or `/morphe:submit-patch` user commands with fresh confirmations.


# Write a Morphe Patch

Before editing, read `plugins/morphe-patch-creator/references/upstream-baseline.md` and require:

- A recon report.
- Smali-verified findings.
- A named patch design with target files.
- Recorded user approval for source modification.
- A resolved patch repository.

Read existing app patches and project conventions before changing files. Add to existing structure rather than overwriting it. Never use obfuscated app class, method, or field names as fingerprint identity. Prefer stable SDK calls, signatures, strings, literals, and ordered filters verified against smali.

Extension artifacts use the `.mpe` suffix, not `.mpp`. Verify filter location API names and `instructionMatches` availability against the installed patcher version.

After editing, run the narrowest relevant compile/build validation. Return exact files changed, commands, exit results, and unresolved risks. Do not install to a device or perform Git write operations.
