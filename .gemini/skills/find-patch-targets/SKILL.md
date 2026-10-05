---
name: "find-patch-targets"
description: "Find Morphe patch targets in decompiled Android source and verify each target against exact smali bytecode. Use after decompiled source and smali exist."
---

> Generated from `plugins/morphe-patch-creator/skills/find-patch-targets/SKILL.md` by `.gemini/convert.py`.

## Gemini main-session handoff
The main session delegates this bounded stage to `creator-target-hunter` with resolved inputs and required approvals, then checks its evidence. When read inside a subagent, execute only your assigned stage and return to main; do not recursively delegate. The original fork/background metadata is not a Gemini skill setting.

Device changes and repository submissions are not authorized by activating this skill. Use only explicit `/morphe:test-on-device` or `/morphe:submit-patch` user commands with fresh confirmations.


# Find Patch Targets

Search in this order unless the requested behavior requires a narrower route:

1. Relevant app architecture and SDKs.
2. Requested feature or behavior call chain.
3. Local feature gates and stable strings.
4. Protections that directly prevent an authorized modification.
5. Related ads, analytics, or configuration only when in scope.

For every candidate, verify the exact smali method and record:

- DEX and class path.
- Full method signature, access flags, return type, and parameters.
- Register count and ordered instruction evidence.
- Stable fingerprint fields that avoid obfuscated app identifiers.
- Proposed patch behavior and limitations.

Write one findings file per target type under `analysis/<app>/notes/`. A Java-only finding is incomplete and must not be handed to `creator-patch-writer`.
