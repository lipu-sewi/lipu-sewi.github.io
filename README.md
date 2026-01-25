# lipu sewi - Toki Pona Bible Reader

A lightweight, web-based reader for the Toki Pona translation of the Bible. This application pulls real-time data from the `lipu-sewi` repository and provides a clean interface for reading in both the Latin alphabet (*nasin Lasina*) and the Toki Pona hieroglyphic script (*sitelen pona*).

[**Live Demo**](https://lipu-sewi.github.io)

## 📖 Features

* **Dual Script Support:** Toggle between standard Latin text and *sitelen pona* using the `nasin-nanpa` font. [etbcor/nasin-nanpa](https://github.com/etbcor/nasin-nanpa) for more.
* **Dynamic Loading:** Fetches scripture directly from the [PaulieGlot/lipu-sewi](https://github.com/PaulieGlot/lipu-sewi) master branch.
* **Progress Tracking:** Visual indicators distinguish between "solidified" (finalized) and "unsolidified" (draft) translations using green and red border markers.
* **Verse Verification:** Integrates with the **Bolls Bible API** to compare the number of translated verses against the original text, highlighting missing content.
* **Deep Linking:** Share specific verses and display preferences via URL parameters (e.g., `?cite=Genesis 1:3&sitelen=true`).
* **Automatic Transliteration:** Automatically converts proper names (marked with `&` in the source) into Toki Pona phonology and cartouche-style *sitelen pona*.

## 🛠️ How It Works

### Data Sources
The app acts as a "headless" reader. It does not store the Bible text itself but fetches it on demand:
1.  **Text:** Fetched as `.txt` files from the `lipu-sewi` GitHub repository.
2.  **Metadata:** Book and chapter counts are hardcoded within the app.
3.  **Verse Counts:** Actual verse counts for progress tracking are fetched from the **Bolls Bible API**.
4.  **Names:** Proper names are resolved using `.csv` lookup tables for place names and people names.

### The "Sitelen Pona" Engine
The app uses the `nasin-nanpa` font to render Toki Pona glyphs. 
* **Ligatures:** The app enables `common-ligatures`, `discretionary-ligatures`, and `contextual` alternates to ensure that multi-word concepts and names render correctly.
* **Name Handling:** Names are rendered using [nasin sitelen kalama pi linja lili](https://sona.pona.la/wiki/nasin_sitelen_kalama_pi_linja_lili) for the first term in a chapter. All subsequent references use the first character only. This is accomplished by the font itself, which converts something like `sewi​[e,lon,,wile,,n,]` into a clean rendering of `sewi Elowin`, with the tick marks below each word to indicate how many letters of the word come.​

### URL Parameters
You can link directly to specific content using the following parameters:
* `cite`: `$book $chapter:$verse` (verse is optional here, e.g. `?cite=Genesis 1:4`, `?cite=Job 1`)
* `sitelen`: Set to `true` to enable hieroglyph mode by default

## 🚀 Local Development

Since this is a client-side JavaScript application, you don't need a build server.

1.  Clone the repository.
2.  Open `index.html` in any modern web browser.
3.  *Note:* Because the app uses `fetch()`, you may need to run it via a local server (like `Live Server` in VS Code or `python3 -m http.server`) to avoid CORS issues when testing locally.

## ✒️ Credits

* **Translation:** [PaulieGlot and contributors](https://github.com/PaulieGlot/lipu-sewi).
* **Font:** `nasin nanpa` by etbcor.
* **API:** Verse metadata provided by [Bolls Bible](https://bolls.life/api/).
* **Styling and Design:** jan Kitelen, jan Metamepiso, and others on Toki Pona Discord
