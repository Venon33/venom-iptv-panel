<div align="center">

# VENOM IPTV Panel

**Local Xtream API analyzer · Category explorer · M3U playlist exporter**

**Analyze authorized Xtream IPTV accounts, explore content categories, select titles, and generate tailored `.m3u` playlists from a single browser-based interface.**

[Features](#features) · [Quick start](#quick-start) · [Workflow](#typical-workflow) · [Privacy](#privacy--security) · [Limitations](#limitations)

</div>

---

## Overview

VENOM IPTV Panel is a lightweight, local-first web application for inspecting IPTV-style URLs and Xtream-compatible account responses. It extracts account details from supported URL patterns, queries the Xtream `player_api.php` endpoint, shows diagnostic information, and helps organize channels, movies, and series into customized M3U playlists.

The interface is written in Spanish and adapts to both desktop and mobile screens. **No application backend is required**; supported data requests are made by the browser to the IPTV server being inspected.

> [!IMPORTANT]
> Only use accounts and services you own or have permission to access. The tool does not supply IPTV content, subscriptions, credentials, or streaming servers.

## Features

| Area | Capabilities |
| --- | --- |
| **URL parsing** | Detects `get.php`, `player_api.php`, `/live/`, `/movie/`, `/series/`, short credential routes, and other recognized URL styles. |
| **Account diagnostics** | Shows account state, expiration, maximum/active/free connections, panel type, route detection, stream ID, and network-related hints. |
| **Category explorer** | Displays selectable **Live TV**, **Movies (VOD)**, and **Series** categories for each compatible Xtream account. |
| **Individual title selection** | Loads titles from selected movie/series categories and lets you choose individual movies or series. |
| **Global search** | Searches analyzed channels and **already-loaded** movie and series catalogs. |
| **Unified M3U export** | One export action can combine selected channels, movies, and series episodes into a single `.m3u` file **per account**. |
| **Playlist URL generator** | Creates a `get.php` URL for a recognized Xtream account, with an option to save it as a `.txt` file. |
| **Progress & errors** | Shows catalog-loading feedback, export progress for series-episode lookups, and a separate list of failed account checks. |
| **Responsive UI** | Desktop table, mobile cards, expandable category sections, color-coded selection, and a bottom **Hide content** action. |
| **Batch processing** | Analyzes multiple supported links with concurrency adjusted for mobile or desktop. |

### Unified export: what is downloaded?

The button **`Descargar contenido seleccionado`** generates a local **M3U playlist file containing stream URLs**. It does **not** download the actual video files.

- Selecting Live TV categories includes matching channels.
- Selecting VOD categories includes their movie entries; when individual movies have been selected, those individual movie selections take priority for VOD.
- Selecting Series categories includes available episodes; when individual series have been selected, those selections take priority for Series.
- Selecting more than one content type can produce **one combined playlist** for the current Xtream account.
- If no category or title is selected, the export does not proceed.

**Note:** Movie and series data requires API requests. The amount of content generated depends on the server response, and the resulting URLs may still require valid account access to play.

### Search and category selection

The **global search** indexes the data the panel has already retrieved; it does **not** search a provider's entire uncached catalog. To find a movie or series, select its category and click **`Cargar películas y series`** first.

Use **`Limpiar y volver a cargar`** to clear previous titles and load the currently selected categories. If none are selected, the catalog stays empty. Use **`Ocultar contenido`** to collapse an expanded details panel without scrolling back to its top.

### Diagnostics and error reporting

The panel provides indicators for:

- Xtream API/account availability and expiration
- Live, VOD, and Series category counts
- Live-stream count and connection limits
- HTTP/API failures and CORS-related conditions
- Possible reverse-proxy, web-server, or Cloudflare signals
- Network/IP/VPN troubleshooting suggestions

These indicators are **heuristics**, not proof of a specific restriction. In particular, VENOM does **not** detect whether your VPN is currently connected.

### Supported source formats

Examples with placeholders (not working credentials):

```text
http://example.com:8080/get.php?username=USER&password=PASS&type=m3u_plus&output=ts
http://example.com:8080/player_api.php?username=USER&password=PASS
http://example.com:8080/live/USER/PASS/12345.ts
http://example.com:8080/movie/USER/PASS/67890.mp4
http://example.com:8080/series/USER/PASS/24680.mp4
http://example.com:8080/USER/PASS/12345
```

The parser also recognizes some M3U/token-style URLs for classification. **Recognizing a format does not guarantee that it contains extractable Xtream credentials or can be queried through `player_api.php`.**

### Portal MAC information

The panel can parse supplied **Portal/MAC information blocks** and display their provided details alongside Xtream results. This is an **information display**, not a general Portal MAC authorization, authentication, or playlist-export client. `get.php` generation is not available for these entries.

## Quick start

**Requirements:** a modern desktop/mobile browser, internet access for external frontend libraries and remote API requests, and a permitted Xtream account for live analysis.

1. Clone the repository or download its files.
2. Open `index.html` in your browser.
3. Paste one or more supported URLs or Portal/MAC information blocks.
4. Click **`Obtener info`** to start analysis.
5. Expand **`Ver detalles`** and choose the content categories you want.
6. Optionally load movie and series titles, select individual items, or use the global search.
7. Click **`Descargar contenido seleccionado`** to generate a custom M3U playlist.

```bash
# Clone the project
git clone https://github.com/Venon33/venom-iptv-panel.git
cd venom-iptv-panel

# Open index.html in your preferred browser.
```

> [!NOTE]
> Opening the page directly via `file://` is supported for the local interface, but some browsers and IPTV servers restrict cross-origin API requests. If calls fail, check the browser console and the server's CORS behavior. Running a local HTTP server does not bypass a remote server's CORS policy.

## Typical workflow

```text
Paste URLs / Portal-MAC details
             │
             ▼
      Obtener info
             │
             ▼
  Review account diagnostics
             │
             ▼
       Ver detalles
             │
       ┌─────┼──────┐
       ▼     ▼      ▼
     Live   VOD   Series
       └─────┼──────┘
             ▼
  Select categories / titles
             │
             ▼
  Descargar contenido seleccionado
             │
             ▼
       Custom .m3u file
```

## Main controls

| UI label | Purpose |
| --- | --- |
| `Obtener info` | Analyze supported accounts/links. |
| `Borrar` | Reset the current analysis, results, counters, and related UI state. |
| `Pegar` | Attempt to paste clipboard content. |
| `Generar get.php` | Build a `get.php` playlist URL from a supported Xtream account. |
| `Guardar .txt` | Save the generated URL as a text file. |
| `Ver detalles` | Expand account/category information. |
| `Cargar películas y series` | Fetch titles in the selected VOD/Series categories. |
| `Limpiar y volver a cargar` | Replace previously loaded title results using the current category selection. |
| `Descargar contenido seleccionado` | Export the selected content into an `.m3u` playlist. |
| `Ocultar contenido` | Collapse the expanded account details. |
| `Ver info` | Show additional diagnostic logs. |

## Responsive interface

VENOM uses a full table for desktop screens and compact cards for mobile devices. Selected categories and titles receive stronger visual emphasis so they are easier to distinguish. The panel includes color-coded state indicators:

- **Green:** normal / available
- **Amber:** warning / partial or uncertain condition
- **Red:** error / unavailable

Batch analysis currently uses up to **6 concurrent workers on desktop** and **3 on mobile**, based on viewport width. Actual speed depends on the remote servers.

## Screenshots

You can add your own screenshots of the running panel here later. Before publishing, make sure images do not reveal real account credentials, access URLs, MAC addresses, or private server identifiers.

## Project structure

```text
venom-iptv-panel/
├── index.html              # Browser UI, parsing, API access and M3U export
└── README.md               # This documentation
```

No application build process or custom backend is needed. Frontend libraries are currently loaded from external CDNs.

## Privacy & security

- The application has **no custom data-collection backend**. API requests go from your browser to the remote IPTV endpoints you choose.
- It also loads third-party frontend assets from CDNs; therefore, **"local-first" does not mean fully offline or network-isolated**.
- **IPTV URLs and exported `.m3u` files can contain usernames and passwords.** Handle them as sensitive files; do not upload them to public issue reports or repositories.
- Diagnostic logs may include the original URL and extracted credentials. Avoid publishing logs or screenshots without reviewing and redacting them.
- Browser extensions, browser history, remote servers, local downloads, and third-party networks can have their own security/privacy implications.

## Limitations

- Server responses vary across Xtream-compatible implementations.
- Browser CORS rules, HTTPS mixed-content restrictions, firewalls, VPNs, or provider controls can prevent API requests.
- A displayed category or stream does not guarantee that playback will succeed.
- Global search only covers data that was **already loaded** in the current session.
- Large category selections and series exports may generate multiple network requests and take time.
- The export button downloads **playlist files**, not full media files.
- Portal MAC information entries do not have the same API/export capabilities as Xtream accounts.

## Tech stack

**HTML5 · CSS3 · Vanilla JavaScript · Axios · Bootstrap 4 · jQuery/DataTables**

## Responsible use

This project is intended for legitimate administration, diagnostics, interoperability testing, and management of **services and accounts you are authorized to access**. No channels, movies, accounts, or access rights are included. Respect provider terms, copyright, and applicable law.

## Author

Developed by **Venom**.

---

<div align="center"><sub>VENOM IPTV Panel · Browser-based Xtream analysis and M3U playlist management</sub></div>
