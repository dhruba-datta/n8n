# 💌 Brevo Email Marketing Automation Workflow

Boost your email marketing campaigns with this **n8n workflow** — automate importing contacts from Google Sheets, adding them to Brevo, sending templated emails, tracking engagement, managing email credits, and cleaning up contacts efficiently.

## 🚀 What Does This Workflow Do?

- Retrieves new contacts marked **"Not Added"** from the **New Contacts** tab in your Google Sheet.
- Adds or upserts these contacts (email, name, job title) into Brevo’s contact list using Brevo API.
- Sends an initial email using a predefined Brevo email template to each new contact.
- Logs sent email status and timestamp in the **Emailed Contacts** tab.
- Monitors email engagement (opens, clicks) from Brevo webhook triggers.
- Updates engagement status (e.g., **"Clicked"**) back into Google Sheets.
- Tracks email sending credits from Brevo account and sends alerts via Google Chat when limits are approaching or exceeded.
- Batches requests and uses wait nodes to comply with Brevo API rate limits.
- Deletes contacts from Brevo after campaign completion to keep the list clean.
- Synchronizes contact statuses across multiple Google Sheets tabs — **New Contacts**, **Emailed Contacts**, **Triggered Contacts**, **Cold Call Contacts** — for smooth workflow management.

## 📂 Folder Contents

```
brevo-email-marketing/
├── Brevo_Email_Marketing.json
└── README.md
```

## 🛠️ Setup & Usage Instructions

### 1. **Import Workflow**

- Download or copy the `Brevo_Email_Marketing.json` file.
- In your n8n instance, go to **Workflows > Import Workflow** and upload the file.

### 2. **Configure Credentials**

- **Google Sheets**:  
    Set up Google Sheets OAuth2 credentials and assign it to all the Google Sheets nodes.
- **Brevo (Sendinblue) API**:  
    Set up your Brevo API credentials in n8n and assign them to all Brevo nodes.
- **Google Chat API**:  
    Set up credentials for Google Chat to enable sending notifications.

### 3. **Customize Google Sheets**

- Replace the `documentId` and `sheetName` in **Google Sheets** nodes to point to your own Google Sheet and corresponding tabs.
- Your Google Sheet should have tabs named **New Contacts**, **Emailed Contacts**, **Triggered Contacts**, **Cold Call Contacts** with columns such as:  
    `ID`, `Name`, `Emails`, `Type`, `Rating`, `Verified`, `Reviews`, `Website`, `Status`, `Brevo`, `Clicked`, etc., matching the workflow’s expected schema.
- Use consistent data to allow smooth matching and updating in the workflow.

### 4. **Setup Brevo Email Templates**

- Configure your email templates in Brevo and update the template IDs in the workflow nodes for initial and follow-up emails.

### 5. **Run the Workflow**

- Trigger the workflow manually or schedule it as desired.
- The workflow will:  
    - Fetch eligible contacts who are not added yet.  
    - Add contacts to Brevo, send emails, and update statuses on sheets.  
    - Monitor engagement triggers and reflect engagement on Google Sheets.  
    - Manage email credits and send Google Chat alerts when close to limits.

## 💡 Workflow Overview

1. **Fetch New Contacts:**  
      Pull contacts marked "Not Added" from Google Sheet.

2. **Add to Brevo:**  
      Upsert contacts via Brevo API.

3. **Send Initial Email:**  
      Send predefined email template.

4. **Update Status:**  
      Mark contacts as "Added" and "Email Sent" with date.

5. **Engagement Tracking:**  
      Receive open/click webhooks from Brevo and update Google Sheets status.

6. **Credit Monitoring:**  
      Check email send credits and notify on Google Chat.

7. **Follow Up & Clean Up:**  
      Manage follow-up sends, batch processing, contact deletions post-campaign.

8. **Synchronization:**  
      Keep contact statuses in sync across multiple sheets and tabs.

## 📝 Notes & Recommendations

- **API Rate Limits:**  
    The workflow has built-in waits and batch processing to avoid Brevo API limits but monitor your limits closely.

- **Email Templates:**  
    Update email template IDs in the respective nodes to reflect your current campaigns.

- **Google Sheets Structure:**  
    Maintain consistent columns and data formats for seamless operation.

- **Error Handling:**  
    Some delete operations continue on errors to ensure workflow robustness.

- **Scheduling:**  
    Enable and customize schedule triggers based on your campaign frequency.

## 🙋♂️ Author

- **Dhruba Datta**  
    Email: [dhrubadattaanjan@gmail.com](mailto:dhrubadattaanjan@gmail.com)  
    Website: [https://dhruba-datta.netlify.app/](https://dhruba-datta.netlify.app/)

## 🌟 Contribution & Support

- Fork the repository, add improvements or new workflows, and submit pull requests.
- Open issues or join the discussion on the n8n community forums.
- Reach out via email for direct inquiries.

---

⭐ Found this useful? Star the repo &amp; let's automate your email marketing with Brevo! 📧

---
