# Smart Schedule Auditor

**Smart Schedule Auditor** is a browser-based tool that cross-references an Excel schedule against a master "source of truth" — either a Cruise Compass PDF or a TESS report — using the **Google Gemini** API to detect mismatches in activities, timings and venues.

## Key Features

* **Two source-of-truth modes**: compare against a master PDF, or against a DM export from TESS (.xlsx / .csv).
* **Fuzzy title & venue matching**: recognises synonyms (e.g. "Pool Deck" = "Poolside", "Photo Gallery" = "Focus Photo Gallery") and loose title variants, while requiring times to match exactly.
* **Real-time system console**: each step of the audit is logged as it happens, newest entry at the top, with an OK / WAITING / ERROR status.
* **Structured report**: results are grouped into missing or extra activities, time mismatches, venue mismatches, and duplicates.

## Live Deployment

The tool is hosted and accessible at:
**[https://smartauditor.asariko.net](https://smartauditor.asariko.net)**

## How to Use

1. **API Key**: Enter your Gemini API key (obtainable from [Google AI Studio](https://aistudio.google.com/)).
2. **Upload Excel**: Select the AEM schedule you want to audit (.xlsx or .csv).
3. **Upload the master**: Either the Compass PDF (upload only the page containing the Daily Planner), **or** a DM export from TESS.
4. **Run Audit**: Click **Run Audit** and follow the console as it works.

## Security & Data Privacy

This application is built with a **privacy-first** architecture:

* **Client-side parsing**: Your Excel and PDF files are read and parsed entirely in your browser. The files themselves are never uploaded anywhere.
* **No data retention**: Nothing is saved, stored or cached on any server of ours — there is no server.
* **Instant wipe**: Refreshing the page or closing the tab clears all uploaded data and extracted text from memory.
* **Volatile API key**: `localStorage` is not used. Your key is cleared on exit or refresh, so it must be entered fresh each session.
* **Direct API communication**: The extracted *text* of your documents is sent directly from your browser to Google's Generative Language API over HTTPS, so that Gemini can perform the comparison. It does not pass through any intermediary.

> Note: the audit is performed by Google's API, so the text content of your schedules does leave your browser to reach Google. What never leaves is the original files themselves and your API key. If your documents are confidential, review [Google's API terms](https://ai.google.dev/gemini-api/terms) before use.

## Built With

* [PDF.js](https://mozilla.github.io/pdf.js/) — client-side PDF text extraction.
* [SheetJS](https://sheetjs.com/) — Excel and CSV parsing.
* [Google Gemini API](https://ai.google.dev/) — the reasoning engine that performs the comparison.

## Repository contents

| File | Purpose |
|---|---|
| `index.html` | The tool. Open in a browser, or use the hosted version. |
| `assets/`, `style.css`, `script.js`, `tailwind.css` | Site styling and shared header/footer behaviour. |
| `tailwind.config.js`, `in.css` | Build inputs used to regenerate `tailwind.css`. Not needed at runtime. |
| `CNAME` | Custom domain for GitHub Pages. |

To regenerate the stylesheet after changing any classes in `index.html`:

```bash
npx tailwindcss@3 -c tailwind.config.js -i in.css -o tailwind.css --minify
```

---

Free to use, not for sale. Licensed under the [PolyForm Noncommercial License 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0) — commercial use, including use for business labor reduction, is prohibited.

© 2026 Asariko.net
