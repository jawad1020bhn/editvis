# Career Player Lab

A browser-based career-mode scouting desk. Filter the full player pool by position, club, age, overall, potential, and growth; use quick target profiles for high-upside players, wonderkids, U21 prospects, young starters, breakout prospects, veteran leaders, hidden gems, free agents, priority/monitor lists, and value picks when source values exist; inspect detailed attribute reports; build a persistent shortlist; compare up to three players and download the comparison report; record private player notes and scouting priorities; quickly search players and app actions with the command palette; and export enriched scout results to CSV. All save parsing and filtering happen locally in the browser. Use **Ctrl/Cmd+K** for quick search or **/** to jump to the player search.

## Run

Serve the repository root with any static HTTP server, for example:

```sh
python3 -m http.server 4173 --bind 0.0.0.0
```

Then open `http://localhost:4173`.

## Design tooling

The project-local **Impeccable** agent skill (v4.8.0) is installed at `.agents/skills/impeccable/` for supported coding agents. Its detector engine downloads separately on first use.

## Settings and local files

Open **Settings** in the header to install a complete FIFA save data set. Select the career save (`.sav` or `.bin`), its matching `fifa_ng_db-meta.xml` schema, and the matching `fifa_ng_db.db` reference database, then choose **Save files & load players**. The files are validated, loaded locally, and retained in browser IndexedDB on this device for later visits. Use **Restore bundled files** to return to the included FIFA 14 data. Uploaded files are not sent to a server.

## Import data

Files successfully loaded through the main **Import Data** picker are also saved in browser IndexedDB and restored automatically on the next visit. This includes CSV/JSON exports and career saves with their selected schema/reference database. Choose **Restore bundled files** in Settings to clear the saved import and return to the included FIFA 14 data.

- **CSV:** first row should contain column headers. Common header names such as `player_name`, `overallrating`, `potential`, `position`, `club`, and `age` are recognized.
- **JSON:** accepts an array of player objects, or an object containing a `players`, `data`, or `records` array.
- The bundled career save loads with its matching `fifa_ng_db-meta.xml` schema and `fifa_ng_db.db` name lookup, all included here.
- **Other raw FIFA career saves:** select the save and its matching schema together. Add the matching base-game `fifa_ng_db.db` (usually under `Game/data/db`) to resolve names. The schema and database must match the game release.
- CSV/JSON exports with names are also supported. The explorer only displays player records; it does not modify or write back to the career save.
