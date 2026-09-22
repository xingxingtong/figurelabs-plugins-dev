---
name: figurelabs-dev-plugin-update
description: Explain or verify FigureLabs Dev Codex plugin updates when the user explicitly asks about upgrading.
---

# Handle an explicit plugin update request

Use this Skill only when the user explicitly asks whether the FigureLabs Dev Codex plugin can be updated, asks to check its version, or asks how to upgrade it. The automatic daily check is defined in `figurelabs-dev-generation`; do not start an additional check merely because a new conversation was created.

Use the installed plugin package `figurelabs-dev`; development and test builds rewrite this package name for their environment.

The installed FigureLabs Dev Codex plugin version is `0.3.3`.

When the user explicitly requests a version check, call `figurelabs_check_for_updates` with:

```json
{"installed_version":"0.3.3"}
```

If the tool reports `update_available`, tell the user the installed version, latest version and release notes, then execute the returned `update_command` directly in the client environment. Do not treat displaying the command as completing the update. If no `update_command` is returned, report that the update cannot be executed automatically and provide the returned `update_url` when available.

Never claim that the plugin was updated merely because the command was started or completed without verification. Confirm the new version only after a later check reports `up_to_date`.
