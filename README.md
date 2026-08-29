# Officer Directory Portal — v2 with Admin

A single-file HTML portal for managing departmental seniority and retirement data. **No coding required** — administrators customise the portal through a built-in admin interface, upload data via Excel, and download an updated portal file to share.

## What's in this bundle

- **`civillist_irs.html`** — fully-populated IRS Civil List (Income Tax Service, 987 officers). Use as-is, or as a working reference.
- **`template_blank.html`** — clean starting template for any department. Sign in, customize, upload your data, download your version.
- **`README.md`** — this file.

## Features

**For all users:**
- **Dashboard** with officer count, grade-wise breakdown, upcoming retirements
- **Quick Lookup** with fuzzy name search and identifier search
- **Query Builder** with grade/batch/date/preset filters
- **Full List** with sortable columns and grade filter
- **Personal notes** per officer (browser-local)
- **CSV and Excel export** of any filtered view
- **Mobile-friendly** layout with drawer navigation
- Works completely offline once loaded

**For administrators (protected by passcode):**
- **Settings tab** — edit portal title, labels, source note, retirement rule (age 55/58/60/62/65/67/70; end of birth month, end of month before, or exact birthday), grades with custom colours
- **Data tab** — upload .xlsx/.xls/.csv with intelligent column-header mapping. Preview and validate before replacing dataset.
- **Publish tab** — download a new HTML file with all changes baked in. Share or upload to make changes permanent for everyone.
- **Password tab** — change the admin passcode

## Getting started in 3 steps

### Step 1: Open the template

Open `template_blank.html` in any modern browser (Chrome, Safari, Firefox, Edge). You'll see a sample portal with 8 example officers.

### Step 2: Sign in as admin

Click the **Admin** tab in the sidebar. Enter the default passcode: **`admin123`**

Go to the **Password** tab first and change it. The default is a placeholder — don't use it for a shared portal.

### Step 3: Customize and upload your data

**In the Settings tab:**
- Change Portal title, Eyebrow, Subtitle to match your service
- Update the Identifier label ("Civil Code", "Cadre Number", "PF Number", etc.)
- Update the Batch label ("Batch", "Allotment Year")
- Choose retirement age and rule
- Edit the Grades list — click × to remove sample grades, click "+ Add Grade" to add yours. Pick badge colours by clicking the colour squares.
- Click **Apply Settings** at the bottom

**In the Data tab:**
- Click the upload zone (or drag a file onto it)
- Select your Excel (.xlsx) or CSV file
- The portal auto-detects your column headers and shows a mapping form
- Confirm which column is Identifier / Name / DOB / Grade / Remarks
- Click **Preview & Validate** to check for errors row-by-row
- Click **Replace dataset** when the preview looks correct

**In the Publish tab:**
- Give the download a filename (e.g. `ias_civillist.html`)
- Click **Download Updated Portal**
- The downloaded file contains all your settings, dataset, and custom passcode — permanently baked in
- Share this file, upload to your host, or open it anywhere. Anyone opening it sees your customised portal.

That's it. You never touched any code.

## Excel format for upload

Any column headers work — the portal auto-guesses common ones and lets you map them manually. Recommended columns:

| Column | What it is | Notes |
|---|---|---|
| Identifier | Unique code per officer | e.g. Civil Code, Cadre Number, PF Number |
| Name | Full name | Any text |
| DOB | Date of birth | `dd.mm.yyyy`, `dd-mm-yyyy`, `yyyy-mm-dd`, or Excel date cells all work |
| Grade | Grade/designation | Should match one of your CONFIG grades |
| Remarks | Optional notes | e.g. "Deputation", "ITAT", "VRS w.e.f. dd.mm.yyyy" |

If a grade in your Excel doesn't match your configured grades, the portal warns you but still imports the row. Add the missing grade in Settings and re-upload, or edit the row later.

## How the "Publish" workflow works

The portal is a single HTML file. Your admin edits initially save to browser storage (fast, private, per-device). Clicking **Download Updated Portal** creates a fresh HTML file where your CONFIG settings and dataset are the new defaults — anyone opening that downloaded file starts from those values.

**Typical workflow:**
1. Admin opens portal, signs in, uploads new Excel, updates title, downloads new HTML
2. Admin shares the new HTML with colleagues (email, shared drive, cloud host)
3. Colleagues open the new HTML — they see the current data and settings
4. Personal notes and edits by each user still save to their own browser separately

## Deployment options

**Option A: Share the file directly**
Email or share via cloud storage. Anyone opens the HTML in a browser. No hosting needed. Best for small teams.

**Option B: Host on the web**
Upload to any static host (Hostinger, Netlify, GitHub Pages, your own server). Everyone opens the same URL. Add directory password protection on the host if data is sensitive. Best for repeated access across devices.

**iPhone / iCloud note**: iOS previews HTML files with JavaScript disabled. If you plan iPhone access, host the file on the web (Option B) instead of opening from Files/iCloud. Once hosted, Safari on iPhone can "Add to Home Screen" for one-tap access.

## Limitations

- **Local edits per browser**: Personal notes and per-officer corrections save to each user's own browser. Not synced across users. For shared updates, admin uses the Publish workflow.
- **Soft authentication**: The passcode gates casual access. A technical user could bypass it by reading the HTML. Adequate for a public seniority list; not for confidential data.
- **JavaScript required**: Won't work with JS disabled, and won't render in iOS Files-app preview.
- **Single dataset per file**: One instance per portal. For multiple departments, deploy separate files.
- **No collaborative editing**: Each user's browser storage is independent.

## Adapting for non-government use

Any roster works: replace grade names with designations, retirement age with contract expiry, etc.

- **Corporate org chart** — Identifier = Employee ID, Grade = Job Level, Retirement = Contract End
- **Alumni directory** — Identifier = Roll Number, Grade = Batch Year, DOB drives age calculation
- **Academic faculty** — Grade = Professor/Assoc/Asst, standard retirement rules

The engine treats data as generic rows; naming it "officer" is convention, not constraint.

## Version 2 changes from v1

- Added Admin section with passcode-gated tabs
- Settings, Data, Publish, Password sub-tabs
- Excel/CSV upload with intelligent column mapping and validation
- Runtime CONFIG editing (labels, colours, retirement rules, grades)
- HTML download that bakes current settings into a new file
- Full mobile responsiveness for admin forms
- Per-instance storage keys so multiple portals don't collide in the browser

## Credits

Engine and template by Claude (Anthropic), 2026. Reference IRS dataset compiled from CBDT Circular F.No. A-23012/1/2021-Ad.VI dated 03.03.2025. Free to adapt, modify, and redistribute.
