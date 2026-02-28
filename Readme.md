# Smart Schedule Auditor

**Smart Schedule Auditor** is a high-performance, browser-based tool designed to cross-reference Excel schedules against a Master PDF "Source of Truth." Utilizing the **Google Gemini 3.0 Flash** model, it detects mismatches in activities, timings, and venues with professional-grade precision.



## Key Features

* **PDF Logic Processing**: Treats the PDF as the absolute source of truth for the audit.
* **Fuzzy Venue & Title Matching**: Intelligent logic that recognizes synonyms (e.g., "Chapel" = "Skylight Chapel") and ignores trademark symbols (®, ™).
* **Real-Time System Console**: A 6-stage lifecycle log that flows from **Top to Bottom**, allowing you to track the audit as it happens.
* **Live Token & Cost Tracking**: Calculates the exact number of input/output tokens used and provides a live USD cost estimate for every audit.

## Live Deployment

The tool is hosted and accessible at:
**[https://smartauditor.asariko.net](https://smartauditor.asariko.net)**

## How to Use

1.  **API Key**: Enter your Gemini API Key (obtainable from [Google AI Studio](https://aistudio.google.com/)).
2.  **Upload Excel**: Select your draft schedule (.xlsx or .csv).
3.  **Upload PDF**: Select the Master PDF document.
4.  **Run Audit**: Click "Run Audit" and watch the console progress through Stages 1 to 6.

## Security & Data Privacy

This application is built with a **Privacy-First** architecture:

* **100% Client-Side**: All processing occurs locally in your browser.
* **No Data Retention**: Your PDF and Excel files are never saved, stored, or cached on any server.
* **Instant Data Wipe**: The moment you **Refresh the Page** or **Close the Tab**, all uploaded data and text extracts are permanently deleted from the browser's volatile memory.
* **Volatile API Key**: We do not use `localStorage`. Your API key is cleared instantly upon exit or refresh, requiring a fresh entry for every session for your protection.
* **Direct API Communication**: Your data travels directly from your browser to Google's Generative Language API via encrypted HTTPS.



## Built With

* [PDF.js](https://mozilla.github.io/pdf.js/) - Client-side PDF text extraction.
* [SheetJS](https://sheetjs.com/) - High-speed Excel data parsing.
* [Google Gemini API](https://ai.google.dev/) - AI reasoning and auditing engine.

---
© 2026 Asariko.net