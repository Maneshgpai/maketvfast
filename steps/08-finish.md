# 08 Finish: lock TV again (you do this)

**Who:** You
**Goal:** Close the door. Debugging left ON lets any device on your wifi ask to control the TV.

## Do
1. In the PC terminal type `adb disconnect` and press Enter.
2. On the TV open Settings > Developer options.
3. Turn OFF **USB debugging** and **Network / Wireless debugging**.
4. Optional: click **Revoke USB debugging authorizations**.
5. Keep `restore.sh`, `changes.log` and the backup files on your PC. Do not share them.

## Need to undo later?
Do [step 01](01-setup-you.md) parts C to E again. Then use [step 07](07-undo.md).

## Done when
Debugging is OFF. Files are saved on your PC.
