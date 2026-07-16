# Xreading Progress Checker

A self-contained student-facing reading-progress page for First Year English,
plus the local tools used to refresh its class snapshot.

## Files

- **reading-progress.html** — the published student page (a personal points
  calculator + a class "how we're climbing" ladder). This is the file embedded
  in an iframe on the class blog. Hosted via GitHub Pages.
- **admin.html** — a browser tool that reads an Xreading CSV export *locally*
  (nothing uploads) and produces an updated `reading-progress.html`.
- **update-reading-progress.py** — command-line equivalent of admin.html.

## Updating the published numbers

1. Export the latest class data from Xreading as a CSV.
2. Either:
   - open `admin.html`, drop in the CSV, then drop in `reading-progress.html`,
     and download the updated copy; **or**
   - run `python3 update-reading-progress.py "your-export.csv"`.
3. Commit and push the updated `reading-progress.html`:

   ```bash
   cd '/Users/Geoff/Library/CloudStorage/OneDrive-公立大学法人旭川市立大学/Xreading Progress Checker'
   git add reading-progress.html
   git commit -m "Update snapshot"
   git push
   ```

**`git push` *is* the deploy — there is no separate hosting step.** GitHub Pages
serves the site directly from this repo, so pushing republishes it automatically
(~1 minute later). The live page and the blog iframe then both show the new
numbers — nothing to upload anywhere, and nothing to change on the blog.

- Confirm it went live: the repo's **Actions** tab shows a "pages build and
  deployment" run — a green check means it's published. Or just reload the page.
- If your own browser still shows old numbers, hard-refresh (Cmd-Shift-R); it's
  just local cache.
- Only ever commit `reading-progress.html`. The CSV stays out (see Privacy).

## Privacy

The raw Xreading CSV contains student names, IDs, and usernames and is **never**
committed (see `.gitignore`). The published page contains only aggregate counts.
