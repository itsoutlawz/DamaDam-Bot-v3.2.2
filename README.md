# DamaDam Scraper – Automated Target Bot
Version: v3.2.1  
Author: OutLawZ

## Overview
This repository contains an advanced automation bot that scrapes DamaDam user profiles and stores well-structured results directly into Google Sheets.

The bot:
- Reads pending users from a Google Sheet (“Target” sheet)
- Logs into DamaDam.pk
- Scrapes profile details (city, age, followers, posts, intro, last post, timestamps)
- Saves results into “ProfilesTarget” sheet
- Updates target status (Done / Error / Pending)
- Creates dashboard analytics logs
- Supports GitHub Actions automation (hourly running)

---

## Features
- Chrome automation with Selenium
- Google Sheets API integration
- Error handling + retry logic
- Adaptive delays to avoid rate limits
- Account suspension / unverified detection
- Quantico font auto-formatting
- Profile update change-tracking with notes
- Fully automated CI workflow

---

## Requirements
- Python 3.9+
- Google Service Account
- Selenium ChromeDriver
- Google Sheet with following tabs:
  - `ProfilesTarget`
  - `Target`
  - `Dashboard`
  - `Tags` (optional)

---

## Environment Variables

Create a `.env` file based on `.env_example`.

| Variable | Description |
|---------|-------------|
| DAMADAM_USERNAME | Account login username |
| DAMADAM_PASSWORD | Account login password |
| GOOGLE_SHEET_URL | Spreadsheet URL |
| GOOGLE_APPLICATION_CREDENTIALS | Path → credentials.json |
| MAX_PROFILES_PER_RUN | Limit scraping per run |
| BATCH_SIZE | Batch size for scraping |
| MIN_DELAY | Min delay between scraping |
| MAX_DELAY | Max delay |
| GOOGLE_CREDENTIALS_JSON | Raw JSON credentials (for GitHub Actions) |

---

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Run Locally

```bash
python Scraper.py
```

---

## GitHub Actions Automation

A workflow is provided in:

```
.github/workflows/damadam-scraper.yml
```

It:
- Installs dependencies
- Injects Google credential JSON
- Runs every 1 hour

---

## Folder Notes
Do NOT upload your real `credentials.json` to GitHub.  
Use the encoded JSON method inside GitHub Secrets.

---

## Support
For improvements or issues, contact OutLawZ.
