# 🚛 Driver Safety Check-In App

This web app is a multilingual driver check-in and training tool. It allows drivers to register, watch a safety video in their language, and confirm completion — with all data automatically logged to a Google Sheet.

---

## 🌐 Supported Languages

- 🇹🇿 Swahili
- 🇿🇲 Bemba
- 🇲🇿 Portuguese

---

## 🎯 Features

- Language selector (with localized labels and messages)
- Form fields for Name and Truck Number
- Embedded HTML5 training video per language
- “Mark as Completed” button appears 10 seconds before video ends
- Google Sheets integration for:
  - Course Start Time
  - Completion Time
  - Duration Tracking

---

## 📁 Files

- `index.html` – Main app interface
- `trucks.jpg` – Background image
- `README.md` – Project overview

---

## 📊 Google Sheets Integration

All data is submitted to this Google Apps Script:


### Tracked Fields:

| Name | Truck | Language | Video Title | Course Started | Course Completed | Duration |
|------|-------|----------|-------------|----------------|------------------|----------|

---

## 🚀 Deployment Instructions

1. Clone or download the repository
2. Ensure `trucks.jpg` is in the root folder
3. Host the files on any static site platform (e.g. GitHub Pages, Netlify)
4. Ensure video files are hosted on a public CDN (used from GitHub in this version)

---

## 🛠 Customization

To update:
- **Languages**: Edit `translations` and `videoLinks` in the JavaScript section.
- **Google Script**: Use your own deployed Google Apps Script URL for data collection.
- **Video Files**: Upload `.mp4` videos and update links accordingly.

---

## 👤 Author

Created by Kwilasa Augustine Kwilasa
Email: Kwilasaagustine57@gmail.com
Deployed using Google Apps Script + GitHub + HTML5

---

## 📜 License

Free to use internally. For commercial use or redistribution, please request permission.

