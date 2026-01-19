# lipu sewi - Toki Pona Bible Reader

A lightweight, web-based reader for the Toki Pona translation of the Bible. This application pulls real-time data from the `lipu-sewi` repository and provides a clean interface for reading in both the Latin alphabet (*nasin Lasina*) and the Toki Pona hieroglyphic script (*sitelen pona*).

[**Live Demo**](https://lipu-sewi.github.io)

## 📖 Features

* **Dual Script Support:** Toggle between standard Latin text and *sitelen pona* using the `LinjaJS` font.
* **Dynamic Loading:** Fetches scripture directly from the [PaulieGlot/lipu-sewi](https://github.com/PaulieGlot/lipu-sewi) master branch.
* **Progress Tracking:** Visual indicators distinguish between "solidified" (finalized) and "unsolidified" (draft) translations using green and red border markers.
* **Verse Verification:** Integrates with the **Bolls Bible API** to compare the number of translated verses against the original text, highlighting missing content.
* **Deep Linking:** Share specific verses and display preferences via URL parameters (e.g., `?book=genesis&chapter=1&sitelen=true`).
* **Automatic Transliteration:** Automatically converts proper names (marked with `&` in the source) into Toki Pona phonology and cartouche-style *sitelen pona*.

## 🛠️ How It Works

### Data Sources
The app acts as a "headless" reader. It does not store the Bible text itself but fetches it on demand:
1.  **Text:** Fetched as `.txt` files from the `lipu-sewi` GitHub repository.
2.  **Metadata:** Book and chapter counts are hardcoded within the app.
3.  **Verse Counts:** Actual verse counts for progress tracking are fetched from the **Bolls Bible API**.
4.  **Names:** Proper names are resolved using `.csv` lookup tables for place names and people names.

### The "Sitelen Pona" Engine
The app uses the `LinjaJS` font to render Toki Pona glyphs. 
* **Ligatures:** The app enables `common-ligatures`, `discretionary-ligatures`, and `contextual` alternates to ensure that multi-word concepts and names render correctly.
* **Name Handling:** When a word starting with `&` is detected, the app looks up the Toki Pona equivalent and wraps it in a `.name-rect` class to create the traditional "name cartouche" border.

### URL Parameters
You can link directly to specific content using the following parameters:
* `testament`: `old_testament` or `new_testament`
* `book`: The slug of the book (e.g., `genesis`, `matthew`)
* `chapter`: The chapter number
* `verse`: The specific verse number to highlight and scroll to
* `sitelen`: Set to `true` to enable hieroglyph mode by default

## 🚀 Local Development

Since this is a client-side JavaScript application, you don't need a build server.

1.  Clone the repository.
2.  Open `index.html` in any modern web browser.
3.  *Note:* Because the app uses `fetch()`, you may need to run it via a local server (like `Live Server` in VS Code or `python3 -m http.server`) to avoid CORS issues when testing locally.

## ✒️ Credits

* **Translation:** [PaulieGlot and contributors](https://github.com/PaulieGlot/lipu-sewi).
* **Font:** `linja pona` (LinjaJS) by jan Same.
* **API:** Verse metadata provided by [Bolls Bible](https://bolls.life/api/).
