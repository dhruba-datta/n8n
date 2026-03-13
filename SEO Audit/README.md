<img width="1919" height="1079" alt="SEO Audit Screenshot" src="https://github.com/user-attachments/assets/ed28102e-b3a8-4e3f-a9b4-a1403f799372" />

# 🔍 SEO Audit & Performance Workflow

Optimize your website's search engine visibility and loading speed with this **n8n workflow**. It automates website performance analysis using Google PageSpeed Insights, generates a professional audit report using GPT-4, and sends it directly to your clients via Gmail.

## 🚀 What Does This Workflow Do?

- **Webhook Trigger**: Receives website URL, name, and email from an external source (e.g., a contact form).
- **Google Sheets Logging**: Logs every audit request into a Google Sheet for tracking and lead management.
- **Performance Analysis**: Connects to Google PageSpeed Online API to fetch mobile performance metrics (Lighthouse).
- **Metric Extraction**: Uses a custom JavaScript node to extract key metrics like Performance Score, First Contentful Paint, Load Time, and Mobile Friendliness.
- **AI-Powered Audit**: Sends performance data to OpenAI (GPT-4) to generate a concise, persuasive business audit.
- **Automated Emailing**: Sends a beautifully formatted HTML email via Gmail to the client with their audit results and a call to action.

## 📂 Folder Contents

```
SEO Audit/
├── SEO_Audit.json
└── README.md
```

## 🛠️ Setup & Usage Instructions

### 1. **Import Workflow**

- Download or copy the `SEO_Audit.json` file.
- In your n8n instance, go to **Workflows > Import Workflow** and upload the file.

### 2. **Configure Credentials**

- **Google Sheets**: Set up Google Sheets OAuth2 credentials for logging audit requests.
- **OpenAI API**: Set up your OpenAI credentials to enable GPT-4 analysis.
- **Gmail API**: Set up Gmail OAuth2 credentials to send the audit reports.

### 3. **Customize Nodes**

- **Google Sheets**: Update the `documentId` and `sheetName` in the **Append row in sheet** node.
- **GPT-4 Prompt**: You can customize the AI's persona or audit rules in the **Message a model** node.
- **Email Template**: Modify the HTML in the **Send a message** node to match your agency's branding.
- **Google API Key**: Ensure you have a valid Google API key in the **HTTP Request** node for PageSpeed Insights.

### 4. **Run the Workflow**

- Send a POST request to the **Webhook URL** with the following JSON body:
```json
{
  "url": "https://example.com",
  "name": "Client Name",
  "email": "client@example.com"
}
```
- The workflow will automatically process the audit and send the email.

## 💡 Workflow Overview

1. **Webhook**: Receives client data.
2. **Edit Fields**: Formats query parameters.
3. **Append row in sheet**: Logs request data.
4. **HTTP Request**: Calls PageSpeed Insights API.
5. **Code in JavaScript**: Processes Lighthouse metrics.
6. **Message a model (AI)**: Generates the audit report.
7. **Code in JavaScript1**: Parses AI response.
8. **Send a message (Gmail)**: Delivers the report to the client.

## 🙋‍♂️ Author

- **Dhruba Datta**  
  Email: [dhrubadattaanjan@gmail.com](mailto:dhrubadattaanjan@gmail.com)  
  Website: [https://dhruba-datta.netlify.app/](https://dhruba-datta.netlify.app/)

---

⭐ Found this useful? Star the repo & let's automate your SEO audits! 🚀
---
