
# Automate Medical Rep Visit Workflow with Google Sheets, Gmail & OpenAI Summaries

This n8n workflow automates the **daily reporting lifecycle for Medical Representatives (MRs)** — assigning daily visits from Google Sheets, emailing visit details, sending reminders for pending updates, converting Google Form responses into structured **AI-generated summaries**, and emailing consolidated daily reports to managers.

---

## ⚡ Quick Start – Implementation Steps

1. Connect **Google Sheets OAuth2 credentials** in all related nodes.
2. Update the `documentId` and `sheetName / gid` for:

   * **MR Plan** sheet
   * **Form Responses** sheet
3. Add **Gmail OAuth2 credentials** for sending emails.
4. Ensure the **Google Form link** exists in the MR Plan sheet.
5. Configure **OpenAI credentials** for AI Agent / Chat Model nodes.
6. Adjust all **Schedule Trigger** nodes (morning, evening, night).
7. Run a full test execution to verify assignments, reminders, and summaries.

---

## 📌 What It Does

This workflow automates three critical daily processes:

### 🌅 Morning – Visit Assignment

* Reads the **MR Plan** sheet.
* Finds visits with `Status = Pending`.
* Emails each MR their visit details and reporting form link.
* Updates the row status to `Assigned`.

### 🌆 Evening – Reminder Follow-ups

* Checks which MRs haven’t submitted visit updates.
* Sends reminder emails with the form link.
* Updates the sheet to mark reminders sent.

### 🌙 Night – AI Summary & Reporting

* Reads all responses from the **Google Form Responses** sheet.
* Uses **OpenAI** to normalize, summarize, and structure visit feedback.
* Emails a consolidated daily summary report to the manager.

This removes manual coordination, improves reporting consistency, and ensures leadership receives clean daily insights.

---

## 👥 Who’s It For

* **Pharma & healthcare field teams** (Medical Reps, ASMs, RSMs)
* Organizations with **daily visit-based operations**
* **Operations teams** needing automated reminders
* **Managers** requiring concise daily reports
* Teams using **Google Sheets + Gmail + AI** for automation

---

## 🛠 Requirements

To use this workflow, you need:

* A **Google Sheet** with daily MR visit assignments
* A **Google Sheet** linked to your Google Form responses
* **Google Sheets OAuth2 credentials**
* **Gmail OAuth2 credentials**
* **OpenAI API credentials**
* A working **Google Form** for visit reporting
* Three configured **Schedule Trigger** nodes:

  * Morning
  * Evening
  * Night

---

## ⚙️ How It Works

### 1. Morning — Daily Visit Assignment

* Schedule Trigger starts the workflow.
* Reads MR Plan rows where `Status = Pending`.
* Sends visit details + form link via email.
* Updates row status to `Assigned`.

---

### 2. Evening — Reminder Emails

* Schedule Trigger runs in the evening.
* Reads records with no form submission.
* Sends reminder emails.
* Updates reminder status in the sheet.

---

### 3. Night — AI Summary Reporting

* Night trigger reads all form responses.
* Each response is processed by **OpenAI**:

  * Normalization
  * Key point extraction
  * Summary generation
* A consolidated report is emailed to the manager.

---

## 🛠 How to Customize

### Google Sheets Nodes

* Change filters (by date, MR name, region).
* Adjust column mappings if your sheet differs.
* Modify `Status` values if you use custom labels.

### Gmail Nodes

* Customize subject lines and email templates.
* Add CC/BCC recipients.
* Personalize emails with MR or manager details.

### AI Agent / Chat Model

* Change summary format:

  * Bullet points
  * Action items
  * Call-outs
* Adapt prompts to match your form structure.

### Schedule Triggers

* Adjust times based on your time zone and work hours.

---

## ➕ Optional Enhancements

You can extend this workflow with:

* **Slack or Microsoft Teams notifications**
* **WhatsApp or SMS reminders** (via Twilio)
* Export summaries to **Google Sheets or Drive**
* Push AI summaries into a **CRM system**
* Automatic backups of MR plans and responses
* Performance dashboards for managers

---

## 📈 Use Case Examples

1. Daily **medical rep visit planning & reporting**
2. Sales teams performing client or distributor visits
3. Service engineers logging on-site work
4. Outreach teams tracking scheduled visits
5. Real estate agents summarizing daily site visits

---

## 🧪 Troubleshooting Guide

| Issue                  | Possible Cause            | Solution                          |
| ---------------------- | ------------------------- | --------------------------------- |
| Emails not sending     | Gmail OAuth expired       | Reconnect Gmail credentials       |
| Sheet data not loading | Incorrect Sheet ID or GID | Verify IDs from Google Sheets URL |
| Rows not updating      | Column name mismatch      | Align sheet column names          |
| AI summary missing     | OpenAI not configured     | Check API key and node settings   |
| Summary email empty    | AI output parsing issue   | Inspect execution logs            |

---

## 💬 Need Help?

If you need help setting up, customizing, or extending this workflow — including adapting it to your organization, improving AI summaries, or integrating external systems — the **WeblineIndia n8n automation team** can help with:

* Field-force automation
* AI-powered reporting
* Google Workspace integrations
* End-to-end n8n workflow development

🚀 Happy automating!

---