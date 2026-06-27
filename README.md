# -freelance-lead-generator-n8n
Automated AI job lead finder using n8n, RSS feeds &amp; AI scoring
What It Does

This n8n workflow automatically:


🔍 Scrapes job leads from LinkedIn, Fiverr, and RemoteOK via RSS/Google Alerts
🔗 Merges all sources into a single pipeline
🧠 AI scores each lead based on relevance, budget, and skill match
✅ Filters high-quality leads (score > 2 only)
📧 Sends a daily email digest via Gmail with the best opportunities
📊 Logs everything to Google Sheets for tracking


No more manually scrolling job boards. Let AI do the hunting. 🎯


🗺️ Workflow Overview

Schedule Trigger
    ├── LinkedIn Google Alert RSS
    ├── RemoteOK RSS
    └── Fiverr Google Alert RSS
            ↓
         Merge
            ↓
    Get rows in sheet (deduplicate)
            ↓
    Code in JavaScript (clean & format)
            ↓
    AI Score & Filter (Claude/OpenAI)
            ↓
    IF Score > 2
       ├── TRUE → Aggregate Leads
       │              ↓
       │       Gmail — Send Lead Digest
       │              ↓
       │       Append row in sheet
       └── FALSE → Skip


🧰 Tech Stack

ToolPurposen8nWorkflow automation engineRSS Feed nodesPull job listings from multiple sourcesGoogle SheetsStore and deduplicate leadsAI Node (Claude/OpenAI)Score and filter leads intelligentlyGmailSend daily digest emailJavaScriptCustom data cleaning & formatting


⚙️ Setup Instructions

1. Prerequisites


n8n instance (cloud or self-hosted)
Google account (Sheets + Gmail)
OpenAI or Anthropic API key
Google Alerts set up for keywords like "AI developer freelance", "n8n automation", etc.


2. Import the Workflow


Download Freelance Lead Generator - AI Jobs.json
Open your n8n instance
Go to Workflows → Import from file
Upload the JSON file


3. Configure Credentials

Connect the following in n8n:


Google Sheets OAuth2 — for reading/writing leads
Gmail OAuth2 — for sending digest emails
OpenAI / Anthropic API — for AI scoring


4. Set Up Google Sheets

Create a Google Sheet with these columns:

titleurlsourcescoredate

Copy your Sheet ID from the URL:

https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID_HERE/edit

Paste it in the Get rows in sheet and Append row in sheet nodes.

5. Set Up Google Alerts RSS


Go to google.com/alerts
Create alerts for keywords like:

AI developer Fiverr
n8n automation freelance
LangChain developer remote



Set delivery to RSS Feed
Copy the RSS URL into the LinkedIn/Fiverr Google Alert RSS nodes


6. Schedule It

The workflow runs on a Schedule Trigger — set it to run daily (e.g., every morning at 8 AM).


📬 Sample Email Output

🎯 Today's Top AI Freelance Leads — June 27, 2026

1. [RemoteOK] AI Chatbot Developer — $500-$1000
   Score: 4/5 | Link: remoteok.com/...

2. [LinkedIn] n8n Automation Expert Needed — $200
   Score: 3/5 | Link: linkedin.com/...

3. [Fiverr] RAG Pipeline Builder — $300
   Score: 3/5 | Link: fiverr.com/...

Total leads found: 28 | High quality: 3


🔧 Customization

What to changeWhereJob keywordsGoogle Alerts RSS URLsScoring criteriaAI Score & Filter node promptScore thresholdIF Score > 2 node (change the 2)Email formatGmail node templateRun frequencySchedule Trigger node


👩‍💻 Built By

Fatima Asim — AI & Automation Developer


🌐 GitHub
📧 fa437918@gmail.com
💼 Open to freelance AI/automation projects



📄 License

MIT — free to use, modify, and share. A ⭐ is appreciated if this helped you!



"Stop hunting for jobs. Build something that hunts for you." 🚀
