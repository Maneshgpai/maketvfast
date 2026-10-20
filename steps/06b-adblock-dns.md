# 06b Optional: ad blocker (DNS)

**Who:** AI + you
**Goal:** Block ads with AdGuard DNS. No app to install. Not 100% (some in-app ads stay). App stops loading? Turn OFF first.

## You do
Open each of your apps after ON. Tell AI if any breaks. On Samsung, LG, Roku: do TV or router settings by hand.

## AI does
Read Android version: `adb shell getprop ro.build.version.release`. Save current values first: `adb shell settings get global private_dns_mode` and `private_dns_specifier`. Pick ONE row:

| TV | ON | OFF |
|---|---|---|
| **Android 9+, Google TV, Fire TV** (via ADB) | `adb shell settings put global private_dns_specifier dns.adguard-dns.com` then `adb shell settings put global private_dns_mode hostname` (this order: name first, else internet drops for a moment) | `adb shell settings put global private_dns_mode off` (automatic: `... private_dns_mode opportunistic`) |
| **Android 8 or older, old Fire OS** | No Private DNS. Use manual DNS or router (below) | Restore DNS |
| **Samsung, LG** (no ADB) | TV Settings > Network > IP/DNS > manual DNS `94.140.14.14` and `94.140.15.15` | Set DNS to Automatic |
| **Roku** | No DNS setting. Use router | Restore router DNS |
| **Any TV (whole home)** | Set AdGuard DNS in router | Restore router default |

Check: `adb shell settings get global private_dns_mode`. Then test internet: open YouTube. No internet? Run OFF line at once. Uncomment DNS lines in `restore.sh` so it resets `private_dns_mode` and `private_dns_specifier` to saved values (usually `opportunistic` and `null`). Log to `changes.log`.

## Prompt
```
You AI helper. User not expert. TALK CAVEMAN. Short. Simple words. Commands exact. Follow rules/safe-rules.md. Ask OK before any change.
Optional. Ask user want ad block? Yes: check Android version. Show only matching OS row. Ask OK. Turn ON. Ask user open each app. App broken? Turn OFF. Always show OFF line.
```

## Done when
Apps load fine. You know the OFF line.
