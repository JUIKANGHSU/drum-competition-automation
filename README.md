<p align="center">
  <img src="https://raw.githubusercontent.com/JUIKANGHSU/drum-competition-automation/refs/heads/main/IMG_7558.jpeg" width="700" alt="project preview">
  <img src="https://raw.githubusercontent.com/JUIKANGHSU/drum-competition-automation/refs/heads/main/IMG_2877.JPG" width="350" alt="project used to">
  <img src="https://raw.githubusercontent.com/JUIKANGHSU/drum-competition-automation/refs/heads/main/IMG_9467.JPG" width="350" alt="project used to">
</p>
# 🥁 Drum Competition Automation (Google Apps Script)

This project automates a full judging workflow for a music/drum competition using **Google Forms + Google Sheets + Google Docs + Google Drive + Gmail**.

It demonstrates:
- event-driven automation (`onFormSubmit`)
- dynamic sheet creation and routing
- group-by average calculation
- report generation from a Docs template
- PDF export and email dispatch

Perfect for showing process automation skills in a portfolio.

---

## ✨ Features

1. **Form submission routing**
   - Detects which category (e.g. drum / electronic / age group) the row belongs to
   - Auto-creates the sheet if it doesn't exist
   - Appends the response to the right sheet

2. **Score aggregation**
   - Groups rows by E–X columns (participant identity)
   - Aggregates AX scores (multiple judges)
   - Writes the average to column AY
   - Generates a sorted list in column AZ

3. **Document generation**
   - Groups multiple judges' rows into one report
   - Fills a Google Docs template with placeholders
   - Saves to Drive and exports PDF to a specific folder

4. **Email dispatch**
   - Looks up participant email from another sheet
   - Sends the generated PDF to the participant

---

## 📦 Setup

1. Create / identify your **Form response sheet**  
   - Put its name in `CONFIG.FORM_SHEET_NAME`

2. Create **category sheets** or let the script auto-create them  
   - If you already know all categories, list them in `CONFIG.CATEGORY_SHEET_NAMES`

3. Prepare a **Google Docs template** with placeholders like:
   - `{{樂器別}}`
   - `{{年齡組別}}`
   - `{{EX_數據}}`
   - `{{平均分數}}`
   - `{{A演奏音樂性、律動性}}` ... etc.
   Put its ID in `CONFIG.DOC_TEMPLATE_ID`.

4. Prepare a **spreadsheet for emails**  
   - Column A: participant key (same as the PDF filename prefix)
   - Column B: email
   - Put its ID and sheet name in `CONFIG.EMAIL_SHEET_ID` and `CONFIG.EMAIL_SHEET_NAME`

5. Create / choose a **Drive folder** to store generated PDFs  
   - Put its ID in `CONFIG.PDF_FOLDER_ID`

6. In Apps Script, set a trigger:
   - `onFormSubmit` → event: “On form submit”

---

## ⚠️ Important

- Do **NOT** commit real spreadsheet IDs, Drive folder IDs, or student names to a public repository.
- Keep your template ID and email sheet ID in a separate config file if this is a production system.
- Gmail quota applies to `MailApp.sendEmail`.

---

## 📝 License

MIT
