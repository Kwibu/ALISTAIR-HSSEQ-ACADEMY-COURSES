# 🚛 Driver Safety Check-In App

This web app is a multilingual driver check-in and training tool. It allows drivers to register, watch a safety video in their language, and confirm completion — with all data automatically logged to a Google Sheet. Monthly and yearly reports can also be generated directly from the sheet.

---

## 🌐 Supported Languages

- 🇹🇿 Swahili
- 🇿🇲 Bemba
- 🇲🇿 Portuguese

---

## 🎯 Features

- Language selector (localized labels, buttons, and messages)
- Form fields for Name and Truck Number
- Embedded HTML5 training video in selected language
- Localized “Mark as Completed” and completion confirmation message
- Completion button appears at the end
- Google Sheets integration for:
  - Course Start Time
  - Completion Time
  - Duration Tracking
- Built-in Monthly and Yearly Reports (via Google Apps Script menu)

---

## 📁 Files

- `index.html` – Main app interface
- `trucks.jpg` – Background image
- `README.md` – Project documentation

---

## 📊 Google Sheets Integration

All data is submitted to this Google Apps Script endpoint: https://script.google.com/macros/s/AKfycbzUy3d6QTbXcjh-kq0O8OsnKQGrMsQlE9CXSzfwiVbc19avtjsCPP3wA9hjd-CikNZJ/exec

### Tracked Fields:

| Name | Truck | Language | Video Title | Course Started | Course Completed | Duration |
|------|-------|----------|-------------|----------------|------------------|----------|

---

## 📈 Reports

The Google Sheet contains a custom menu **“Driver Reports”** with the following options:

- ✅ Generate Monthly Report
- ✅ Generate Yearly Report

Each option creates a new sheet summarizing completions by month or year.

---

## 🚀 Deployment Instructions

1. Clone or download the repository
2. Ensure `trucks.jpg` is in the root folder
3. Host the files on any static site platform (e.g., GitHub Pages, Netlify)
4. Ensure video files are hosted publicly (GitHub-hosted `.mp4` links are used)
5. Link the `index.html` to your deployed Google Apps Script

---

## 🛠 Customization

To update:
- **Languages**: Edit `translations` and `videoLinks` in the JavaScript section of `index.html`
- **Completion message**: Translations for “Course Completed” can be edited per language
- **Reports**: You can extend the reporting script to filter by truck, language, or duration

---

## 👤 Author

Created by: **Kwilasa Augustine Kwilasa**  
📧 Email: [Kwilasaagustine57@gmail.com](mailto:Kwilasaagustine57@gmail.com)  
🔧 Built with: Google Apps Script + HTML5 + GitHub Pages

---

## 📜 License

Free to use internally. For commercial use or redistribution, please request permission.
