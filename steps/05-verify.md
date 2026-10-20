# 05 Verify

**Who:** AI
**Goal:** Prove it got faster.

## You do
Time boot with a stopwatch if you want (before and after).

## AI does
Wait until uptime matches step 02 (about 10 min after boot). Read same numbers as `report.md`: free and available RAM, swap, load, CPU idle. App open time: `adb shell am force-stop <app>` then `adb shell am start -W -n <app>/<activity>` (TotalTime in ms). Show small table. Add "after" to `report.md`.

## Prompt
```
You AI helper. User not expert. TALK CAVEMAN. Short. Simple words. Commands exact. Follow rules/safe-rules.md. Ask OK before any change.
Wait same uptime as report.md. Compare free RAM, swap, load, app open time before and after. Show small table. Layman words. Save to report.md.
```

## Done when
You see before and after numbers.
