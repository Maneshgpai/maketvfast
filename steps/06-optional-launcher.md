# 06 Optional: light launcher

**Who:** AI + you
**Goal:** Swap heavy home screen for light one (e.g. Projectivy). Skip if you like your home screen.

## You do
Install the new launcher from the TV app store. Press Home, choose it as **Always**. Test it.

## AI does
1. Find stock launcher. Never guess: `adb shell cmd package resolve-activity -a android.intent.action.MAIN -c android.intent.category.HOME` and `adb shell pm list packages | grep -i launcher`. Android TV is often `com.google.android.tvlauncher`, Google TV `com.google.android.apps.tv.launcherx`. Fire TV and others differ.
2. Confirm new launcher installed (Projectivy package `com.spocky.projengmenu`).
3. Confirm it is the home app (same resolve command).
4. Test: Home, open app, Home.
5. Add stock launcher to `restore.sh` and `changes.log` first. Then disable old: `adb shell pm disable-user --user 0 <stock-launcher>`. Refused? Stop. Keep stock launcher. Never use `pm hide`.
6. Reboot. Check Home, remote, inputs.

**Danger:** never disable old launcher before new one is installed, set as home and tested. Else screen may go blank.

**Fire TV:** skip. Amazon blocks launcher swap on new Fire OS; disabling `com.amazon.tv.launcher` can leave a blank screen.

**Undo:** `adb shell pm enable <stock-launcher>`, then pick stock home in Settings.

## Prompt
```
You AI helper. User not expert. TALK CAVEMAN. Short. Simple words. Commands exact. Follow rules/safe-rules.md. Ask OK before any change.
Optional. Ask user want light launcher? Yes: find real launcher name, never guess. Install new launcher first. Set as home. Test. Then disable old. Give undo line.
```

## Done when
Home opens new launcher. Remote works.
