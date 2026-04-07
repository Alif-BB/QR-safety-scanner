# QR Safety Scanner

A browser-based QR code scanner that checks URLs for safety using heuristic analysis, Google Safe Browsing, and VirusTotal.

## Features

- **Live camera scanning** — point your webcam at any QR code
- **Image upload** — scan QR codes from saved images
- **Heuristic analysis** — instant checks for HTTPS, typosquatting, suspicious TLDs, phishing keywords, URL encoding, and more
- **Google Safe Browsing** — checks against Google's threat database (malware, phishing, unwanted software)
- **VirusTotal** — checks against 70+ antivirus engines
- **No backend required** — runs entirely in the browser

---

## Deploy to GitHub Pages (step by step)

### 1. Create a new GitHub repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** button (top right) → **New repository**
3. Name it `qr-safety-scanner` (or anything you like)
4. Set it to **Public**
5. Click **Create repository**

### 2. Upload the file

1. On your new repo page, click **uploading an existing file**
2. Drag and drop `index.html` into the upload area
3. Scroll down and click **Commit changes**

### 3. Enable GitHub Pages

1. Go to your repo **Settings** tab
2. Scroll to **Pages** in the left sidebar
3. Under **Source**, select **Deploy from a branch**
4. Set Branch to `main` and folder to `/ (root)`
5. Click **Save**

After about 60 seconds, your site will be live at:
```
https://YOUR_USERNAME.github.io/qr-safety-scanner/
```

---

## Getting free API keys

### Google Safe Browsing (recommended)

1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Create a new project (or use an existing one)
3. Go to **APIs & Services** → **Enable APIs**
4. Search for **Safe Browsing API** and enable it
5. Go to **APIs & Services** → **Credentials**
6. Click **Create Credentials** → **API Key**
7. Copy the key — paste it into the app when checking a URL

### VirusTotal

1. Go to [virustotal.com](https://www.virustotal.com) and create a free account
2. Go to your profile → **API Key**
3. Copy the key — paste it into the app when checking a URL

> **Free tier limits:**
> - Google Safe Browsing: 10,000 requests/day
> - VirusTotal: 4 requests/minute, 500/day

---

## How the safety checks work

| Check | What it looks for |
|---|---|
| HTTPS | Whether the URL uses encryption |
| Shortened URL | bit.ly, tinyurl, t.co, etc. that hide the real destination |
| IP address host | Domains like `http://192.168.1.1/...` |
| Typosquat / lookalike | Misspelled brand names (paypa1, g00gle, etc.) |
| TLD risk | High-abuse top-level domains (.xyz, .tk, .ml, etc.) |
| Subdomain depth | Excessive subdomains used to fake legitimacy |
| Phishing keywords | Words like login, verify, account, confirm, prize |
| URL encoding | Excessive %XX encoding used to obfuscate URLs |
| URL length | Unusually long URLs that may hide the real destination |

---

## Privacy

API keys are only used in your browser — they are never stored or sent anywhere except directly to Google/VirusTotal when you click "Check". No data is collected.

---

## Tech stack

- Vanilla HTML/CSS/JS — no frameworks, no build step
- [jsQR](https://github.com/cozmo/jsQR) for QR decoding
- [Google Safe Browsing API v4](https://developers.google.com/safe-browsing/v4)
- [VirusTotal API v3](https://developers.virustotal.com/reference/overview)
