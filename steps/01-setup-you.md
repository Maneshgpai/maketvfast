# 01 Setup (you do this, no AI needed)

**Who:** You
**Time:** about 15 minutes
**Goal:** Check your TV works with this guide, put ADB on your PC, and connect PC to TV.

ADB is a free Google tool. It lets your PC send commands to your TV.

## Part A: Check your TV
1. Find your TV brand. Look at the TV box, the remote, or Settings > About.
2. Pick your row:

| Your TV | Next |
|---|---|
| Android TV, Google TV, Fire TV (Sony, TCL, Xiaomi, Acer, Hisense, Philips, Shield, Fire stick...) | Go on |
| Samsung, LG, Roku | Stop. This guide does not work. Only the [ad blocker](06b-adblock-dns.md) can be done by hand |

Not sure? Home screen with Google or Android logo = go on.

## Part B: Put ADB on your PC
Open a terminal (Windows: search "PowerShell"; Mac: search "Terminal"; Linux: Ctrl+Alt+T). Paste ONE line for your PC, press Enter. Type your PC password if asked.

| PC | Line |
|---|---|
| Windows | `winget install Google.PlatformTools` |
| Mac | `brew install android-platform-tools` |
| Linux (Ubuntu, Debian) | `sudo apt install adb` |

Close the terminal. Open a new one. Type `adb version`, press Enter.
- Shows a version number: done.
- Says "not found": redo the line. Mac without `brew`? Get it from brew.sh first.

## Part C: Turn on debugging on the TV
Menu names differ by TV. Use your row.

1. Open developer mode. Click the item **7 times** until it says "You are a developer".
   - Android TV: Settings > Device Preferences > About > **Build**
   - Google TV: Settings > System > About > **Android TV OS build**
   - Fire TV: Settings > My Fire TV > About > your **device name**
2. Go back one level. Open **Developer options**.
3. Turn ON **USB debugging** (Fire TV: **ADB debugging**).
4. Turn ON **Network debugging** or **Wireless debugging** if you see it.

## Part D: Find the TV address (IP)
1. TV: Settings > Network (or Network & Internet). Click your wifi.
2. Write down the **IP address**. Looks like `192.168.1.50`.
3. PC must be on the same wifi as the TV.

## Part E: Connect PC to TV
1. In the terminal type (use your IP): `adb connect 192.168.1.50:5555` and press Enter.
2. Watch the TV. A popup asks "Allow USB debugging?". Tick **Always allow**. Click **Allow**.
3. Type `adb devices` and press Enter.
   - Line ends with `device`: done.
   - Line ends with `unauthorized`: click Allow on the TV, run `adb devices` again.
   - Nothing listed: see "If it fails" below.

## If it fails
- Restart the TV. Check PC and TV are on the same wifi. Try again.
- TV has **Wireless debugging** (Android 11 or newer)? Then:
  1. On the TV open Wireless debugging > **Pair device with pairing code**. It shows an IP, a **pair port** and a 6-digit code.
  2. On the PC type `adb pair 192.168.1.50:PAIRPORT` (use the pair port). Type the code.
  3. Go back to the main Wireless debugging screen. Note the **IP and port** shown there (not the pair port).
  4. On the PC type `adb connect 192.168.1.50:PORT` (use that port).
- Router has "client isolation" or a guest wifi? Move PC and TV to the main wifi.

## Done when
`adb devices` shows your TV as `device`. Keep the terminal open. Go to [step 02](02-diagnose.md) or paste the [master prompt](../prompts/master-prompt.md) into your AI app.
