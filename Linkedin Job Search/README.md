# 🔎 LinkedIn Job Search Automation Workflow

Unlock smarter job searching with this **n8n workflow** — automate LinkedIn job searches and save results directly to Google Sheets!  
This workflow dynamically builds search URLs, scrapes job data, and stores results for easy filtering and follow-up.

<br>

## 🚀 What Does This Workflow Do?

- Accepts user input for **keywords, job type, and experience level** via an n8n web form.
- Automatically constructs a custom LinkedIn search URL based on your criteria.
- Scrapes job postings and extracts:
  - Job title
  - Company
  - Location
  - Description
  - Direct apply link
- **Appends results to a Google Sheet** for tracking and later review.

<br>

## 📂 Folder Contents

```
linkedin-job-search/
├── LinkedIn_Job_Search.json
└── README.md
```

<br>

## 🛠️ Setup & Usage Guide

### 1. **Import Workflow**

- Download or copy the `LinkedIn_Job_Search.json` file.
- In your n8n instance, go to **Workflows > Import Workflow** and upload the file.

### 2. **Set Up Google Sheets Credentials**

- This workflow requires a connected Google Sheets account.
- In n8n, navigate to **Credentials** and set up a new **Google Sheets OAuth2 API** credential.
- Edit the workflow and assign this credential to the "**Google Sheets**" node.

### 3. **Customize Your Sheet**

- By default, the workflow appends job results to a specific Google Sheet and tab:
  - Replace the `documentId` and `sheetName` in the "Google Sheets" node with your own.
- Columns used: `title`, `company`, `location`, `description`, `jobid`, `applyLink`.

### 4. **Trigger the Workflow**

- Open the **webhook URL** from the "**On form submission**" node (grab it from node details).
- Fill out the web form:
  - **Job Role** (relevant search term)
  - **Keywords** (comma separated)
  - **Experience Level** (select one or more)
  - **Job Type** (On-site, Remote, Hybrid)
- Submit the form to start the automation!

<br>

## 💡 Workflow Overview

1. **Input Form:**  
   You provide search criteria via an n8n-generated form.
2. **URL Builder:**  
   The workflow creates a LinkedIn job search URL with codes for your selected filters.
3. **Data Fetching & Extraction:**  
   Job links are scraped, individual job pages fetched, and data extracted.
4. **Google Sheets Output:**  
   Cleaned, formatted job data is appended as new rows in your Google Sheet.

<br>

## 📝 Notes & Tips

- **Strongly recommended:** Limit frequency of runs to avoid LinkedIn rate limits.
- All scraping is done with generic selectors; job posting markup may change, so review selectors if results appear incomplete.
- By default, the workflow filters for USA jobs (GeoId hardcoded to US).
- You’re free to modify and extend this workflow for your location, fields, or target sheet.

<br>

## 🙋‍♂️ Author

- **Dhruba Datta**  
  Email: [dhrubadattaanjan@gmail.com](mailto:dhrubadattaanjan@gmail.com)  
  Website: [https://dhruba-datta.netlify.app/](https://dhruba-datta.netlify.app/)

<br>

## 🌟 Contributing

- Add your enhancements, customizations, or new workflows:
  1. Fork this repo
  2. Place your `.json` and a `README.md` in a new folder
  3. Open a pull request

<br>

## ❓ Need Help?

- 🐞 [Open an issue](https://github.com/your-username/n8n-workflows/issues)
- 💬 Community: [n8n Forum](https://community.n8n.io)
- 📧 Reach out via email (above)

<br>

---

<p align="center">
  ⭐ <b>Found this useful? Star the repo &amp; Let’s automate the world together! 🌍</b>
</p>

---
