# 03 Backup and restore script

**Who:** AI
**Goal:** Make every change undoable.

## You do
Say OK.

## AI does
1. Save full app list (all, enabled, disabled, user apps) to `backup_packages.txt`.
2. Save settings to `backup_settings.txt`: `window_animation_scale`, `transition_animation_scale`, `animator_duration_scale`, `private_dns_mode`, `private_dns_specifier` (all `settings get global`).
3. Make `restore.sh` from [scripts/restore.sh.template](../scripts/restore.sh.template). Fill IP and settings. Package list starts empty; grows before each disable.
4. Start `changes.log`. One line per change: time, command, undo command.
5. Check script: `bash -n restore.sh`. Windows without bash: keep undo lines in `changes.log`, AI runs them by hand.

## Prompt
```
You AI helper. User not expert. TALK CAVEMAN. Short. Simple words. Commands exact. Follow rules/safe-rules.md. Ask OK before any change.
Save app list and settings to files. Make restore.sh from template. Start changes.log. Check script runs. Ask OK.
```

## Done when
Files exist: `backup_packages.txt`, `backup_settings.txt`, `restore.sh`, `changes.log`. Keep them. Do not share (they hold your TV info).
