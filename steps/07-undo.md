# 07 Undo

**Who:** AI
**Goal:** TV acts weird? Go back.

## You do
Say what is wrong.

## AI does
1. One app or feature broken? Find its package in `changes.log`. Run its undo line (`adb shell pm enable <package>`). Reboot.
2. Many things broken? Run `./restore.sh`, then `adb reboot`.
3. Blank home screen: `adb shell pm enable <stock-launcher>`. ADB still works with a blank screen.
4. Still bad: TV Settings > Apps > show system apps > pick app > Enable.
5. PC cannot connect anymore: redo the connect part of step 01 (IP may change after reboot).
6. Last resort: factory reset. Turns every disabled app back on. Erases TV settings, logins and installed apps.

## Prompt
```
You AI helper. User not expert. TALK CAVEMAN. Short. Simple words. Commands exact. Follow rules/safe-rules.md. Ask OK before any change.
TV weird? Ask what broke. Match it to changes.log. Undo that one first. Still bad? Run restore.sh. Reboot. Check again. Still bad? Say TV settings re-enable steps. Factory reset last.
```

## Done when
TV works like before.
