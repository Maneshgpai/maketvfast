# Smart TV Speed-Up

Slow smart TV? Let an AI helper speed it up from your PC. It turns off apps you never use, so the TV gets free memory (RAM). Nothing is deleted. Everything can be undone.

> **Disclaimer:** Use at your own risk. The author is not responsible for any damage to your TV's OS, software or hardware, data loss, or warranty issues. No guarantees. See [DISCLAIMER.md](DISCLAIMER.md).

## Works on

| TV | Works? |
|---|---|
| Android TV, Google TV, Fire TV (Acer, Sony, TCL, Xiaomi, Hisense, Philips, Shield...) | Yes |
| Samsung (Tizen), LG (webOS), Roku | No (only the optional ad blocker, by hand) |

Best for TVs with 1-2 GB RAM.

## Benefits
- Faster menus and faster app opening.
- Real example (Acer, 1.5 GB RAM): available RAM went from about 350 MB to about 458 MB (+30%). See [real test results](#real-test-results-acer-tv-15-gb-ram).
- No recommendations or ads (optional).
- Free. Reversible.

## Real test results: Acer TV, 1.5 GB RAM

Tested on a real Acer TV: Android 14, Realtek rtd2841a chip, 32-bit, 1.5 GB RAM, 600 MB swap, 4 cores. Numbers read over ADB (`/proc/meminfo`, `top`, `dumpsys meminfo`). Each reading was taken a few minutes after boot, so small differences are noise.

| Metric | Before | After all changes | Change |
|---|---|---|---|
| Available RAM | ~350 MB | ~458 MB | +~108 MB (+30%) |
| Free RAM | ~75 MB | ~90 MB | +15 MB |
| Swap in use | 131-231 MB | 90 MB | -40% or more |
| CPU idle (of 400%) | 180% | 354% | CPU much calmer |
| Running tasks | 454-470 | 450 | Slightly fewer |
| Load average (4 cores) | 22-25 | ~23 | No change (CPU idle, so likely a kernel quirk) |
| Animation speed | 1.0 | 0.5 | Menu animations take half the time |
| Ad block (Private DNS, AdGuard) | Off | On | Ads and trackers blocked system-wide |
| Home screen | Stock launcher with recommendations | Projectivy (clean, no ads) | No home ads |

### What was disabled (reversible)
- **Junk and debug:** `com.apps.logapp`, `com.apps.factory.ui`, `com.mk.tv.meeting.service`, `com.mk.tv.timeclock`, `com.creative.fastscreen.tv`, `com.apps.usbmediaplayer`.
- **Setup and games:** `setupwraith`, `initsetup`, Play Games, YouTube Music.
- **Updaters:** `com.apps.ota`, `com.apps.authota`. Downside: no more security updates.
- **Google extras:** `tvrecommendations`, `tvlauncher` (replaced by Projectivy), `tv.remote.service` (phone remote), `katniss` (voice search, mic button), `mediashell` (cast from phone).
- **TV tuner and input apps:** `livetv`, `atsc`, `isdb`, `atv`, `passthrough`. This owner uses no antenna and no HDMI devices. **`passthrough` = HDMI inputs.** Use a console, cable box or streaming stick? Keep it.

This list fits this one TV and owner. Your AI builds your own list from your TV.

### What still uses the most RAM
- `system` (~286 MB), Projectivy (~199 MB), Play Store (~150 MB plus ~129 MB in the background), `gms` (~135 MB).
- Streaming apps you open (Netflix ~141 MB, Prime ~157 MB). Avoid opening several at once.

### Honest take
- Gain is real but modest. 1.5 GB is tight for Android 14.
- Swap and CPU load improved most. Menus feel faster mainly because of animations and less swap.
- For a big jump, add a cheap streaming stick with 2 GB or more RAM.
- Tip: turn off Play Store auto-update to cut the ~129 MB background process.

## Risks
- Wrong app disabled = remote, inputs or an app may misbehave.
- TV updates may stop, or may turn apps back on.
- Ad blocker (optional) can break some apps.
- Debugging left ON = other devices on your wifi can ask to control the TV. Turn it off at the end ([step 08](steps/08-finish.md)).
- Backup, restore script and change log make these easy to undo. Factory reset turns everything back on as a last resort.

## Time and cost
- Time: under 1 hour.
- Cost: under $1.50 of AI usage with Claude Sonnet 5.5 (estimate; it varies).

## You need
- A PC on the same wifi as the TV.
- An AI desktop app that can run commands (Claude, ChatGPT, Gemini, Cursor).

## Quick start
1. Do [step 01](steps/01-setup-you.md) yourself. Plain instructions, no AI. About 15 minutes.
2. Open this folder in your AI app.
3. Paste [prompts/master-prompt.md](prompts/master-prompt.md).
4. Follow the AI. It asks OK before every change.
5. At the end do [step 08](steps/08-finish.md) yourself.

Prefer step by step? Use the [steps](steps/) folder. AI steps (02 to 07) each have their own prompt.

## Steps

| # | Step | Who |
|---|---|---|
| 01 | [Setup: check TV, install ADB, enable debugging, connect](steps/01-setup-you.md) | You |
| 02 | [Diagnose (read only)](steps/02-diagnose.md) | AI |
| 03 | [Backup and restore script](steps/03-backup-restore.md) | AI |
| 04 | [Fix in batches](steps/04-fix-in-batches.md) | AI + you |
| 05 | [Verify](steps/05-verify.md) | AI |
| 06 | [Optional: light launcher](steps/06-optional-launcher.md) | AI + you |
| 06b | [Optional: ad blocker](steps/06b-adblock-dns.md) | AI + you |
| 07 | [Undo](steps/07-undo.md) | AI |
| 08 | [Finish: turn off debugging](steps/08-finish.md) | You |

## Backup and restore
- **Backup:** before any change, the AI saves your app list and settings to files.
- **Change log:** every change goes to `changes.log` with its undo line, before it runs.
- **Restore:** the AI makes `restore.sh`. Run it and every change is undone. Details: [step 03](steps/03-backup-restore.md) and [step 07](steps/07-undo.md).

## Folders
- `steps/` human instructions (01, 08) and AI steps with prompts (02 to 07)
- `prompts/` one master prompt
- `rules/` safety rules the AI follows
- `scripts/` restore script template

## License
MIT. See [LICENSE](LICENSE).
