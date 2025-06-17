# LangChain Inbox Assistant 📬🤖

An AI-powered inbox assistant that automatically:
- Connects to your Gmail
- Reads unread emails
- Classifies them using a LangChain agent
- Logs metadata to a Google Sheet (including summary, type, and junk status)

Built using:
- 🔗 LangChain + OpenRouter (Mistral-7B)
- 📥 Gmail API
- 📊 Google Sheets API
- 🐍 Python (Jupyter)

---

## 🚀 What It Does

✅ Reads unread emails from your Gmail  
✅ Uses an LLM agent to classify the message content  
✅ Detects types like `refund_request`, `test`, or `junk`  
✅ Logs results to your connected Google Sheet

---

## 📦 Features

- **Gmail Integration**: OAuth 2.0-based secure connection
- **AI Classification**: LangChain-powered logic using OpenRouter
- **Logging**: Appends results to a live Google Sheet
- **Extendable**: Plug in auto-responses, dashboards, assignments, or auto-sorting

---

## 📸 Example Output

```bash
📬 Subject: Need refund
🧠 Classifying...
✅ Classified: {'summary': 'Request for refund or replacement.', 'type': 'refund_request', 'is_junk': False}

| Timestamp        | Input                    | Summary                           | Type            | Junk |
| ---------------- | ------------------------ | --------------------------------- | --------------- | ---- |
| 2025-06-17 13:12 | Hello I want a refund... | Request for refund or replacement | refund\_request | No   |



