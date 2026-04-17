# BAND-MAID Okyuji — Setlist Archive

A static, single-page setlist viewer for BAND-MAID live performances. No build step, no dependencies, no server — just an HTML file and a JSON file served via GitHub Pages.

🔗 **View the archive here:**  
[https://drivetimebm.github.io/BAND-MAID_okyuji/](https://drivetimebm.github.io/BAND-MAID_okyuji/)

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire app — markup, styles, and script |
| `setlists.json` | Source data — one record per song per show |
| `favicon.png` | Site icon, also shown in the app header |

## Data Format

`setlists.json` is a flat array of song-performance records. Every song in a show gets its own record. Shows with the same date are disambiguated by `SetId`.

```json
[
  {
    "Date":     "2026-04-11",
    "Venue":    "KT Zepp Yokohama",
    "City":     "Yokohama",
    "Country":  "JP",
    "Tour":     "WORLD TOUR 2026",
    "URL":      "https://www.setlist.fm/setlist/...",
    "Sequence": 1,
    "Song":     "Unleash!!!!!",
    "SetId":    550
  }
]
```

| Field | Type | Notes |
|---|---|---|
| `Date` | string | ISO 8601 (`YYYY-MM-DD`) |
| `Venue` | string | Venue name |
| `City` | string | City name |
| `Country` | string | ISO country code |
| `Tour` | string | Tour name (optional) |
| `URL` | string | setlist.fm URL (optional) |
| `Sequence` | number | Song's position in the setlist |
| `Song` | string | Song title |
| `SetId` | number | Unique identifier for a single show; allows multiple shows on the same date |

## Views

### By Show
Cards grouped by show in data order, each showing the setlist in `Sequence` order. The header displays date, venue, city/country, tour, and a link to setlist.fm when a URL is present.

### By Song
Cards grouped by unique song title, sorted alphabetically. Each card lists every show where that song was performed, sorted by date, with its setlist position.

## Filtering

Both views support simultaneous filtering by **Date** and **Song**. Filters are substring matches and are case-insensitive.

- **Date** matches anywhere in the `Date` field — so `2026` matches all of 2026, `2026-04` matches April 2026, and `2026-04-11` matches an exact date.
- **Song** matches anywhere in the song title — so `love` would match any song containing that string.

Clicking a song title in the **By Show** view sets the Song filter to that exact title. Clicking a date in the **By Song** view sets the Date filter to that exact date. Either click clears the other filter.

## URL Parameters

The current filter state is always reflected in the URL query string, making any filtered view directly shareable or linkable.

| Parameter | Example | Effect |
|---|---|---|
| `date` | `?date=2026-04-11` | Filter to a specific date |
| `date` | `?date=2026` | Filter to a full year |
| `song` | `?song=Unleash!!!!!` | Filter to shows containing that song |
| `mode` | `?mode=songs` | Open in By Song view instead of By Show |

Parameters can be combined:

```
index.html?mode=songs&song=Magie
index.html?date=2026&mode=shows
```

## Controls

| Control | Action |
|---|---|
| **By Show / By Song** | Switch between the two views |
| **Date** input | Filter by date substring |
| **Song** input | Filter by song title substring |
| **Clear** | Remove all active filters |
| **Collapse All** | Collapse every card in the current view |
| **Expand All** | Expand every card in the current view |
| **⎘ Copy URL** | Copy the current filtered URL to the clipboard |

Individual cards can also be collapsed or expanded by clicking their header row.

## GitHub Pages

The app fetches `setlists.json` relative to `index.html`, so it works as-is when both files are in the repo root and GitHub Pages is pointed at the `main` branch root.

It can also be embedded as a view inside a parent app (such as BAND-MAID Unofficial) via iframe. URL parameters are written with `history.replaceState` against the page's own path and do not interfere with any parent frame.
