# Driver Check-In Web App

A multi-language driver check-in portal that:

- Lets drivers select English, Swahili, Bemba or Portuguese  
- Autocompletes driver names (with truck numbers) from a Google Sheet  
- Records **Course Started** and **Course Completed** events back to Google Sheets  
- Plays an MP4 or embedded YouTube video and reveals the **Mark Complete** button 10 s before the end  

---

## 🚀 Features

1. **Language Selection**  
   Localized UI for English, Swahili, Bemba and Portuguese.  
2. **Driver Autocomplete**  
   Pulls `{ name, truck }` from your Google Sheet via Apps-Script and fills a `<datalist>`.  
3. **Logging**  
   Records start & completion events (with timestamps and duration) back to your logging Apps-Script.  
4. **Video Playback**  
   - **English**: YouTube embed via IFrame API (polls remaining time).  
   - **Other languages**: Native HTML5 `<video>`.  
5. **Smart “Mark Complete”**  
   Button only appears 10 s before the video ends.  

---

## 📝 Prerequisites

- A **Google Sheet** (e.g. “Sheet1”) with columns:
Full Name | Truck ID
Manyanda Maziku | T1234 ABC
Jordan Chaki | T5678 DEF
…
- Two **Apps Script** web-apps published as “Anyone, even anonymous”:
1. **Driver list endpoint** (returns JSON array of `{name,truck}`)  
   e.g. `https://script.google.com/macros/s/…/exec`
2. **Logging endpoint** (accepts POST of `name,truck,language,videoTitle,status[,duration,rowId]`)  
   e.g. `https://script.google.com/macros/s/…/exec`
- A static web-server (GitHub Pages, Firebase Hosting, etc.) to serve the HTML.

---

## 🛠️ Setup

### 1. Driver-List Apps Script

Replace your existing `doGet()` with:

```js
function doGet() {
const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Sheet1");
const rows  = sheet.getDataRange().getValues().slice(1);
const out   = rows
  .filter(r => r[0] && r[1])
  .map(r => ({ name: r[0], truck: r[1] }));
  
return ContentService
  .createTextOutput(JSON.stringify(out))
  .setMimeType(ContentService.MimeType.JSON);
}
Deploy → New deployment → Web app → “Execute as: Me” + “Who has access: Anyone, even anonymous.”
Copy the Web app URL for the driver list.

2. Logging Apps Script
Example doPost():
function doPost(e) {
  const ss    = SpreadsheetApp.openById("YOUR_SHEET_ID");
  const sheet = ss.getSheetByName("Log");
  const p     = e.parameter;
  sheet.appendRow([
    p.name, p.truck, p.language, p.videoTitle,
    p.status, new Date(), p.duration || ""
  ]);
  return ContentService
    .createTextOutput(JSON.stringify({ success: true, row: sheet.getLastRow() }))
    .setMimeType(ContentService.MimeType.JSON);
}
Deploy similarly and copy the Web app URL for logging.

### 3. Update index.html
In your <script>:
const DRIVER_LIST_URL = 'https://script.google.com/macros/s/.../exec';
const LOGGING_URL     = 'https://script.google.com/macros/s/.../exec';
Verify your YouTube video ID and MP4 URLs in the videoLinks map.

### 📂 Project Structure
/
├─ index.html        ← Full HTML + JS UI
├─ README.md         ← This file
└─ apps-script/      ← Google-Apps-Script projects
   ├─ driverList.gs
   └─ logging.gs

### ⚙️ Usage
Open index.html in a browser.

Select a language and Continue.

Type your name – suggestions appear from the Sheet.

Pick a name → Truck auto-fills.

Submit & Watch → logs Course Started + plays video.

Mark Complete appears 10 s before the end; click to log completion.

### ✏️ Customization
Add languages: extend the translations and videoLinks objects.

Adjust timing: change the ≤10 checks in the JS.

Style tweaks: edit CSS in the <style> block or load your own stylesheet.

### 👤 Author
Created by: Kwilasa Augustine Kwilasa
📧 Email: Kwilasaagustine57@gmail.com
🔧 Built with: Google Apps Script + HTML5 + GitHub Pages

### 📜 License
Free to use internally. For commercial use or redistribution, please request permission.
