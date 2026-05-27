# GRP Weekly Cash Position Dashboard

Weekly cash position dashboard for Golden Rule Practices. Hosted on GitHub Pages. Shareable URL. Historical weeks available via dropdown.

**Live URL (after setup):**
`https://goldenruleproperties.github.io/payables-dashboard/`

---

## One-time setup

### Step 1 — Create the repo

1. Go to github.com/GoldenRuleProperties
2. Click **New repository**
3. Name it exactly: `payables-dashboard`
4. Set to **Private**
5. Do NOT initialize with a README (you will push this folder)
6. Click **Create repository**

### Step 2 — Push these files via GitHub Desktop

1. Open **GitHub Desktop**
2. Click **File → Add Local Repository**
3. Browse to the folder containing these files
4. Click **Publish repository**
5. Set the name to `payables-dashboard`, org to `GoldenRuleProperties`, keep Private
6. Click **Publish**

### Step 3 — Enable GitHub Pages

1. Go to the repo on github.com
2. Click **Settings** (top menu)
3. Click **Pages** (left sidebar)
4. Under **Source**, select: **Deploy from a branch**
5. Branch: **main** / folder: **/ (root)**
6. Click **Save**

GitHub will show the live URL. It takes 1-2 minutes to go live the first time.

### Step 4 — Verify

Open the URL in a browser. You should see the dashboard with the week selector in the top right. Switch between weeks to confirm all three load correctly.

Share the URL with Trent and Tim. That URL never changes.

---

## Repo structure

```
payables-dashboard/
├── index.html          ← The entire dashboard (never needs to change)
├── README.md           ← This file
└── data/
    ├── index.json      ← List of available weekly files (newest first)
    ├── 2026-05-15.json
    ├── 2026-05-08.json
    └── 2026-04-24.json
```

---

## Weekly workflow — every Thursday

### Step 1 — Get the JSON from Claude

Upload the Payables Template, P&L export, and meeting transcript to Claude. Claude generates the weekly JSON file named `YYYY-MM-DD.json`.

### Step 2 — Save the JSON file

Save the file Claude produces into the `data/` folder of your local repo.

Example: `data/2026-05-22.json`

### Step 3 — Update data/index.json

Open `data/index.json` and add the new filename at the **top** of the array (newest first):

```json
[
  "2026-05-22.json",
  "2026-05-15.json",
  "2026-05-08.json",
  "2026-04-24.json"
]
```

### Step 4 — Commit and push via GitHub Desktop

1. Open GitHub Desktop
2. You will see two changed files: the new JSON and the updated `index.json`
3. Write a commit message: `Week ending May 22`
4. Click **Commit to main**
5. Click **Push origin**

The dashboard updates within 1-2 minutes. Refresh the URL.

---

## Troubleshooting

**Dashboard shows "failed to load" error**
- Confirm `data/index.json` was updated with the new filename
- Confirm the filename in `index.json` exactly matches the file in `/data/` (case-sensitive)
- Wait 2 minutes after pushing — GitHub Pages has a propagation delay
- Try a hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)

**Week selector shows wrong order**
- In `index.json`, newest date must be first in the array

**Numbers look wrong on the dashboard**
- The JSON is the source of truth. Open the JSON file directly to verify the numbers before assuming a dashboard issue.

**index.html never needs to be changed.**
The dashboard reads whatever JSON files are listed in `data/index.json`. Adding a new week is always just: drop the JSON file, update `index.json`, push.

---

Golden Rule Practices · Internal Use Only · Confidential
