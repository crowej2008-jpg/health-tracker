# Soft lock: Shortcut setup (iPhone, iOS 16)

The app (v15+) adds these to `status.json`:
- `dayNum`: app day as a number, e.g. 20261120 (day runs 4am→4am)
- `lockAt`: hour the lock starts, on a 4am clock (13.5 = 1:30pm, 21 = 9pm, 25 = 1am). 99 = nothing missing
- `tomorrowLockAt`: first deadline of the next day (used if the app wasn't opened today)
- `spendUntil`: next Monday (e.g. 20261123) if over the wants/games limit, else 0
- `lockMsg`: what to do to unlock

## 1. Shortcut "Lock Check"
1. **Get Contents of URL**: paste your sync link (the one ending in `/status.json`).
2. **Adjust Date**: Subtract 4 hours from Current Date.
3. **Format Date** (Adjusted Date), Custom `yyyyMMdd` → rename the result **Today**.
4. **Format Date** (Adjusted Date), Custom `H` → **H**. Another **Format Date**, Custom `m` → **M**.
5. **Calculate Expression**: `H + 4 + M / 60` → **Hour**.
6. **Get Dictionary Value** `spendUntil` from Contents of URL.
   **If** it is greater than **Today** → **Show Notification** "Over the wants limit: locked until Monday", open the health app, **Stop This Shortcut**. End If.
7. **Get Dictionary Value** `dayNum`. **If** it is **Today**:
   - **Get Dictionary Value** `lockAt` → **Set Variable** Limit
   - Otherwise: **Get Dictionary Value** `tomorrowLockAt` → **Set Variable** Limit
   - End If
8. **If Hour** is greater than or equal to **Limit**:
   **Get Dictionary Value** `lockMsg` → **Show Notification** (it; if empty: "Open the health app and log today"), open the health app the same way your Log shortcut does, **Stop This Shortcut**.
   End If

## 2. Automation
Shortcuts → Automation → **+** → Create Personal Automation → **App** → choose Instagram + your games → **Is Opened** → Next → Run Shortcut **Lock Check** → Next → turn **off** "Ask Before Running".

## Test
Before 1:30pm on a weekday nothing locks. To test now: in the app, delete today's food, then open Instagram after the deadline. You should bounce to the health app. The app also shows a red 🔒 bar when you're locked.
If the phone is offline, the Shortcut errors and Instagram stays open (fails open).
