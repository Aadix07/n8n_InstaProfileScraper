# InstaProfileScraping – n8n Workflow

An automated Instagram profile scraping system built with **n8n** that fetches recent post data from a given profile and stores it in a **Google Sheet** for easy tracking and analysis.

---

## 📹 Demo Video

https://youtu.be/2aSxgngRe7U<!-- Add your demo video link here -->

---

## 📌 Overview

This n8n workflow enables you to:

- Scrape Instagram post data using Apify's Instagram Scraper API
- Extract metadata like type, caption, hashtag, post URL, likes, and video play count
- Store the structured data into a Google Sheet
- Run the process manually for any public Instagram profile

---

## ⚙️ Workflow Components

### 1. Manual Trigger
- Initiates the workflow on demand from within the n8n UI
- Input: Instagram profile URL

### 2. HTTP Request
- Makes a `POST` request to the Apify Instagram Scraper API
- Input: JSON body with the profile URL and scrape options
- Output: Post data (up to 5 posts)

### 3. Split Out
- Breaks down the returned array into individual post objects
- Extracted Fields:
  - Profile URL
  - Type
  - Caption
  - First Hashtag
  - Post URL
  - Likes Count
  - Video Play Count

### 4. Google Sheets
- Appends each post’s data as a new row in the target Google Sheet
- Sheet must be pre-configured with the correct columns

---

## 🧾 Google Sheet Format

| Profile URL | Type | Caption | Hashtag | URL | Likes Count | Video Play Count |
|-------------|------|---------|---------|-----|--------------|------------------|


---

## 🚀 How It Works

1. You manually trigger the workflow.
2. The profile URL is sent to Apify’s Instagram Scraper API.
3. The returned post data is split into individual records.
4. Each record is inserted into the Google Sheet as a new row.
5. You get a structured database of Instagram post analytics.

---

## 🛠 Setup Requirements

To use this workflow, you need:

- ✅ A running instance of n8n
- ✅ Apify API access with token
- ✅ Google Sheets API credentials (OAuth2 connected in n8n)
- ✅ An accessible Google Sheet with the required columns
- ✅ The Instagram profile should be public

---

## 📥 Example Input

```json
{
  "profile": "https://www.instagram.com/meta.ai?igsh=eW1nZWFob2F5c2F3" #you can add any profile url here
}
```

---

## 📤 Sample Output in Sheet

| Profile URL                          | Type  | Caption                | Hashtag | URL                  | Likes Count | Video Play Count |
|--------------------------------------|-------|-------------------------|---------|-----------------------|--------------|------------------|
| https://www.instagram.com/meta.ai...| image | "Exploring the metaverse"| ai      | https://instagr.am/...| 1050         | 5600             |

---


