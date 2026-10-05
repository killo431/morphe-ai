---
name: "recon-apk"
description: "Inspect an authorized APK, APKM, APKS, or XAPK and create a structured Morphe reconnaissance report. Use for a new app before decompilation or patch target analysis."
---

> Generated from `plugins/morphe-patch-creator/skills/recon-apk/SKILL.md` by `.gemini/convert.py`.

## Gemini main-session handoff
The main session delegates this bounded stage to `creator-apk-recon` with resolved inputs and required approvals, then checks its evidence. When read inside a subagent, execute only your assigned stage and return to main; do not recursively delegate. The original fork/background metadata is not a Gemini skill setting.

Device changes and repository submissions are not authorized by activating this skill. Use only explicit `/morphe:test-on-device` or `/morphe:submit-patch` user commands with fresh confirmations.


# Recon an APK

Inspect the supplied package without modifying the original.

1. Resolve the analysis directory from project configuration.
2. Use `plugins/morphe-patch-creator/scripts/init-analysis.sh` when the workspace is new.
3. Use `plugins/morphe-patch-creator/scripts/inspect-apk.sh` for deterministic metadata evidence.
4. For split containers, inspect the base APK but preserve the original container as the future Morphe CLI input.
5. Write `analysis/<app>/notes/recon.md` with identity, SDK levels, format, DEX count, framework, architectures, protections, and tool limitations.
6. Mark recon complete only after the report exists and evidence is captured.
7. Return the report path and recommended next stage.

Do not decompile, hunt targets, write patches, install packages, or use a remote service.
