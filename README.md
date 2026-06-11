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
3. Commit and push the updated `reading-progress.html`. GitHub Pages redeploys
   automatically, and the iframe on the blog shows the new numbers.

## Privacy

The raw Xreading CSV contains student names, IDs, and usernames and is **never**
committed (see `.gitignore`). The published page contains only aggregate counts.
