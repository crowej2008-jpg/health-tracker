# Soft lock: Shortcut setup (iPhone, iOS 16)

The app (v16+) syncs `lockTime` to `status.json`, e.g. `2026-11-20 13:30`.
Once the current time is past it, Instagram + games are locked. The app works out every rule
(deadlines, weekends, spending lock until Monday, app not opened today); the Shortcut only compares times.

## 1. Shortcut "Lock Check" (6 actions)
1. **Get Contents of URL**: your sync link (ends in `/status.json`).
2. **Get Dictionary Value**: key `lockTime`.
3. **Get Dates from Input** (the Dictionary Value).
4. **If** *Dates* **is before** *Current Date*
5. **Show Notification** "Locked: open the health app", then **Go to Home Screen**. Then **End If**.

Don't use Open URLs: it opens the app in Safari, which has separate storage that never syncs.

## 2. Automation
Automation → **+** → Create Personal Automation → **App** → pick Instagram + games → **Is Opened** → Next →
**Run Shortcut** → Lock Check → Next → turn **off** "Ask Before Running" → Done.

The red 🔒 bar in the app says what to log to unlock. Offline = Instagram stays open.
