---
name: "validate-patch"
description: "Build, list, and locally apply Morphe patches to verify registration and fingerprint matching. Use after patch source exists or when diagnosing build and match failures."
---

> Generated from `plugins/morphe-patch-creator/skills/validate-patch/SKILL.md` by `.gemini/convert.py`.

## Gemini main-session handoff
The main session delegates this bounded stage to `creator-patch-validator` with resolved inputs and required approvals, then checks its evidence. When read inside a subagent, execute only your assigned stage and return to main; do not recursively delegate. The original fork/background metadata is not a Gemini skill setting.

Device changes and repository submissions are not authorized by activating this skill. Use only explicit `/morphe:test-on-device` or `/morphe:submit-patch` user commands with fresh confirmations.


# Validate a Morphe Patch

Read `plugins/morphe-patch-creator/references/upstream-baseline.md` before running any CLI command.
Detect the installed CLI version (non-mutating) before any version-sensitive invocation:

```bash
CLI_VERSION=$(java -jar "$MORPHE_CLI" -V 2>/dev/null \
              || java -jar "$MORPHE_CLI" --version 2>/dev/null \
              || echo "unknown")
echo "CLI version: $CLI_VERSION"
```

If the jar is absent, report it and stop.

Perform these gates in order:

1. Resolve the patch repository, Morphe CLI, original input package, and output directory.
2. Build the patch bundle using the repository's documented Gradle task.
3. Resolve the bundle from project version metadata rather than an ambiguous glob.
4. Run `list-patches` and confirm the expected patch name and compatibility.
5. Apply the intended patch to the original APK/APKM/APKS/XAPK and write a new artifact under `analysis/<app>/builds/`.
6. Capture command, exit status, relevant output, and resulting artifact.

A compilation failure is a writer handoff. A fingerprint match failure is a creator-target-hunter handoff. Do not install the artifact, alter a device, commit, push, or publish.
