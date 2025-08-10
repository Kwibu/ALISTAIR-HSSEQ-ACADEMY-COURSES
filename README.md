# Driver Training Portal — Quick README

**What it is:** A single-file front-end + small Google Apps Script (GAS) backend for driver training videos (YouTube / Google Drive / MP4 / local). Multilingual UI, simple admin, offline-friendly.

## Files
- `driver-training-portal.html` — the app (open in a browser / host statically)
- `apps-script/Code.gs` — GAS backend (deploy as a Web App)
- `trucks.jpg` — optional background image

## Setup

### 1) Backend (Google Apps Script)
1. Create a Google Sheet with **three tabs**:
   - **Drivers**: `name, truck`
   - **Assignments**: `id, title, language, type, videoId, url, driveId, assignedAt`
   - **History**: `timestamp, name, truck, language, videoTitle, status, duration, assignmentId, rowId`
2. In Google Drive: **New → More → Google Apps Script**.
3. Paste `apps-script/Code.gs` into `Code.gs`.
4. Set `SPREADSHEET_ID` to your Sheet’s ID and adjust `ORIGINS`.
5. **Deploy → New deployment → Web app**  
   Execute as: **Me** · Access: **Anyone with the link** (or your org).  
   Copy the Web App **exec URL**.

### 2) Front-end
1. Open `driver-training-portal.html`.
2. Set `CONFIG.BASE_URL` to your GAS **exec URL**.
3. (Optional) Change demo admin auth in `CONFIG`:
   - `ADMIN_ACCESS_CODE`
   - `ADMIN_CREDENTIALS`

## Admin (demo)
- **Access code:** `AG-TRAINING-2025`  
- **Email + password (domain must end with `@alistairgroup.com`):**
  - `admin@alistairgroup.com` / `admin123`
  - `training@alistairgroup.com` / `training123`

## Notes
- Demo credentials live in the HTML → for production, move auth to the backend and issue a session token.
- If “Continue / Admin Login” don’t click, ensure the tiny `$`/`$$` helper script is included **before** the main app code (already in v2).
- Offline completions queue locally; use **Sync Pending** to push when online.

## License
MIT (or your preferred license).
