# Venom IPTV Panel
## Live Demo
https://venon33.github.io/venom-iptv-panel

A lightweight web panel to analyze IPTV links based on Xtream API servers.

## Features

* Automatic conversion of IPTV links to `get.php`
* Extracts **username and password** from IPTV URLs
* Queries `player_api.php`
* Displays server information:

  * Account status
  * Expiration date
  * Active connections
  * Available connections
  * LIVE / VOD / SERIES categories
  * Total number of channels
* Optimized interface for **desktop and mobile**
* Clean dark UI
* Pure **HTML + JavaScript** (no backend required)

## Usage

1. Paste an IPTV link into the input field.

Example:

```
http://example.com:8080/live/user/password/12345.ts
```

2. Click **Generate get.php** or **Get info**.

The panel will automatically detect:

* username
* password
* server host
* account status

## Technologies

* HTML
* CSS
* JavaScript
* Axios
* Bootstrap

No installation or backend required.

## Demo

You can run the panel directly in your browser.

## Author

Developed by **Venom**.



