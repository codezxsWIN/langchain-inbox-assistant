
# 🔐 Authentication Setup for LangChain Inbox Assistant

This guide walks you through setting up authentication for **Gmail API** and **Google Sheets API** using OAuth 2.0 and a Service Account.

---

## 📩 1. Gmail API (User OAuth Consent Flow)

### ✅ Create OAuth Credentials for Gmail

1. Go to [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
2. Select or create a project
3. In the left sidebar, go to **"OAuth consent screen"**
   - App name: LangchainInboxComplaint (or your app name)
   - User support email: your Gmail
   - Add yourself as a **Test User**
4. Go to **"Credentials" > "Create Credentials" > OAuth client ID**
   - App type: **Desktop App**
   - Download the file and rename it to: `client_secret2.json`
5. Place `client_secret2.json` in the same folder as your `.ipynb` file

### 🧪 First-time Authentication

- The app will launch a browser for login (`flow.run_local_server(port=0)`)
- After login, access token is saved to `token.json`
- You will only need to authenticate once unless token expires

---

## 📊 2. Google Sheets API (Service Account)

### ✅ Create a Google Sheets Service Account

1. Go to [Google Cloud Console > IAM & Admin > Service Accounts](https://console.cloud.google.com/iam-admin/serviceaccounts)
2. Click **“Create Service Account”**
3. Name it (e.g. `LangchainSheetsAgent`)
4. Click “Create and Continue” (no role needed)
5. Click “Done”

### 🔑 Generate JSON Credentials

1. Find your new service account → Click **Actions > Manage keys**
2. Add Key > Create new key > **JSON**
3. Save the file as `projectemailsorter-62df267deeed.json` (or similar)
4. Place this file next to your `.ipynb`

### 📝 Share Your Sheet With the Service Account

1. Open your target Google Sheet (e.g., named `LangChain`)
2. Click **Share**
3. Add the **client email** from your service account JSON file
   Example:
   ```text
   langchain-sheets@yourproject.iam.gserviceaccount.com
   ```
4. Give it **Editor** access

---

## 🧪 Verifying Setup

### Gmail Auth Test:
```python
gmail_service = authenticate_gmail()
labels = gmail_service.users().labels().list(userId='me').execute()
print([label['name'] for label in labels['labels']])
```

### Google Sheets Test:
```python
import gspread
from oauth2client.service_account import ServiceAccountCredentials

scope = ["https://spreadsheets.google.com/feeds", "https://www.googleapis.com/auth/drive"]
creds = ServiceAccountCredentials.from_json_keyfile_name("projectemailsorter-62df267deeed.json", scope)
client = gspread.authorize(creds)
sheet = client.open("LangChain").sheet1
sheet.update("A1", [["✅ Connected to Sheet"]])
```

---

## 📁 Final Required Files

| File Name                           | Purpose                  |
|------------------------------------|---------------------------|
| `client_secret2.json`              | Gmail OAuth desktop login |
| `token.json`                       | Saved user Gmail token    |
| `projectemailsorter-62df267deeed.json` | Sheets service account     |

---

## ✅ You're Ready

Once both Gmail and Sheets are connected, the notebook can:
- Fetch real emails
- Classify with LangChain
- Log metadata to Google Sheets

