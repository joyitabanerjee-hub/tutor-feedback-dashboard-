# How to Update the Dashboard Summary

**Dashboard URL:** https://joyitabanerjee-hub.github.io/tutor-feedback-dashboard-/
**GitHub Repo:** https://github.com/joyitabanerjee-hub/tutor-feedback-dashboard-

---

## First-Time Setup (do this once)

1. Go to your repo: https://github.com/joyitabanerjee-hub/tutor-feedback-dashboard-
2. Click **"Add file" > "Upload files"**
3. Drag in these 2 files from `Desktop > Joyita > Tutor Feedback`:
   - `index.html`
   - `summary-config.json`
4. Click **"Commit changes"**

---

## How to Update the Summary Text (anytime)

1. Go to your repo: https://github.com/joyitabanerjee-hub/tutor-feedback-dashboard-
2. Click on **`summary-config.json`**
3. Click the **pencil icon** (top right) to edit
4. Change the text — add, remove, or rewrite items
5. Click **"Commit changes"**
6. Wait 1-2 minutes — the live dashboard updates automatically

---

## What the Config File Looks Like

```json
{
  "immediate_actions": [
    {
      "title": "Action title here",
      "description": "What you're doing about it."
    },
    {
      "title": "Another action",
      "description": "Details here."
    }
  ],
  "planned_actions": [
    {
      "title": "Future item title",
      "description": "Why it's planned, not immediate."
    }
  ]
}
```

- **immediate_actions** = "What We're Doing Right Now" (tagged In Progress)
- **planned_actions** = "On Our Radar" (tagged Planned)
- You can have as many items as you want in each list
- Keep the JSON format — make sure every `{` has a `}`, every `[` has a `]`, and strings use `"double quotes"`

---

## How to Update the Dashboard Code (index.html)

Only needed if the dashboard itself changes (not for summary text updates).

1. Go to your repo
2. Click **"Add file" > "Upload files"**
3. Drag in the new `index.html` from `Desktop > Joyita > Tutor Feedback`
4. Click **"Commit changes"**

---

## What Updates Automatically (no action needed)

- **Tutor feedback data** — fetched live from the Google Sheet every time someone opens the dashboard
- **All charts, stats, themes** — computed from the latest data
- **Tutor leaderboard** — always reflects current submissions

## What Needs Manual Update

- **Summary actions** — edit `summary-config.json` in GitHub (steps above)
- **Dashboard code** — re-upload `index.html` if the HTML/JS changes

---

## Troubleshooting

- **Dashboard shows "Local data file"** — Google Sheet may not be publicly accessible. Go to the Sheet > Share > "Anyone with the link can view"
- **Summary not updating** — Make sure `summary-config.json` is in the repo root (same level as `index.html`). Check for JSON syntax errors.
- **Site not loading** — Go to repo Settings > Pages and confirm it says "Your site is live". Branch should be `main`, folder `/`.
