[6/4/26 12:37] Notas: from pathlib import Path

readme = """# Venom IPTV Panel

Venom IPTV Panel is a lightweight local web tool for analyzing IPTV links based on Xtream Codes / Xtream API style servers.

It extracts credentials from IPTV URLs, queries the server API, generates a ready-to-use get.php playlist URL, and displays useful diagnostics such as account status, expiration date, categories, live channels, panel type, detected mode, stream ID, access behavior, and network advice.

The project is designed to run locally in the browser.

---

## Overview

Venom IPTV Panel helps inspect IPTV-style links and determine:

- whether the panel is responding correctly
- which type of panel is being detected
- which credentials were extracted
- whether the server is returning categories and live streams
- whether access may depend on network, VPN, or IP behavior

The interface is optimized for both:

- Desktop → full table layout
- Mobile → compact card layout

---

## Main Features

### IPTV URL Detection

The panel can detect and normalize multiple IPTV link formats, including:

- get.php
- player_api.php
- /live/user/pass/id
- /movie/user/pass/id
- /series/user/pass/id
- short route patterns like /user/pass/id
- M3U / M3U8 links
- tokenized links

---

### Automatic get.php Generator

Each detected result includes a Generate get.php button.

The generated playlist URL follows this structure:

get.php?username=USER&password=PASS&type=m3u_plus&output=ts
The final URL appears in the upper panel and can be saved as a .txt file.

---

### Xtream API Analysis

The panel queries the server through:

player_api.php
and extracts:

- account status
- expiration date
- max connections
- active connections
- free connections
- TV categories
- movie categories
- series categories
- live channel count

---

### Panel Type Detection

The tool attempts to classify the IPTV source automatically.

| Type | Description |
|------|-------------|
| Xtream API | Standard Xtream API endpoint |
| Xtream route | /live/user/pass/... style URL |
| M3U simple | Static playlist |
| M3U with token | Token-protected playlist |
| Unknown | Not clearly identified |

---

### Detected Route Mode

The parser also identifies how credentials were extracted from the original URL.

Possible detected modes include:

- get_php
- player_api
- query_credentials
- live_route
- movie_route
- series_route
- short_route
- unknown

This makes it easier to understand how the panel interpreted the input.

---

### Stream ID Detection

If the original link contains a stream identifier, the panel displays it as Stream ID.

This is especially useful for links such as:

http://host:port/user/pass/12345
or:

http://host:port/live/user/pass/12345.ts
---

### Diagnostics

The panel provides visual diagnostics for:

- direct access / CORS behavior
- reverse proxy / web server hints
- Cloudflare detection
- live channel count health
- possible IP / network restrictions
- access consistency

---

### Network Advice

The panel includes a Network Advice indicator to help interpret cases where access may differ between devices or networks.

Examples of advice shown:

- No clear signs
- Try without VPN or change network
- Possible restriction by IP or location
- Try another network or disable VPN

This does not directly detect whether a VPN is active.  
Instead, it infers network-related issues based on panel behavior and response patterns.

---

### Parallel Processing

Multiple IPTV links are analyzed in parallel for better performance.

The panel automatically adjusts request concurrency depending on the device:

| Device | Parallel requests |
|--------|-------------------|
| Mobile | 3 |
| Desktop | 6 |

This makes batch analysis much faster.

---

### Mobile-Friendly Interface

The interface automatically switches between:

- Desktop table layout
- Mobile card layout

Mobile layout includes:
[6/4/26 12:37] Notas: - compact diagnostics
- per-card actions
- expandable categories
- simplified visual status indicators

---

### Clean Re-run Logic

The panel includes a hardened reset flow to reduce stale state between runs.

This improves reliability when:

- clearing results
- re-running analysis several times
- testing multiple IPTV entries in sequence
- aborting previous runs and starting again

---

## Visual Status Guide

The panel uses compact colored indicators:

- ✔ Green → normal / good
- ⚠ Yellow → warning / partial response
- ✖ Red → error / blocked / missing data

These colors are used in diagnostics such as:

- panel type
- access behavior
- protection
- channel count
- network restriction hints

---

## How to Use

1. Open index.html in your browser.
2. Paste one or more IPTV links into the input box.
3. Click Obtener info.
4. Review the results in the table or mobile cards.
5. Click Generar get.php on any result if needed.

### Example Input

http://example.com:8080/live/user/pass/12345.ts
---

## Buttons

### Obtener info
Starts the IPTV analysis process.

### Borrar
Clears all results, counters, generated URLs, and logs.

### Pegar
Attempts to paste clipboard content into the input box.

### Guardar .txt
Saves the generated get.php URL as a text file.

### Ver info
Shows internal logs only when needed.

---

## Example Workflow

1. Paste one or multiple IPTV links.
2. Run the analysis.
3. Review:
   - account status
   - expiration
   - categories
   - live channel count
   - panel type
   - detected mode
   - stream ID
   - network advice
4. Generate get.php from a valid result.
5. Save it as .txt if required.

---

## Project Structure

.
├── index.html
└── README.md
---

## Recommended Usage

For best results:

- run the panel locally
- use a modern browser
- paste complete IPTV URLs when possible
- avoid running multiple scans manually at the same time
- if mobile behavior differs from desktop, test another browser or network

---

## Notes

Some IPTV servers may behave differently depending on:

- IP address
- VPN usage
- ASN / ISP
- geographic region
- proxy / firewall rules
- browser security restrictions
- DNS resolution differences between devices

Because of that, some panels may:

- fully respond
- partially respond
- block category or stream queries
- return inconsistent results depending on network conditions

---

## Clipboard Notes

On some mobile browsers, clipboard access may be restricted.

If the Paste button cannot access the clipboard, use manual paste instead.

---

## Privacy

All analysis is performed locally in your browser.

The tool does not send data to any external server of its own.

Requests are made directly from the browser to the IPTV source being analyzed.

---

## Technologies Used

- HTML
- CSS
- JavaScript
- Axios
- Bootstrap
- DataTables

No backend or installation is required.

---

## Disclaimer

This project is provided for educational, diagnostic, and testing purposes only.

The author is not responsible for misuse of this tool or unauthorized access to IPTV services.

Use it only with systems and accounts you are authorized to inspect.

---

## Author

Developed by Venom
