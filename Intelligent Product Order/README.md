<img width="1512" height="949" alt="image" src="https://github.com/user-attachments/assets/ef8600d0-d527-456a-a061-acdebdf90f39" />

# 📦 Intelligent Product Order Automation

Streamline your order management with this **n8n workflow** — it syncs product catalogs, intelligently extracts order details from emails using AI, and automatically creates tasks in Monday.com for fulfillment.

## 🚀 What Does This Workflow Do?

This workflow consists of two main parts:

### Part A: Product Data Sync

- **Fetches Product Data**: Retrieves product information from multiple external JSON sources (Github Gists).
- **Consolidates Data**: Merges data from multiple pages into a single dataset.
- **Syncs to Google Sheets**: Upserts product details (ID, Name, Price, Category) into a **"Products"** Google Sheet to maintain an up-to-date catalog.

### Part B: Smart Order Processing

- **Monitors Emails**: Watch a Gmail inbox for new incoming emails.
- **AI Extraction**: Uses **OpenAI (GPT-3.5)** to parse unstructured email text and extract structured order data:
  - Intent (e.g., "order")
  - Product ID & Name
  - Quantity
  - Customer Details (Name, Phone, Address)
  - Requested Delivery Date
  - Priority
- **Product Verification**: Cross-references the extracted Product ID with the **"Products"** Google Sheet to fetch accurate pricing and category details.
- **Task Creation**:
  - Creates a new item in **Monday.com** with a clear title (e.g., "Order: Red T-Shirt").
  - Adds a detailed update to the item containing all order specifics formatted for easy reading.

## 📂 Folder Contents

```
intelligent-product-order/
├── Intelligent_Product_Order.json
└── README.md
```

## 🛠️ Setup & Usage Instructions

### 1. **Import Workflow**

- Download the `Intelligent_Product_Order.json` file.
- In your n8n instance, go to **Workflows > Import Workflow** and upload the file.

### 2. **Configure Credentials**

You will need to set up and select the following credentials in the respective nodes:

- **Google Sheets OAuth2 API**: For reading/writing the product catalog.
- **Gmail OAuth2**: For reading incoming order emails.
- **OpenAI API**: For the AI text extraction model.
- **Monday.com API**: For creating tasks on your board.

### 3. **Customize Google Sheets**

- Create a Google Sheet.
- Rename the tab/sheet reference in the nodes or ensure your sheet matches (e.g., Sheet name `Sheet1` or `Products`).
- Ensure columns exist for: `ID`, `Name`, `Price`, and `Category`.
- Update the **Sheet ID** in nodes **A4** and **B5**.

### 4. **Configure Monday.com**

- Update the **Board ID** and **Group ID** in the Monday.com nodes (**B7**, **B8**) to match your target board.

### 5. **Run the Workflow**

- **Product Sync**: Run the manual trigger ("When clicking ‘Execute workflow’") periodically to update your product list.
- **Order Processing**: Activate the workflow. It will automatically run every minute (or as configured) to check for new emails.

## 💡 Workflow Overview

### Part A: Catalog Management

1.  **Fetch & Merge**: Pulls JSON data from remote URLs.
2.  **Update Sheet**: Adds or updates rows in Google Sheets based on Product ID.

### Part B: Order Automation

1.  **Email Trigger**: Detects new emails.
2.  **AI Analysis**: OpenAI transforms email body text into a JSON object.
3.  **Filter**: Proceeds only if the email intent is classified as an "order".
4.  **Lookup**: Finds the product in Google Sheets to validate existence and get details.
5.  **Create Task**: Pushes the validated order to Monday.com.

## 📝 Notes & Recommendations

- **AI Model**: The workflow is configured for `gpt-3.5-turbo`. You can switch to `gpt-4` in node **B3** for potentially higher accuracy with complex emails.
- **Data Safety**: The content is processed by OpenAI. Ensure no sensitive PII that violates your compliance standards is sent if that is a concern.
- **Error Handling**: The workflow includes checks to ensure JSON is parsed correctly from the AI response.

## 🙋‍♂️ Author

- **Dhruba Datta**  
  Email: [dhrubadattaanjan@gmail.com](mailto:dhrubadattaanjan@gmail.com)  
  Website: [https://dhruba-datta.netlify.app/](https://dhruba-datta.netlify.app/)

## 🌟 Contribution & Support

- Fork the repository, add improvements or new workflows, and submit pull requests.
- Open issues or join the discussion on the n8n community forums.
- Reach out via email for direct inquiries.

---

⭐ Found this useful? Star the repo & let's automate your order processing! 🛒
