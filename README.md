# Vendor Spec raid site

Two static pages, no backend:

- `index.html` – public raid groups (for all members)
- `officers.html` – officer hub (roster, raid leads & times, socials list)

The data lives in two Google Sheets that officers edit together:

| Sheet | Tabs | Who can see it |
|---|---|---|
| Vendor Spec – Raid Groups | Groups, Schedule | Public (feeds `index.html`) |
| Vendor Spec – Officers | Roster, Socials, Plan | Officers only |

## 1. Create the Google Sheets (once)

1. In Google Drive: **New → File upload**, upload `Vendor-Spec-Raid-Groups.xlsx` and `Vendor-Spec-Officers.xlsx`.
2. Open each one and choose **File → Save as Google Sheets**. Use those copies from now on.
3. **Share** both sheets with your officers as **Editor**. Don't share the Officers sheet with anyone else.

## 2. Publish the sheets as CSV

For each sheet: **File → Share → Publish to web**.

- Under *Link*, pick one tab (e.g. *Groups*) and the format *Comma-separated values (.csv)*, then **Publish**. Copy the link.
- Repeat for each tab you need: **Groups** and **Schedule** (Raid Groups sheet), and **Roster**, **Socials** and **Plan** (Officers sheet).

Each link looks like `https://docs.google.com/spreadsheets/d/e/2PACX-…/pub?gid=123&single=true&output=csv`.

## 3. Connect the pages

- **Public page:** open `index.html` and paste the Groups and Schedule links into `GROUPS_CSV` and `SCHEDULE_CSV` at the top. Until you do, it shows the 26 Nov snapshot.
- **Officer page:** don't put the officer links in the code (the repo is public). Each officer opens `officers.html`, goes to **Sheet links**, and pastes the Roster, Socials and Plan links once. They're saved only in that officer's browser.

The Officers CSV links work for anyone who has them, so only send them to officers.

## 4. Put it online (GitHub Pages)

1. Create a **public** GitHub repository, e.g. `vendor-spec-raids`.
2. Upload `index.html`, `officers.html` and this README (**Add file → Upload files**).
3. **Settings → Pages → Build and deployment → Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After about a minute the site is at `https://<your-user>.github.io/vendor-spec-raids/`. The officer page is at `…/officers.html`.

Don't upload the .xlsx files to the public repo, since the Officers one has private notes.

## Editing

- Change groups, raid leaders or the banner message in the **Raid Groups** sheet. The public page updates within about 5 minutes (Google refreshes published data on its own schedule).
- Change roster notes, statuses and the socials list in the **Officers** sheet. Reload the officer page to see them.
- Keep the header rows and tab names as they are: the pages read columns by name.
