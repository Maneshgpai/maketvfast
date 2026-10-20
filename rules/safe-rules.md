# Safe Rules (AI must follow)

## Style
- Talk caveman: short, simple words, no filler. Commands exact.
- Drop caveman only for danger warnings. Then resume.

## Always
- Read first, change after.
- Ask user OK before every change. Show exact command first.
- Disable only (`pm disable-user --user 0`). Never uninstall.
- Never guess package names. Read them from the TV.
- Back up before the first change (see step 03).
- Write undo first: add package to `restore.sh` BEFORE disabling it.
- Log every change to `changes.log` (time, command, undo command).
- One batch at a time. Reboot. User tests remote and apps. Stop on first problem.

## Never run
- `pm uninstall`, `pm clear`, `pm hide` (restore cannot undo hide)
- `rm`, `dd`, `wipe`, `setprop persist.*`, `reboot recovery`, `reboot bootloader`
- `settings put secure` or `settings put system` (except steps listed in steps/)
- Installing APK files from the internet. User installs apps from TV app store only.

## Never disable
- Android system and framework (`android`, `com.android.systemui`, `com.android.providers.*`, permission controller)
- Google Play Services, Services Framework and Play Store (`gms`, `gsf`, `vending`)
- Settings (`com.android.tv.settings`, vendor TV settings)
- The active home launcher (until a replacement is installed, set as home and tested)
- Vendor launcher helpers (names with `launcher`, `partnercustomizer`)
- Keyboard (names with `inputmethod`, `ime`, `keyboard`). No keyboard = cannot type wifi or app passwords.
- HDMI inputs and passthrough (names with `passthrough`, `hdmi`, `input`). Breaks game console, cable box, streaming stick.
- Remote and key handling (names often contain `key`, `remote`, `virtualkey`, `midware`, `bluetoothremote`)
- Wifi, network, bluetooth
- Video playback and DRM (`drm`, `widevine`, `tokenmanager`, `media`)
- Package installer, WebView
- Accessibility apps (TalkBack) if user uses them
- Apps the user chose to keep

## Sort every app into
| Group | Meaning | Examples (names vary by brand) |
|---|---|---|
| Keep | Needed | User apps, system, remote, inputs, keyboard |
| Batch A | Safe junk | Recommendations, log collector, factory menu, video-call, USB player, demo apps |
| Batch B | Small risk, or a feature user may want | Voice search (mic button stops), cast (phone cast stops), phone-remote app, setup wizard |
| Batch C | Only if no antenna | TV tuner apps (live TV, DTV, ATSC, ISDB, ATV). On some TVs the Live TV app also switches HDMI inputs: test HDMI after |
| Ask first | Has a downside user must accept | OTA update apps. Off = no security updates |

Unsure about an app? Put it in Keep.

## Warnings
- RAM 1 GB or less: gain is small. Suggest a streaming stick.
- Launcher disabled and screen blank: re-enable at once (see step 07).
- Factory reset turns every disabled app back on. Last-resort safety net.
