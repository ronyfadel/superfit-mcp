# SuperFit for Claude

Coach with your SuperFit training data in Claude. Once connected, Claude can read your program, calendar, workouts, lift history, recommendations and coach notes, and make changes for you: log a session, adjust the next few days around soreness or travel, swap or push back sessions, update a session type, set your loads for next week, or build your next training block. Changes show up in the SuperFit app the next time you open it.

It works in Claude on the web (claude.ai), the Claude desktop and mobile apps, and Claude Code.

## What you need

- The SuperFit app, signed in, on a version with **Settings → Connect Claude**.
- A Claude plan that lets you add custom connectors (for claude.ai and the Claude apps), or Claude Code.

## Connect in claude.ai or the Claude apps

1. In Claude, open **Settings → Connectors** and choose **Add custom connector**.
2. Name it `SuperFit` and paste this URL:

   ```
   https://superfit-mcp.rony-cloudflare.workers.dev/mcp
   ```

3. Choose **Connect**. A SuperFit page opens and asks for a code.
4. In the SuperFit app, go to **Settings → Connect Claude** and tap **Get a pairing code**. Enter it on the page. It works once, for 10 minutes.

A connector you add on claude.ai is also available in the Claude desktop and mobile apps. In a chat, make sure SuperFit is turned on in the tools menu.

**Optional:** for coaching guidance on top of the data, add the skill in [`skills/superfit-coach`](skills/superfit-coach). Download it as a zip and upload it under **Settings → Capabilities → Skills**.

## Connect in Claude Code

Install the plugin, which includes the connector and the coaching skill:

```
/plugin marketplace add ronyfadel/superfit-claude
/plugin install superfit@superfit
```

Or add only the connector:

```sh
claude mcp add --transport http superfit https://superfit-mcp.rony-cloudflare.workers.dev/mcp
```

Then run `/mcp`, choose **superfit** and authenticate. Your browser opens the SuperFit page; enter a pairing code from the app as above.

## Things to ask

- "How did this week go? Anything I should change for next week?"
- "How's my squat progressing over the last two months?"
- "Yesterday: deadlift 120 kg 3×5 at 2 RIR, pull-ups +7.5 kg 3×6, rows 26 kg 2×12. Log it."
- "My legs are wrecked after padel. Make the next two days easier."
- "I'm travelling Monday to Wednesday with only a hotel gym. Sort out my week."
- "Push everything back three days, I'm sick."
- "Plan my next 8-week block toward a half marathon on June 14."

## What Claude can do

| Read | Change |
|---|---|
| Overview of your training as of today | Log a session's results, and complete it |
| Calendar for any dates | Correct a logged session |
| One day in full, with every set logged | Log an activity outside the program |
| Your program's structure | Set recommendations (loads, pacing) |
| Workout logs | Replace a day's session, or add a workout |
| History of any exercise | Swap days, push back or bring forward |
| The program's change history | Change specific dates, session types, schedule, phases |
| | Build or replace your program |
| | Send a proposed change to the app for you to apply |
| | Undo program changes |
| | Remember or forget notes about you |

Past dates and completed sessions stay as they were when the program changes. Every program change is kept in its history (the Program tab in the app), so it can be undone.

Claude asks before using a tool, unless you allow it to always use that tool.

## Disconnect

In the SuperFit app, go to **Settings → Connect Claude**, then swipe the connection and tap **Disconnect**. Claude's access ends right away. You can also remove the connector in Claude's settings.

## Privacy

- Connecting gives that Claude account access to your SuperFit training data: program, workouts, recommendations, coach notes, activities and profile. Your chat with the in-app coach isn't shared.
- What you discuss in Claude is handled by Anthropic under your Claude account's terms and settings.
- SuperFit stores only what the connection needs: the connected app's name, your time zone (so "today" is right), when it was last used, and hashed access tokens. Access tokens last an hour and are renewed while you stay connected; disconnecting deletes them.
- Changes Claude makes are saved to your SuperFit account like changes from your phone, and are listed in the app as coming from Claude.

## Support

Open an issue in this repository.
