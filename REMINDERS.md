# Reminders: Shortcut setup (iPhone, iOS 16)

The app (v17+) syncs a `remind` list to `status.json`, keyed by date + hour, e.g. `"2026-11-21 15": "🚶 Walk 1 time…"`.
Only things you haven't logged yet get a reminder, so if it's done, your phone stays quiet.
Covers today plus the next 2 days, so open the app at least every couple of days.

## 1. Shortcut "Reminder Check" (6 actions)
1. **Get Contents of URL**: your sync link (the same one as Lock Check).
2. **Get Dictionary Value**: key `remind`.
3. **Format Date**: Date = *Current Date*, Date Format = **Custom**, type `yyyy-MM-dd HH`.
4. **Get Dictionary Value**: key = *Formatted Date* (tap the key field → pick the blue variable),
   in = *Dictionary Value* (tap → Select Variable → the one from step 2).
5. **If** *Dictionary Value* **has any value**
6. **Show Notification**: *Dictionary Value*. Then **End If**.

## 2. Automations (one per time, all run Reminder Check)
Automation → **+** → Create Personal Automation → **Time of Day** → set the time → Daily → Next →
**Run Shortcut** → Reminder Check → Next → turn **off** "Ask Before Running" → Done.

| Time | Reminder |
|---|---|
| 7:15 am | Log sleep + mood |
| 12:00 pm (Weekly: Sat + Sun) | Laundry / Sunday check-in |
| 1:15 pm | Log lunch |
| 3:00 pm | Walk 1 |
| 7:30 pm | Walk 2 |
| 9:30 pm | Finish today's check-in |
| 10:30 pm | Wind down |
