# 🎯 Dice Job Search Automation Workflow

Automate **Dice.com** job searches for multiple states, capture only fresh postings, and store results directly in Google Sheets — with optional email alerts to your team.

This workflow dynamically builds Dice search URLs, scrapes job data, and formats results for easy tracking and review.

<br>

## 🚀 What Does This Workflow Do?

- Accepts your **target role**, list of **U.S. states**, and **pages per state**.
- Automatically constructs custom Dice search URLs for each state and page.
- Filters jobs posted **in the last 24 hours**.
- Scrapes and extracts:

  - Serial number
  - Job title
  - Company
  - Location
  - Posted date/time (formatted)
  - Employment type
  - Salary
  - Direct job link

- **Appends results to a Google Sheet**.
- **(Optional)** Sends an email notification with a link to the updated sheet.

<br>

## 📂 Folder Contents

```
dice-job-search/
├── Dice_Job_Search.json
└── README.md
```

<br>

## 🛠️ Setup & Usage Guide

### 1. **Import Workflow**

- Download or copy the `Dice_Job_Search.json` file.
- In n8n, go to **Workflows > Import Workflow** and upload the file.

### 2. **Set Up Google Sheets Credentials**

- In **n8n > Credentials**, create a **Google Sheets OAuth2 API** credential.
- Assign it to the "**Google Sheets**" node.

### 3. **Customize Search Criteria**

- In the "**Customize Your Search**" node, update:

  - `role` → Job title (e.g., `"Business Analyst"`)
  - `states` → Array of U.S. state codes (e.g., `["TX", "NY", "MI", "MA"]`)
  - `pagesPerState` → Number of pages to scrape per state

- This workflow is preset to filter for **CONTRACTS | THIRD_PARTY** roles posted in the **last 24 hours**.

### 4. **Configure Google Sheets Output**

- Replace `documentId` and `sheetName` with your own in the "**Google Sheets**" node.
- Required columns:
  `Serial_No.`, `Title`, `Link`, `Company`, `Location`, `Posted`, `Employment_Type`, `Salary`, `error`.

### 5. **Email Notifications (Optional)**

- In the "**Gmail**" node:

  - Update `sendTo` with your recipients.
  - Edit `subject` and `message`.

- Ensure Gmail API credentials are configured.

### 6. **Run the Workflow**

- Use the "**When clicking ‘Test workflow’**" node to run manually.
- Or add a schedule trigger for automation.

<br>

## 🗺️ Workflow Diagram

```mermaid
flowchart LR
    A[When clicking 'Test workflow'] --> B[Customize Your Search\n(Build Dice URLs)]
    B --> C[Loop Over Items]
    C -->|Branch 1| D[Gmail Notification (Optional)]
    C -->|Branch 2| E[Dice Search\n(Fetch HTML)]
    E --> F[Parse HTML into Job Data]
    F --> G[Google Sheets\n(Append Results)]
    G --> C
```

<br>

## 💡 Workflow Overview

1. **Input & URL Generation** – Role & states are used to build paginated Dice search URLs.
2. **Data Fetching** – HTML pages are downloaded.
3. **Parsing** – Extracts job details and formats posted dates.
4. **Output** – Writes results into Google Sheets.
5. **Notification** – Optionally sends an email with the sheet link.

<br>

## 📝 Notes & Tips

- Avoid excessive runs to prevent rate limits from Dice.
- HTML selectors may need updating if Dice changes their page layout.
- Currently optimized for **U.S.-based searches**.

<br>

## 🙋‍♂️ Author

- **Dhruba Datta**  
  Email: [dhrubadattaanjan@gmail.com](mailto:dhrubadattaanjan@gmail.com)  
  Website: [https://dhruba-datta.netlify.app/](https://dhruba-datta.netlify.app/)

<br>

## 🌟 Contributing

- Fork this repo and add your `.json` and `README.md` for other job sites or enhancements.
- Submit a pull request to share your improvements.

---

<p align="center">
  ⭐ <b>Found this useful? Star the repo &amp; Let’s automate the world together! 🌍</b>
</p>

---
