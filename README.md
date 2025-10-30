# All BAND-MAID Setlists (Okyuji) 🎸

This project displays every **BAND-MAID okyuji (live concert)** setlist using data from a JSON file.  
Each entry expands to reveal the full setlist and includes a link to the corresponding **setlist.fm** page.

🔗 **View the setlists here:**  
[https://drivetimebm.github.io/BAND-MAID_okyuji/index.html](https://drivetimebm.github.io/BAND-MAID_reports/index.html)
---

## 🔧 Features

- Displays one line per unique **SetId** (each okyuji).  
- Click on a date line to **expand or collapse** the full setlist.  
- Each show includes a **Setlist.fm link** (opens in a new tab).  
- Shows are **sorted by date (newest first)** and songs are ordered correctly within each set.  
- Includes a **live song filter** — type a song name to see only shows where it was played.

---

## 📁 Project Structure

```
BAND-MAID_okyuji/
├── index.html # Main page displaying the setlists
├── setlists.json # JSON data file with all songs
└── README.md # This documentation
```

---

## 📜 JSON Format

Each record in `setlists.json` represents a single song in a show.  
Example:

```json
{
  "Date": "2025-10-26",
  "Venue": "Makuhari Messe Kokusai Tenjijou Hall 9-10-11",
  "City": "Chiba",
  "Country": "JP",
  "Tour": "",
  "URL": "https://www.setlist.fm/setlist/bandmaid/2025/makuhari-messe-kokusai-tenjijou-hall-9-10-11-chiba-japan-5b4ec36c.html",
  "Sequence": 1,
  "Song": "What is justice?",
  "SetId": 540
}
```

## 🧠 How It Works

- The browser fetches and parses setlists.json.
- All entries are sorted by Date (descending) and Sequence (ascending).
- A Map preserves insertion order while grouping by SetId.
- Each show is dynamically rendered into HTML.
- JavaScript handles expand/collapse and filtering interactions.

## 💡 Credits

- BAND-MAID Okyuji and MV Map: @simeonkr on Discord
- Code: HTML + CSS + JavaScript
- Concept: BAND-MAID Okyuji archive visualization

---

## All BAND-MAID Projects

- [BAND-MAID X/Twitter Archive](https://github.com/DriveTimeBM/BAND-MAID_tweets)
- [BAND-MAID Song Sorter (Ranker)](https://github.com/DriveTimeBM/BAND-MAID_song_sorter)
- [BAND-MAID GIF Catalog](https://github.com/DriveTimeBM/BAND-MAID_gifs)
- [BAND-MAID Reports](https://github.com/DriveTimeBM/BAND-MAID_reports)
- [BAND-MAID Instagram Archive](https://github.com/DriveTimeBM/BAND-MAID_instagram)
- [BAND-MAID GPT](https://github.com/DriveTimeBM/BAND-MAID_gpt)
- [BAND-MAID Prime Metadata](https://github.com/DriveTimeBM/BAND-MAID_prime)
- [BAND-MAID Creations](https://github.com/DriveTimeBM/BAND-MAID_creations)
- [BAND-MAID Setlists (Okyuji)](https://github.com/DriveTimeBM/BAND-MAID_okyuji)
- [BAND-MAID Translations](https://github.com/DriveTimeBM/BAND-MAID_translations)
