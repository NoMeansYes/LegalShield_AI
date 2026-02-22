# ⚖️ LegalShield AI
### AI-powered Legal Document Red-Flagging for Indian Contracts

> Built for Hackathon Project A3 — Legal Tech / NLP

---

## 🚀 Live Demo
🌐 [legalshield.xyz](https://legalshield.xyz)

---

## 📌 Problem Statement
Most Indians sign rental agreements, employment contracts, and loan 
documents without understanding the legal implications. Professional 
legal review costs ₹5,000–₹20,000 per document — unaffordable for 
most people.

---

## 💡 Our Solution
LegalShield AI lets anyone upload a legal document and instantly get:
- ✅ Clause-by-clause risk scoring (1–10)
- ✅ Flagged risky or unfair clauses
- ✅ Cross-references to Indian laws (Contract Act, Rent Control Act, IT Act)
- ✅ Plain-English explanations for non-lawyers
- ✅ Suggested redlined edits
- ✅ Executive summary with overall verdict

---

## 🏗️ System Architecture
```
User uploads document (PDF/TXT)
        ↓
n8n Webhook receives file
        ↓
Extract text from PDF
        ↓
Split into individual clauses
        ↓
Groq AI analyzes each clause (llama-3.3-70b-versatile)
        ↓
Parse and aggregate all results
        ↓
Generate executive summary (Groq AI)
        ↓
Return full risk report to frontend
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|-----------|---------|
| **n8n** | Workflow automation engine |
| **Groq AI** | Legal clause analysis (llama-3.3-70b) |
| **HTML/CSS/JS** | Frontend interface |
| **Netlify** | Frontend hosting |
| **ngrok** | n8n webhook tunnel |

---

## ⚙️ How to Run Locally

### Prerequisites
- Node.js installed
- Groq API key from console.groq.com (free)

### Steps

**1. Install and start n8n**
```bash
npm install -g n8n
n8n start
```

**2. Import the workflow**
- Open http://localhost:5678
- Click Import → select `workflow.json`
- Add your Groq API key in the HTTP Request nodes
- Toggle workflow to Active

**3. Start the tunnel**
```bash
ngrok http 5678
```
Copy the ngrok URL shown in terminal

**4. Update frontend**

Open `index.html` and change:
```javascript
const WEBHOOK_URL = 'https://YOUR-NGROK-URL/webhook/upload-contract';
```

**5. Open the app**

Double click `index.html` in your browser — done!

---

## 📄 Test It

Upload the included `test_contract.txt` file to see the system in action.
It contains several deliberately unfair clauses that should score 7–9/10.

---

## 🔑 Key Features

- **Agentic Loop** — AI iterates through every clause until all are analyzed
- **Indian Law Context** — Trained on IPC, Rent Control Act, IT Act, Contract Act 1872
- **Plain English** — Explains legal jargon in simple language
- **Redlined Edits** — Suggests fairer rewrites for dangerous clauses
- **Risk Scoring** — Color-coded 1–10 score for each clause

---

## 👥 Team Syntax Syndicate
- Kushal Thakare
- Pranav Waghmare

---

## 📸 Screenshots

<img width="1916" height="881" alt="image" src="https://github.com/user-attachments/assets/bd256f20-35fd-4a5e-8d79-1bd8fbb69c60" />
<img width="1206" height="840" alt="image" src="https://github.com/user-attachments/assets/170fc08a-fd32-49a5-ba32-6db48541093b" />
<img width="1449" height="862" alt="image" src="https://github.com/user-attachments/assets/e60a8ffe-68a4-4597-a356-84014f4a9cbb" />




---

## 🏆 Hackathon
**Event:** Codelite 2.0
**Track:** Legal Tech / NLP  
**Project:** A3 — AI Agent for Legal Document Red-Flagging
