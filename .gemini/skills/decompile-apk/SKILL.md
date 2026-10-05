---
name: "decompile-apk"
description: "Decompile an authorized Android package and extract smali from all DEX files for Morphe analysis. Use after reconnaissance and before target hunting."
---

> Generated from `plugins/morphe-patch-creator/skills/decompile-apk/SKILL.md` by `.gemini/convert.py`.

## Gemini main-session handoff
The main session delegates this bounded stage to `creator-apk-decompiler` with resolved inputs and required approvals, then checks its evidence. When read inside a subagent, execute only your assigned stage and return to main; do not recursively delegate. The original fork/background metadata is not a Gemini skill setting.

Device changes and repository submissions are not authorized by activating this skill. Use only explicit `/morphe:test-on-device` or `/morphe:submit-patch` user commands with fresh confirmations.


# Decompile an APK

1. Require an existing recon report and original package under the app analysis directory.
2. Check for existing non-empty `decompiled/` or `smali/` output; do not overwrite it without explicit approval.
3. Prefer `plugins/morphe-patch-creator/scripts/decompile-local.sh`.
4. Extract all DEX files using `plugins/morphe-patch-creator/scripts/extract-smali.sh`.
5. Verify non-zero Java/source and smali outputs and record counts.
6. If local jadx is unavailable or unsuitable, explain the optional remote data flow. Use `jadx-decompiler-gui` only when configured and explicitly approved.
7. Record exact failures and leave the stage failed or blocked rather than claiming partial success.

Do not search for patch targets or write patch code.
