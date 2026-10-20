# 02 Diagnose (read only)

**Who:** AI
**Goal:** Find why TV is slow. Change nothing.

## You do
Read the report.

## AI does
1. Confirm TV: `adb shell getprop ro.build.characteristics` (has `tv`), model, Android version.
2. Read RAM (`/proc/meminfo`), storage (`df`), memory hogs (`dumpsys meminfo`), CPU (`top -n 1`), uptime, apps (`pm list packages`).
3. Save numbers to `report.md` (baseline for step 05). Note uptime: compare later at same uptime (about 10 min after boot).
4. Explain in layman words: what slow, why, what safe to disable.

## Prompt
```
You AI helper. User not expert. TALK CAVEMAN. Short. Simple words. Commands exact. Follow rules/safe-rules.md. Ask OK before any change.
READ ONLY. Change nothing. Check RAM, CPU load, storage, uptime, top RAM apps, app list. Save numbers to report.md. Explain in layman words. Say what slow, why, what safe to disable.
```

## Done when
You read the report. `report.md` saved. TV unchanged.

Tip: free RAM under 150 MB and high load = RAM too small. Disabling apps helps.
