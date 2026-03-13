<img width="1919" height="1079" alt="Form Verification Screenshot" src="https://github.com/user-attachments/assets/ed28102e-b3a8-4e3f-a9b4-a1403f799372" />

# 📝 AI-Powered Form Verification & Triage Workflow

Streamline your lead generation process with this **n8n workflow**. It automatically triages incoming form submissions using advanced AI (GPT-5.2-Pro), verifies email addresses via NeverBounce, and sends real-time notifications to your team via Google Chat and Gmail.

## 🚀 What Does This Workflow Do?

- **Google Sheets Trigger**: Monitors a Google Sheet for new form submissions (e.g., website contact leads).
- **AI Triage (GPT-5.2-Pro)**: Sends the submission data to OpenAI's latest model to classify the lead as "Lead", "Spam", or "Testing".
- **Data Transformation**: A custom JavaScript node extracts and formats key fields such as Name, Email, Phone, Zip, Service, and Entry ID.
- **Categorization Logic**: Uses conditional branching (If node) to handle leads differently from spam or test submissions.
- **Email Verification**: For valid "Lead" submissions, it automatically verifies the email address using the NeverBounce API.
- **Real-Time Alerts**: Sends a detailed summary of the new lead to dedicated Google Chat spaces.
- **Automated Notifications**: Delivers the lead's information to the legal team via Gmail for immediate follow-up.
- **Sheet Synchronization**: Updates the original Google Sheet with the AI status, verification results, and email timestamps.

## 📂 Folder Contents

```
Form Verification/
├── Form_Verification.json
└── README.md
```

## 🛠️ Setup & Usage Instructions

### 1. **Import Workflow**

- Download or copy the `Form_Verification.json` file.
- In your n8n instance, go to **Workflows > Import Workflow** and upload the file.

### 2. **Configure Credentials**

- **Google Sheets**: Set up Google Sheets Trigger credentials to watch for new entries.
- **OpenAI API**: Set up your OpenAI credentials for GPT-5.2-Pro triage.
- **NeverBounce API**: Configure your NeverBounce API key in the **HTTP Request1** node.
- **Google Chat API**: Set up credentials for sending alerts to your team.
- **Gmail API**: Configure credentials for sending lead notifications.

### 3. **Customize Nodes**

- **Google Sheets Trigger**: Update the `documentId` and `sheetName` to point to your leads sheet.
- **AI Triage Prompt**: Tailor the system instructions in the **Message a model** node for your specific industry (default is law firm triage).
- **Email Recipients**: Update the email addresses in the **Send a message** node to notify the correct team members.
- **Google Chat Spaces**: Update the `spaceId` in the **Google Chat** nodes to point to your internal communication channels.

### 4. **Run the Workflow**

- The workflow is triggered automatically when a new row is added to your monitored Google Sheet.
- You can also manually execute it for testing by pinning data in the trigger node.

## 💡 Workflow Overview

1. **Google Sheets Trigger**: Detects new form entries.
2. **Message a model (AI)**: Classifies the lead (GPT-5.2-Pro).
3. **Code in JavaScript1**: Formats submission and AI output.
4. **Update row in sheet6**: Logs the initial AI classification.
5. **If2 (Decision Node)**: Branches based on "AI Status" (Lead vs. Spam/Test).
6. **HTTP Request1 (NeverBounce)**: Verifies the lead's email authenticity.
7. **Google Chat / Chat2**: Sends notifications to team channels.
8. **Send a message (Gmail)**: Notifies the legal/sales team.
9. **Update row in sheet4**: Finalizes the record with verification and send logs.

## 🙋‍♂️ Author

- **Dhruba Datta**  
  Email: [dhrubadattaanjan@gmail.com](mailto:dhrubadattaanjan@gmail.com)  
  Website: [https://dhruba-datta.netlify.app/](https://dhruba-datta.netlify.app/)

---

⭐ Found this useful? Star the repo & let's automate your lead verification! 🚀
---
