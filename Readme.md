# Automate Medical Rep Visit Workflow with Google Sheets, Gmail & OpenAI Summaries

This n8n workflow automates the entire daily reporting cycle for medical representatives (MRs) — assigning daily visits from Google Sheets, emailing task details, sending reminders to those who haven’t submitted updates, converting form responses into structured AI summaries using OpenAI, and emailing consolidated daily reports to managers. :contentReference[oaicite:1]{index=1}

---

## ⚡ Quick Start – Implementation Steps

1. Connect your **Google Sheets credentials** in all relevant nodes. :contentReference[oaicite:2]{index=2}
2. Update the `documentId` and `sheetName (gid)` for **MR Plan** and **Form Responses** sheets. :contentReference[oaicite:3]{index=3}
3. Add **Gmail OAuth credentials** for sending emails. :contentReference[oaicite:4]{index=4}
4. Ensure your **Google Form link** is present in the MR plan sheet. :contentReference[oaicite:5]{index=5}
5. Add **OpenAI credentials** for the AI Agent and Chat Model nodes. :contentReference[oaicite:6]{index=6}
6. Adjust all three **Schedule Trigger** nodes to your preferred timing (morning/afternoon/night). :contentReference[oaicite:7]{index=7}
7. Run a complete test execution to confirm messaging and summary behavior. :contentReference[oaicite:8]{index=8}

---

## 📌 What It Does

This workflow handles:

- **Daily visit assignment (Morning)** — Reads the MR Plan sheet; finds pending visits; emails each MR their visit details and reporting form link; updates the sheet status. :contentReference[oaicite:9]{index=9}
- **Reminder flow (Evening)** — Checks which MRs haven’t submitted responses; sends reminder emails with links and marks rows accordingly. :contentReference[oaicite:10]{index=10}
- **Reporting & AI Summary (Night)** — Reads the form responses; runs AI processing to normalize and extract key points; generates structured summaries; emails a consolidated summary to the manager. :contentReference[oaicite:11]{index=11}

This workflow reduces manual follow‑ups, improves consistency, and ensures managers get timely, structured daily summaries. :contentReference[oaicite:12]{index=12}

---

## 👥 Who’s It For

- **Pharma field‑force teams** (Medical Reps, Area Sales Managers, Regional Sales Managers). :contentReference[oaicite:13]{index=13}
- **Organizations with daily client or appointment‑based visits.** :contentReference[oaicite:14]{index=14}
- **Ops teams** that want automated reminders and reporting. :contentReference[oaicite:15]{index=15}
- **Managers** needing concise daily summaries from field updates. :contentReference[oaicite:16]{index=16}
- **Automation teams** using Google Sheets, Gmail, and AI to streamline workflows. :contentReference[oaicite:17]{index=17}

---

## 🛠 Requirements

To use this workflow you need:

- A **Google Sheet** containing daily MR visit assignments. :contentReference[oaicite:18]{index=18}
- A **Google Sheet** capturing responses from your visit reporting Google Form. :contentReference[oaicite:19]{index=19}
- Valid **Gmail OAuth credentials** for sending emails. :contentReference[oaicite:20]{index=20}
- **Google Sheets OAuth credentials** configured in n8n. :contentReference[oaicite:21]{index=21}
- **OpenAI credentials** for AI summarization via the AI Agent/Chat Model nodes. :contentReference[oaicite:22]{index=22}
- A working **Google Form** for MR visit reporting. :contentReference[oaicite:23]{index=23}
- Properly configured **Schedule Trigger** nodes for morning, evening, and night automation. :contentReference[oaicite:24]{index=24}

---

## ⚙️ How It Works & Setup

### 1. Morning — Daily Visit Assignment

- A **Schedule Trigger** starts the workflow at the configured morning time. :contentReference[oaicite:25]{index=25}
- The MR Plan sheet is read to find all rows where `Status = Pending`. :contentReference[oaicite:26]{index=26}
- For each pending record, the MR receives an email with visit details and the form link. :contentReference[oaicite:27]{index=27}
- The same row is updated in Sheets to mark `Status = Assigned`. :contentReference[oaicite:28]{index=28}

---

### 2. Evening — Reminder Emails

- A second **Schedule Trigger** fires at your chosen evening time. :contentReference[oaicite:29]{index=29}
- The workflow reads all records where `Status = Pending`. :contentReference[oaicite:30]{index=30}
- Each MR who hasn’t submitted an update receives a reminder email. :contentReference[oaicite:31]{index=31}
- The sheet is updated with `Reminder = Yes`. :contentReference[oaicite:32]{index=32}

---

### 3. Night — Summary Reporting

- A third scheduled trigger begins after business hours. :contentReference[oaicite:33]{index=33}
- All form responses from the “Form Responses 1” sheet are read. :contentReference[oaicite:34]{index=34}
- Each response is passed to the **AI Agent** node for normalization and summarization. :contentReference[oaicite:35]{index=35}
- The summary output is compiled and emailed to the manager via Gmail. :contentReference[oaicite:36]{index=36}

---

## 🛠 How to Customize Nodes

### Google Sheets Nodes

- Change row filters (e.g., by date range or specific MR). :contentReference[oaicite:37]{index=37}
- Adjust column mappings in node settings. :contentReference[oaicite:38]{index=38}
- Replace or update `Status` logic if your sheet uses different labels. :contentReference[oaicite:39]{index=39}

### Gmail Nodes

- Modify email subjects and body formatting. :contentReference[oaicite:40]{index=40}
- Use CC or BCC fields for secondary notifications. :contentReference[oaicite:41]{index=41}

### AI Agent Node

- Update the AI instructions for different summary styles (e.g., bullet points, action items). :contentReference[oaicite:42]{index=42}
- Tailor prompts to match your form data structure. :contentReference[oaicite:43]{index=43}

### Schedule Trigger Nodes

- Adjust trigger times for your time zone and operational schedule. :contentReference[oaicite:44]{index=44}

---

## ➕ Add‑Ons (Optional Extensions)

You can extend this workflow with:

- **Slack or Teams notifications** for reminders or final summaries. :contentReference[oaicite:45]{index=45}
- **Daily export of summaries** to Google Sheets or shared folders. :contentReference[oaicite:46]{index=46}
- **WhatsApp/SMS reminders** via Twilio integration. :contentReference[oaicite:47]{index=47}
- **Push AI summaries into CRM systems** for record keeping. :contentReference[oaicite:48]{index=48}
- **Automatic backups** of MR plan and responses. :contentReference[oaicite:49]{index=49}

---

## 📈 Use Case Examples

1. **Daily MR field work planning & reporting** in pharma or healthcare. :contentReference[oaicite:50]{index=50}
2. **Sales teams** performing client visits with automated follow‑ups. :contentReference[oaicite:51]{index=51}
3. **Service engineers** logging on‑site work with instant reminders. :contentReference[oaicite:52]{index=52}
4. **Outreach teams** conducting scheduled visits and summaries. :contentReference[oaicite:53]{index=53}
5. **Real estate field agents** tracking property visits and daily reports. :contentReference[oaicite:54]{index=54}

---

## 🧪 Troubleshooting Guide

| **Issue**               | **Possible Cause**                                      | **Solution**                              |
| ----------------------- | ------------------------------------------------------- | ----------------------------------------- | --------------------------------------- |
| Emails not sending      | Gmail OAuth expired or disconnected                     | Reconnect Gmail credentials               |
| Sheets data not loading | Wrong sheet ID or GID                                   | Confirm IDs from Google Sheets URL        |
| Rows not updating       | Column names differ from workflow mapping               | Align spreadsheet column names            |
| AI summary missing      | OpenAI credentials missing or unexpected form structure | Check OpenAI credentials and data format  |
| Summary email blank     | Parsed AI output lacks expected fields                  | Inspect AI Agent output in execution logs | :contentReference[oaicite:55]{index=55} |

---

## 💬 Need Help?

If you’d like assistance setting up, testing, or extending this workflow — including adapting it to your organization, enhancing AI summaries, or connecting it with external systems — the **WeblineIndia n8n workflow development team** can help with professional automation services, support, and custom add‑ons. :contentReference[oaicite:56]{index=56}

---
