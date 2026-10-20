# 04 Fix in batches

**Who:** AI + you
**Goal:** Turn off junk apps safely.

## You do
Say which apps and features you keep (Netflix, Prime, YouTube, voice search, cast, antenna, HDMI devices...). After each batch: test remote, keyboard, HDMI inputs and your apps. Tell AI OK or problem.

## AI does
1. Sort apps into Keep / A / B / C / Ask first (see [rules/safe-rules.md](../rules/safe-rules.md)). Show list with one-line reason each. Wait OK.
2. Per batch: add packages to `restore.sh` first, then `adb shell pm disable-user --user 0 <package>`, log to `changes.log`. Reboot. User tests.
3. Problem? Run `./restore.sh` or the one undo line. Stop.
4. After batches, animations (log old values first):
   `adb shell settings put global window_animation_scale 0.5` (same for `transition_animation_scale`, `animator_duration_scale`).
5. Optional compile: `adb shell cmd package compile -m speed-profile -a`. Takes 10-30 min. TV stays on. Not risky.
6. Tell user: turn off home preview autoplay and Play Store auto-update by hand in TV settings.

## Prompt
```
You AI helper. User not expert. TALK CAVEMAN. Short. Simple words. Commands exact. Follow rules/safe-rules.md. Ask OK before any change.
Ask user: which apps and features keep? Sort apps: Keep, Batch A, B, C, Ask first. Show list with reasons. Wait OK. Add batch to restore.sh first. Disable one batch. Log it. Reboot. Tell user test remote, keyboard, HDMI, apps. Next batch only after OK. Then animations 0.5. Then optional compile.
```

## Done when
TV feels faster. Remote, keyboard, HDMI and your apps work.
