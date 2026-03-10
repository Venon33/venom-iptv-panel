Venom IPTV Panel

Venom IPTV Panel is a lightweight web tool designed to analyze IPTV links that use Xtream Codes API or similar server structures.

The panel extracts credentials from IPTV URLs, queries the server API, and displays useful account information such as status, expiration date, categories, and number of channels.

The tool runs entirely in the browser and does not require any backend or installation.

Features
IPTV URL Detection

The panel automatically detects different IPTV URL formats including:

* get.php
* player_api.php
* /live/user/pass/id
* /movie/user/pass/id
* /series/user/pass/id
* M3U links
* tokenized URLs
* Automatic get.php Generator
* For every detected IPTV account the panel can generate a ready-to-use playlist URL:

  get.php?username=USER&password=PASS&type=m3u_plus&output=ts

  This allows quick testing or importing into IPTV players.

Xtream API Analysis

The panel queries the server using:

player_api.php

and extracts:

* account status
* expiration date
* max connections
* active connections
* free connections
* live categories
* vod categories
* series categories
* number of live channels

Panel Type Detection

The tool attempts to identify the type of IPTV service:

  Type                              Description
Xtream API	              Standard Xtream Codes panel
Xtream route	            /live/user/pass style URL
M3U simple	              Static playlist
M3U token	                Token protected playlist
Unknown	                  Cannot determine panel type



Diagnostics
Additional server diagnostics are displayed:

* proxy / direct access detection
* reverse proxy indicators
* Cloudflare detection
* channel count health indicator


Parallel Processing
Multiple IPTV links are analyzed simultaneously.

Typical performance:

10 IPTV links → 2–4 seconds

The panel automatically adjusts processing depending on device:

Device	     Parallel requests
Mobile	          3
Desktop	          6
Mobile         Friendly UI

The interface automatically switches to card view on mobile devices, making it easier to read account data.

Desktop uses a full data table.

How to Use

1- Open the panel in your browser.
2- Paste IPTV links into the input box.

Example:

http://example.com:8080/live/user/pass/12345.ts

Click Obtener info.
The panel will automatically:

* detect credentials
* query the Xtream API
* display account information

Generate Playlist
After analysis you can click:

Generar get.php

to generate a playlist URL.

The generated URL appears in the get.php panel where it can be saved as a .txt file.

Technologies
This project is built using simple frontend technologies:

* HTML
* CSS
* JavaScript
* Axios
* Bootstrap
* DataTables

No server, database, or backend is required.

Privacy
All analysis is performed locally in your browser.
The tool does not send data to any external server.

Disclaimer
This project is provided for educational and testing purposes only.
The author is not responsible for misuse of this tool or for accessing IPTV services without proper authorization.

Author

Developed by Venom

  
