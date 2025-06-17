# 🧰 Setup

1. Clone this repo & open `Langchain_Inbox_with_Gmail.ipynb` in Jupyter
2. Place your credential files:
   - `client_secret2.json` (Gmail OAuth desktop app)
   - `your-sheets-service-account.json` (Google Sheets service account)
3. Install dependencies:
   ```bash
   pip install gspread oauth2client google-auth google-auth-oauthlib google-api-python-client langchain-openai

4. Run the notebook to authenticate Gmail and connect Sheets

5. View results live in the terminal and your sheet

## 🔐 Credentials Setup

You’ll need:
-A Desktop App OAuth 2.0 Client
-A Google Sheets Service Account
-A Google Sheet named LangChain shared with your service account email

## 📌 Future Upgrades
✉️ Auto-reply via Gmail
📊 Live dashboards with Looker Studio or Streamlit
🔁 Scheduled background agent (cron or cloud function)


## 🧑‍💻 Created By
Built by Akshay Damle
Updates: [https://x.com/home](https://x.com/codezxs)
For personal inbox automation and AI experiments.


## 📄 License
MIT License – do whatever you want, just don't spam people with it.
