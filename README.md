# EMBA Assistant

**From Noise to Strategy: A Multimodal AI "Chief of Staff" for Executive Education.**

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-App-ff4b4b)
![AI](https://img.shields.io/badge/AI-Gemini_Pro_%2B_Perplexity-orange)

## Why
Executive MBA programs require **synthesis**, not just transcription.
- **Audio recordings** (Zoom H1) capture the *nuance* of the debate.
- **Handwritten notes** (Wacom/Paper) capture my *interpretation* of the model.
- **Real-world application** requires validating academic theory against live market data.

Doing this manually for 8-hour lectures is inefficient.

## How
This is a local, privacy-first Python application that acts as a "Strategy Engine." It ingests raw classroom data and outputs a structured, market-validated strategic memo.

### The Architecture: "The Architect & The Auditor"
1.  **The Architect (Google Gemini 1.5 Pro):**
    * Ingests huge context (Audio + Images simultaneously).
    * "Listens" to the lecture while "reading" my handwritten diagrams.
    * Identifies gaps: *"The professor emphasized X, but you only wrote down Y."*
2.  **The Auditor (Perplexity Sonar Pro):**
    * Takes the theoretical summary from Gemini.
    * audits it against **live 2026 European market data**.
    * *Example Output:* "This strategy worked for US Payers, but here is why it failed in Germany last year."

## 🛠️ Features
-   **Universal Input:** Works with Audio+Notes, Audio-only, or Notes-only.
-   **Privacy First:** Runs locally on your machine. API keys are stored in a local `.toml` file, never exposed in code.
-   **Obsidian Integration:** Automatically saves formatted Markdown notes directly to your personal Knowledge Vault.
-   **Intel-Mac Friendly:** Heavy lifting is offloaded to the Cloud (Gemini/Perplexity APIs), so it runs fast even on older hardware.

---

## ⚙️ Installation & Setup

### 1. Prerequisites
-   **Python 3.10+** installed on your Mac/PC.
-   **Google AI Studio API Key** (Free Tier available).
-   **Perplexity Pro API Key** (Included with Pro subscription).

### 2. Clone & Prepare
```bash
# Clone this repository
git clone [https://github.com/benjaminFaguer/emba-strategy-engine.git](https://github.com/benjaminFaguer/emba_assistant.git)

# Navigate into the folder
cd emba_assistant

# Create a Virtual Environment (Recommended)
python3 -m venv venv
source venv/bin/activate

# Install Dependencies
pip install -r requirements.txt

```

### 3. Configure Secrets (Critical!)

This app uses a local secrets file to keep your API keys safe. **This file is git-ignored and will not be uploaded.**

1. Create a folder named `.streamlit` in the project root.
2. Inside it, create a file named `secrets.toml`.
3. Paste the following config:

```toml
# .streamlit/secrets.toml

[keys]
gemini_api_key = "PASTE_YOUR_GOOGLE_KEY_HERE"
perplexity_api_key = "PASTE_YOUR_PERPLEXITY_KEY_HERE"

[paths]
# Update these to match your local folders
vault_root = "/Users/yourname/Documents/ObsidianVault/EMBA"
archive_root = "/Users/yourname/Documents/EMBA_Archive"

```

---

## 🖥️ Usage

### Standard Launch

Open your terminal and run:

```bash
streamlit run emba_app.py

```

A browser window will open at `http://localhost:8501`.

### ⚡ Pro Tip: One-Click Mac App

You can create a clickable launcher to run this without opening the terminal.

1. Create a file named `Launch_EMBA.command` in the project folder.
2. Paste this script:
```bash
#!/bin/bash
cd "$(dirname "$0")"
source venv/bin/activate
streamlit run emba_app.py

```


3. Make it executable: `chmod +x Launch_EMBA.command`.
4. **Double-click to launch!**

---

## 📂 Project Structure

```
emba-strategy-engine/
├── emba_app.py             # Main application logic
├── requirements.txt        # Python dependencies
├── .gitignore              # Protects secrets & temp files
├── Launch_EMBA.command     # One-click launcher script
├── .streamlit/
│   └── secrets.toml        # [PRIVATE] Your API Keys
└── README.md               # Documentation

```

## 🛡️ Disclaimer

* **Data Privacy:** This tool sends data to Google and Perplexity APIs. Ensure you comply with your institution's recording policies and do not upload confidential patient data (HIPAA/GDPR) without anonymization.
* **Academic Integrity:** This is a **synthesis tool**, not a cheating tool. It is designed to help you process information you have legally acquired.

---

*Built by Benjamin Faguer for the EDHEC EMBA.*

