# NexByte Speed Test

NexByte is a Windows utility platform for network tools, internet speed testing, and desktop applications. Its current desktop app, NexByte Speed Test, measures:

- Live ping
- Download speed
- Upload speed
- Internet connection quality
- Network performance in real time

Website:
https://nexbyteexe.github.io/

## Pages

- Homepage: https://nexbyteexe.github.io/ - Platform overview, product previews, FAQs, and developer profile
- Software and download: https://nexbyteexe.github.io/software.html - Windows app details and official installer
- Privacy policy: https://nexbyteexe.github.io/privacy.html - Data collection, advertising, and privacy details

The sitemap at `sitemap.xml` lists all public pages. `robots.txt` points crawlers to that sitemap.

## Overview

NexByte provides Windows network tools and desktop applications. Its current app, NexByte Speed Test, helps users check internet speed and monitor connection quality while working, gaming, streaming, or downloading files.

## Features

- Windows 10 and Windows 11 support
- Lightweight desktop-style speed testing interface
- Live ping monitoring
- Download and upload speed measurement
- Network quality tracking in a simple dashboard
- Download page for the Windows installer
- User feedback and anonymous download tracking
- Privacy policy page

## Project structure

- `index.html`: homepage, SEO metadata, Open Graph tags, and SoftwareApplication schema
- `software.html`: dedicated software landing page
- `privacy.html`: privacy policy and WebPage schema
- `index.min.css`: production stylesheet
- `home-layout.css`: responsive homepage layout
- `privacy.min.css`: privacy stylesheet
- `site-contact.css`: shared footer email-link styling
- `sitemap.xml`: public page URLs and last-modified dates
- `robots.txt`: crawler access and sitemap location
- `ads.txt`: authorized AdSense seller declaration
- `favicon.png`: browser tab icon
- `og-preview.jpg`: social sharing preview image
- `LOGO BRAND.webp`: developer logo linked from the homepage
- `app.min.js`: homepage interactions, download tracking, and script configuration
- `Code.gs`: Apps Script backend for click and feedback logging
- `preview-1.webp` to `preview-4.webp`: product preview images
- `nexbyte-icon.webp`: app icon
- `batik-pattern.svg`: decorative background asset

## Google AdSense

The AdSense loader is included on all three public pages. `ads.txt` declares Google as a direct seller for the site's publisher ID. Ads display only after the site is approved and Auto ads or ad units are enabled in the AdSense account.

## Run locally

This project is static and does not require a build step.

```powershell
py -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## GitHub Pages deployment

This repository is published via GitHub Pages at:

```text
https://nexbyteexe.github.io/
```

To deploy:

1. Push the project files to the `main` branch.
2. Open the repository on GitHub.
3. Go to **Settings > Pages**.
4. Set **Source** to **Deploy from a branch**.
5. Choose `main` and `/ (root)`.
6. Save and wait for deployment.

## Windows installer release

The Windows installer is published on GitHub Releases:

```text
https://github.com/nexbyteexe/nexbyteexe.github.io/releases/download/v1.0.0/NexByte.1.0.0.exe
```

When releasing a new version:

1. Create a new GitHub release with a version tag such as `v1.0.1`.
2. Upload the `.exe` installer file.
3. Update the installer URL in the project if the file name or release version changes.
4. Update the version metadata and download details in the homepage when needed.

## Apps Script backend

`Code.gs` stores click and feedback data in Script Properties. To use a custom backend:

1. Create a Google Apps Script project.
2. Copy the code from `Code.gs`.
3. Deploy it as a **Web App** with access for public requests.
4. Copy the deployment URL ending in `/exec`.
5. Update the Apps Script URL in `app.min.js`.

## Privacy

Download actions and feedback are collected in a limited and privacy-conscious way. Full details are available in the privacy page:

```text
https://nexbyteexe.github.io/privacy.html
```

## SEO and structured data

The site is positioned as a Windows utility platform for network tools, internet speed testing, and desktop applications. The current product is NexByte Speed Test. Public pages use page-specific canonical and Open Graph URLs; product pages provide `SoftwareApplication` JSON-LD, and the privacy page provides `WebPage` JSON-LD. The homepage and software page highlight:

- Windows compatibility
- live ping
- download speed
- upload speed
- network quality monitoring
