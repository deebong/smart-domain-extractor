# Smart Domain Extractor 🕵️‍♂️

A lightweight, single-file HTML/JS tool designed to extract domain names from unstructured text, forum posts, and sales reports. 

Unlike standard extractors, this tool is built to handle **obfuscated** and "human-written" domains often found on platforms like NamePros, Twitter (X), and DNForum where users try to prevent search engine indexing.

## 🚀 The Problem
Domain sellers often report sales using creative formatting to avoid bots:
* `S t o c k O r b i t / c o m` (Spaced out with slashes)
* `Google(.)com` (Parenthesis)
* `Example dawt com` (Phonetic spelling)
* `Company . inc` (Floating dots)

Standard Regex fails here. It either misses the domain entirely or accidentally captures sentences like *"My favorite registrar in 2025"* as `registrar.in`.

## ✨ Features

* **Advanced De-Obfuscation:** Normalizes spaces, slashes, brackets, and phonetic dots ("dawt", "dot", "•").
* **Context Awareness:** Uses a "Sentence Gate" algorithm to distinguish between a spaced-out domain name and a normal English sentence.
* **Noise Filtering:** Automatically strips out prices (`$5,000`), dates, and common stop words (`Sold via...`).
* **Format Preservation:** Detects and preserves CamelCase (e.g., `StockOrbit.com`) if present in the source.
* **Interactive Sidebar:**
    * **TLD Stats:** Clickable filter to view only specific extensions (e.g., show only `.ai` sales).
    * **Sorting:** Toggle between A-Z and Z-A.
    * **Grouping:** Group sales by extension.
* **Export Options:** Download results as `.txt` or `.csv`.
* **100% Client-Side:** Runs entirely in your browser. No server, no data uploads.

## 🛠 Quick Start

No installation or build process is required.

1.  Download the `extractor_v5.html` file from this repository.
2.  Open it in any modern web browser (Chrome, Firefox, Safari).
3.  Paste your text into the **Source Data** box.
4.  Click **Extract Domains**.

## 🧠 How It Works

Instead of looking for a standard URL pattern (which is easily broken), this tool uses a **Reverse Anchoring** strategy:

1.  **Normalization:** First, it standardizes visual tricks (converting `(.)`, `[dot]`, `dawt` to real dots).
2.  **Anchor Search:** It scans for known TLDs (`.com`, `.ai`, `.co.uk`) acting as "anchors."
3.  **Reverse Extraction:** Once an anchor is found, it scans *backwards* to capture the domain name, stopping intelligently at "stop words" (like *sold*, *via*, *price*) or pricing patterns.
4.  **Validation Gates:**
    * **Risky TLD Check:** Extensions that are also words (like `.in`, `.it`, `.me`) trigger a stricter check to ensure they aren't part of a sentence.
    * **Length Gate:** Discards fragments that are too long to be valid domains.

## 🤝 Contributing

Feel free to open an issue if you find a specific style of obfuscation that this tool misses! Pull requests are welcome to improve the regex patterns or UI.

## 📄 License

MIT License - free to use and modify.
