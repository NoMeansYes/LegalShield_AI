# ⚖️ LegalShield AI
### AI-powered Legal Document Red-Flagging for Indian Contracts

> Built for **CodeLite 2.0** — Project A3 | Legal Tech / NLP | Team: Syntax Syndicate

---

## 🎥 Demo Video
[![LegalShield AI Demo](https://img.shields.io/badge/Watch%20Demo-YouTube-red?style=for-the-badge&logo=youtube)](https://youtu.be/iT51WL8LzjI)

---

## 📌 Problem Statement
Most Indians sign rental agreements, employment contracts, and loan documents without understanding the legal implications. Professional legal review costs ₹5,000–₹20,000 per document — unaffordable for most people.

---

## 💡 Our Solution
LegalShield AI lets anyone upload a legal document and instantly get:
- ✅ Clause-by-clause risk scoring (1–10)
- ✅ Flagged risky or unfair clauses
- ✅ Cross-references to Indian laws (Contract Act 1872, Rent Control Act, IT Act)
- ✅ Plain-English explanations for non-lawyers
- ✅ Suggested redlined edits for dangerous clauses
- ✅ Executive summary with overall verdict and negotiation points

---

## 🏗️ System Architecture

```
User uploads document (PDF/TXT) via index.html
              ↓
     n8n Webhook receives file
              ↓
      Extract text from PDF
              ↓
   Split into individual clauses
              ↓
  Groq AI analyzes each clause
  (llama-3.3-70b-versatile)
              ↓
   Parse and aggregate results
              ↓
  Generate executive summary
       (Groq AI again)
              ↓
  Return full risk report to
     frontend for display
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|-----------|---------|
| **n8n** | Workflow automation engine — connects all the nodes |
| **Groq AI** | Legal intelligence — llama-3.3-70b-versatile model |
| **HTML / CSS / JS** | Frontend interface — no framework needed |
| **Netlify** | Frontend hosting |
| **ngrok** | Makes n8n webhook accessible from internet |

---

## 📁 Files in This Repo

| File | Description |
|------|-------------|
| `index.html` | Frontend — upload interface and results dashboard |
| `workflow.json` | n8n workflow — import this into your n8n to get all nodes |
| `test_contract.txt` | Sample contract with unfair clauses to test the system |
| `architecture.html` | Visual system architecture diagram |
| `README.md` | This file |

---

## ⚙️ How to Run This Project Locally

Follow these steps exactly in order.

---

### Step 1 — Install Node.js
Go to https://nodejs.org and download the LTS version. Install it normally.

Verify it worked — open terminal and type:
```
node -v
```
You should see something like `v20.11.0`

---

### Step 2 — Install and Start n8n
In terminal type:
```
npm install -g n8n
```
Wait 2-3 minutes. Then start n8n:
```
n8n start
```
Open your browser and go to: `http://localhost:5678`
Create an account (any email and password works for local use).

---

### Step 3 — Import the Workflow
1. In n8n, click the **menu icon** (top left hamburger icon)
2. Click **Workflows**
3. Click **Import** button (top right)
4. Select the `workflow.json` file from this repo
5. The entire workflow loads with all nodes already connected

---

### Step 4 — Get a Groq API Key (Free)
1. Go to https://console.groq.com
2. Sign up free
3. Click **API Keys** on left sidebar
4. Click **Create API Key**
5. Copy the key — it starts with `gsk_`

---

### Step 5 — Add Your Groq API Key to the Workflow
1. In n8n, click the **first HTTP Request node** (Groq clause analysis)
2. Click the credential field → **Edit**
3. Change the **Value** field to: `Bearer YOUR_GSK_KEY_HERE`
4. Click Save
5. Repeat the same for **HTTP Request1** (executive summary node)

---

### Step 6 — Activate the Workflow
In n8n, toggle the workflow from **Inactive** to **Active** using the toggle in the top right corner. Click Save.

---

### Step 7 — Make n8n Publicly Accessible (for demo)

**Option A — Using ngrok (Recommended)**

Download ngrok from https://ngrok.com/download and install it.

Sign up at ngrok.com and get your free auth token, then run:
```
ngrok config add-authtoken YOUR_NGROK_TOKEN
```

Then in a new terminal window run:
```
ngrok http 5678
```

You will see a URL like:
```
Forwarding: https://abc123.ngrok.io → localhost:5678
```
Copy this URL.

**Option B — n8n built-in tunnel**

Stop n8n and restart with:
```
n8n start --tunnel
```
The tunnel URL will appear in the terminal output.

---

### Step 8 — Update the Webhook URL in index.html
Open `index.html` in any text editor (Notepad, VS Code etc).

Find this line near the bottom:
```javascript
const WEBHOOK_URL = 'http://localhost:5678/webhook-test/upload-contract';
```

Replace it with your ngrok or tunnel URL:
```javascript
const WEBHOOK_URL = 'https://abc123.ngrok.io/webhook/upload-contract';
```

Save the file.

---

### Step 9 — Open the App
Double click `index.html` to open it in your browser.
Upload the included `test_contract.txt` file and click Analyze.
You should see the full risk report appear in about 30-60 seconds.

---

## 🧪 Testing with Sample Document

The repo includes `test_contract.txt` which contains several deliberately unfair clauses:
- Unilateral termination without notice
- Non-refundable security deposit
- ₹2000/day late payment penalty
- Landlord entry without informing tenant

These should score 7–9/10 and trigger multiple flags.

---

## ❓ Common Errors and Fixes

| Error | Fix |
|-------|-----|
| `Cannot connect to webhook` | Make sure n8n is running and workflow is Active |
| `CORS error` in browser | Restart n8n with `N8N_CORS_ALLOWED_ORIGINS=* n8n start` |
| Score always shows 0 or 5 | Check Groq API key is correct in both HTTP Request nodes |
| `401 Unauthorized` in n8n | API key wrong — check Bearer token has no extra spaces |
| PDF text not extracting | Use a text-based PDF or .txt file instead |
| Clauses not splitting | Make sure document has numbered sections like "1.", "2." |

---

## 👥 Team — Syntax Syndicate

| Name | 
|------|
| Kushal Thakare |
| Pranav Waghmare |

---

## 🏆 Hackathon Details
| Field | Details |
|-------|---------|
| **Event** | CodeLite 2.0 |
| **Team Name** | Syntax Syndicate |
| **Track** | Legal Tech / NLP |
| **Project ID** | A3 — AI Agent for Legal Document Red-Flagging |
| **Difficulty** | Medium-Hard |
