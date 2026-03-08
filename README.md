Venom IPTV Panel

A lightweight web panel to analyze IPTV links based on Xtream API servers.

This tool extracts credentials from IPTV URLs and retrieves account information directly from the IPTV server using "player_api.php".

---

⚠️ Important

This project is designed to run locally in your browser.

When hosted on platforms like GitHub Pages, some IPTV servers may not respond due to:

- CORS restrictions
- HTTPS → HTTP security blocking (Mixed Content)
- Server-side access limitations

For the most reliable results, run the panel locally.

---

Features

- Automatic conversion of IPTV links to "get.php"

- Extracts username and password from IPTV URLs

- Queries "player_api.php"

- Displays server information:
  
  - Account status
  - Expiration date
  - Active connections
  - Available connections
  - LIVE / VOD / SERIES categories
  - Total number of channels

- Responsive interface (desktop & mobile)

- Clean dark UI

- Pure HTML + JavaScript

- No backend required

---

Supported IPTV URL formats

The panel automatically detects credentials from multiple formats.

Example 1

http://example.com:8080/get.php?username=user&password=pass&type=m3u

Example 2

http://example.com:8080/live/user/pass/12345.ts

Example 3

http://example.com:8080/player_api.php?username=user&password=pass

---

Usage

1. Open the panel in your browser.

2. Paste one or multiple IPTV URLs in the input field.

Example:

http://example.com:8080/get.php?username=user&password=pass&type=m3u

3. Click Get info.

The panel will automatically:

- extract username and password
- detect the IPTV server
- query "player_api.php"
- display account information and categories.

---

Running locally

Download or clone the repository and open:

index.html

with any modern browser.

No installation is required.

---

Technologies

- HTML
- CSS
- JavaScript
- Axios
- Bootstrap
- DataTables

---

Project purpose

This project is intended as an informational IPTV analysis tool.

It does not host streams or distribute IPTV content.

---

Author

Developed by Venom