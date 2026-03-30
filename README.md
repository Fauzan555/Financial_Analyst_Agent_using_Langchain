# 📊 Financial Analyst Agent using LangChain & Groq

## 🚀 Overview

This project is an AI-powered **Financial Analyst Agent** that can analyze financial reports (PDFs) and generate intelligent insights using **LLMs**.

It combines:

* 📄 PDF processing (PyMuPDF)
* 🤖 LLM reasoning (Groq - LLaMA3)
* 🧠 Conversation memory
* 🛠 Tool-based agent architecture

The system simulates a real-world financial analyst that can **read reports and provide structured insights automatically**.

---

## ✨ Key Features

* 📄 Extracts text from financial PDFs
* 🤖 Uses LLaMA3 (via Groq) for analysis
* 🧠 Maintains conversation context using memory
* 🛠 Tool-based agent for modular reasoning
* 📊 Generates:

  * Revenue insights
  * Profitability analysis
  * Risk factors
  * Business outlook

---

## 🧱 Tech Stack

* **Python**
* **LangChain**
* **Groq (LLaMA3-70B)**
* **PyMuPDF (fitz)**
* **Jupyter Notebook**

---

## 📁 Project Structure

```bash
Financial-Analyst-Agent/
│
├── Financial_Analyst_Agent.ipynb   # Main implementation
├── Meta_Report2024.pdf             # Sample financial report
├── README.md                       # Documentation
├── requirements.txt                # Dependencies
└── .env                            # API key (not included)
```

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/financial-analyst-agent.git
cd financial-analyst-agent
```

---

### 2. Install dependencies

```bash
pip install langchain langchain-community langchain-groq pymupdf python-dotenv
```

---

### 3. Set API Key

Inside notebook or `.env`:

```python
import os
os.environ["GROQ_API_KEY"] = "your_api_key_here"
```

---

## ▶️ How It Works

### 🔹 Step 1: Extract Text from PDF

* Uses **PyMuPDF (`fitz`)**
* Reads all pages and converts into raw text

```python
doc = fitz.open(pdf_path)
text = "\n".join([page.get_text("text") for page in doc])
```

---

### 🔹 Step 2: LLM Initialization

* Uses Groq’s **LLaMA3-70B model**

```python
chat_model = ChatGroq(
    temperature=0,
    model_name="llama3-70b-8192"
)
```

---

### 🔹 Step 3: Memory Integration

* Stores chat history for context-aware responses

```python
memory = ConversationBufferMemory(
    memory_key="chat_history",
    return_messages=True
)
```

---

### 🔹 Step 4: Tool Creation

* Defines a tool to analyze financial reports

```python
def analyze_financial_report():
    prompt = f"""Analyze the financial report:
    {pdf_text[:4000]}
    """
```

---

### 🔹 Step 5: Agent Execution

* Uses LangChain agent to combine LLM + tools + memory

```python
agent = initialize_agent(
    tools=[pdf_tool],
    llm=chat_model,
    memory=memory,
    verbose=True
)
```

---

## 📊 Example Output

The agent successfully extracts and analyzes:

* 📈 **Revenue Growth:** +27% YoY
* 💰 **Net Income Growth:** +117%
* 📊 **Operating Margin:** Increased to 38%
* ⚠️ **Risks:** Rising costs, regulatory pressure
* 🚀 **Outlook:** Strong growth but heavy investments ahead

---

## ⚠️ Warnings & Notes

* LangChain shows deprecation warnings:

  * `ConversationBufferMemory` will be replaced
  * `initialize_agent` moving toward LangGraph

👉 These do NOT break the project but indicate future upgrades.

---

## 🚀 Future Improvements

* 🔍 Convert into full **RAG pipeline**
* 📊 Add stock market APIs (real-time data)
* 🌐 Deploy using Streamlit
* 🧠 Switch to LangGraph (latest agent framework)
* 📉 Add visualization dashboards

---

## 👨‍💻 Author

**Mohd Fauzan**
M.Tech Data Science (JNU)

---

## ⭐ Support

If you found this project useful:

* ⭐ Star the repo
* 🍴 Fork it
* 📢 Share it

---
