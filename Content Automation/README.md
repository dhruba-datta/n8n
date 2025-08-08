<img width="1919" height="1079" alt="Screenshot 2025-08-08 192109" src="https://github.com/user-attachments/assets/1f6a8227-69e3-49b9-81d1-220177c07fe8" />

# ✨ Content Automation Workflow

Boost your content creation process with this **n8n workflow** — automate the generation of engaging social media content and seamlessly manage it with Google Sheets and Trello! This workflow pulls client data, generates tailored content ideas using AI, and organizes them in your Trello backlog for easy tracking.

<br>

## 🚀 What Does This Workflow Do?

- Retrieves client information from a **Google Sheet** (e.g., industry, audience, content goals).
- Generates **3 unique social media content ideas** for each content type using OpenAI (GPT-4o-mini).
- Formats the content ideas (hook, subtitle, CTA) and creates a new **Trello card** in the client’s backlog.
- Loops through multiple content types to ensure comprehensive content planning.

<br>

## 📂 Folder Contents

```
content-automation/
├── Content_Automation.json
└── README.md
```

<br>

## 🛠️ Setup & Usage Guide

### 1. **Import Workflow**

- Download or copy the `Content_Automation.json` file.
- In your n8n instance, go to **Workflows > Import Workflow** and upload the file.

### 2. **Set Up Credentials**

- **Google Sheets**:
  - Navigate to **Credentials** in n8n and set up a new **Google Sheets OAuth2 API** credential.
  - Assign this credential to the "**Google Sheets**" node in the workflow.
- **OpenAI**:
  - Set up an **OpenAI API** credential in n8n and assign it to the "**OpenAI**" node.
- **Trello**:
  - Create a **Trello API** credential and assign it to both the "**Find Trello Card Backlog**" and "**New Card in Trello**" nodes.

### 3. **Customize Your Google Sheet**

- The workflow reads client data from a Google Sheet:
  - Replace the `documentId` and `sheetName` in the "**Google Sheets**" node with your own Google Sheet ID and tab name.
- Expected columns in the Google Sheet:
  - `ChatGPT Role`, `Client`, `Content Types`, `Industry`, `Primary Service`, `Target Condition`, `Audience`, `Content Goal`, `USP`, `Call To Action`, `Compliance Layer`, `Tone`, `Special Add-ons`, `Content Pillar`, `Platform`, `Backlog` (Trello list ID).

### 4. **Set Up Trello**

- Ensure you have a Trello board with a **Backlog list** for storing content ideas.
- Update the Trello list ID manually in the Google Sheet’s `Backlog` column for each client, or use the "**Find Trello Card Backlog**" node to retrieve it dynamically.

### 5. **Trigger the Workflow**

- Run the workflow manually by clicking **Test Workflow** in n8n.
- The workflow will:
  - Fetch client data from the Google Sheet.
  - Generate 3 unique content ideas per content type using OpenAI.
  - Create a Trello card for each content idea in the specified backlog.

<br>

## 💡 Workflow Overview

1. **Google Sheets Input**:
   - Pulls client details (e.g., content type, industry, audience) from a Google Sheet.
2. **Content Type Splitting**:
   - Splits the `Content Types` array (e.g., Educational, Conversion Focused) for individual processing.
3. **AI Content Generation**:
   - Uses OpenAI (GPT-4o-mini) to generate 3 unique content sets (hook, subtitle, CTA) per content type, adhering to compliance and tone requirements.
4. **Content Formatting**:
   - Formats the AI-generated content into a readable string using a custom code node.
5. **Trello Integration**:
   - Creates a Trello card in the client’s backlog with the content type, topic name, and formatted content.
6. **Looping**:
   - Iterates through all content types to ensure all ideas are processed.

<br>

## 📝 Notes & Tips

- **Content Types**: The workflow uses predefined content types (Educational Content, Conversion Focused, Service-Based Content, Community & Trust, Seasonal & Trending Content). Modify these in the Google Sheet or "**Edit Fields**" node as needed.
- **Rate Limits**: Be cautious with OpenAI and Trello API rate limits. Adjust execution frequency if necessary.
- **Compliance**: Ensure the `Compliance Layer` and `Special Add-ons` fields in your Google Sheet align with your content requirements.
- **Customization**: Modify the OpenAI prompt in the "**OpenAI**" node to tailor content generation to your specific needs.
- **Trello List ID**: The `Backlog` column in the Google Sheet must contain valid Trello list IDs. Use the "**Find Trello Card Backlog**" node to retrieve these if needed.

<br>

## 🙋‍♂️ Author

- **Dhruba Datta**  
  Email: [dhrubadattaanjan@gmail.com](mailto:dhrubadattaanjan@gmail.com)  
  Website: [https://dhruba-datta.netlify.app/](https://dhruba-datta.netlify.app/)

<br>

## 🌟 Contributing

- Add your enhancements, customizations, or new workflows:
  1. Fork this repo.
  2. Place your `.json` workflow file and a `README.md` in a new folder.
  3. Open a pull request.

<br>

## ❓ Need Help?

- 🐞 [Open an issue](https://github.com/your-username/n8n-workflows/issues)
- 💬 Community: [n8n Forum](https://community.n8n.io)
- 📧 Reach out via email (above)

<br>

---

<p align="center">
  ⭐ <b>Found this useful? Star the repo &amp; Let’s automate content creation together! 🌍</b>
</p>

---
