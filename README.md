# Developer Tools Research Agent

A command-line AI agent that helps developers research, compare, and analyze developer tools and technologies. It leverages LLMs and web scraping to extract actionable insights, pricing, tech stack, and recommendations for developer-focused products.

---

## Features

- **Natural Language Query:** Ask about any developer tool, technology, or category.
- **Automated Web Research:** Uses Firecrawl to search and scrape relevant articles and official sites.
- **LLM-Powered Analysis:** Extracts structured data (pricing, open source status, tech stack, APIs, integrations, etc.) using Google Gemini.
- **Actionable Recommendations:** Provides concise, developer-focused recommendations.
- **Extensible Workflow:** Modular design for easy extension and customization.

---

## How It Works

1. **User Query:** Enter a query (e.g., "best database for Python apps").
2. **Article Search & Scraping:** The agent searches for relevant articles and scrapes their content.
3. **Tool Extraction:** LLM extracts a list of relevant tools/services from the content.
4. **Company Research:** For each tool, the agent finds the official site, scrapes it, and analyzes developer-relevant features.
5. **Recommendation:** LLM generates a concise recommendation based on the findings.
6. **Results Display:** Structured results and recommendations are printed in the terminal.

---

## Installation

1. **Clone the repository:**
   ```bash
   git clone <repo-url>
   cd AdvancedAgent
   ```

2. **Set up a virtual environment (optional but recommended):**
   ```bash
   python -m venv env
   source env/Scripts/activate  # On Windows
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set environment variables:**
   - Create a `.env` file in the root directory with:
     ```
     FIRECRAWL_API_KEY=your_firecrawl_api_key
     GOOGLE_API_KEY=your_google_api_key
     ```

---

## Usage

Run the agent from the command line:

```bash
python main.py
```

You’ll see:
```
Developer Tools Research Agent

🔍 Developer Tools Query:
```
Type your query (e.g., `best CI/CD tools for startups`) and press Enter.

- Type `quit` or `exit` to stop.

---

## Example Output

```
Developer Tools Research Agent

🔍 Developer Tools Query: MongoDB Alternatives
 Finding articles about: MongoDB Alternatives
Extracted tools: Amazon Web Services (AWS), Oracle, Microsoft, MariaDB, Couchbase
🔬 Researching specific tools: Amazon Web Services (AWS), Oracle, Microsoft, MariaDB
Searching for: Amazon Web Services (AWS)
Searching for: Oracle
Searching for: Microsoft
Searching for: MariaDB
Error scraping company page: Failed to parse Firecrawl error response as JSON. Status code: 502
🪄 Generating recommendations

📊 Results for: MongoDB Alternatives
============================================================

1. 🏢 Amazon Web Services (AWS)
   🌐 Website: https://aws.amazon.com/pricing/
   💰 Pricing: Paid
   📖 Open Source: False
   🛠️  Tech Stack: Python, Java, JavaScript, Go, C++
   💻 Language Support: Python, Java, JavaScript, Go, C++
   🔌 API: ✅ Available
   🔗 Integrations: GitHub, Docker, Jenkins, Terraform
   📝 Description: AWS provides a wide range of cloud computing services and tools for developers, including compute, storage, databases, networking, analytics, and machine learning.


2. 🏢 Oracle
   🌐 Website: https://www.oracle.com/cloud/pricing/
   💰 Pricing: Paid
   📖 Open Source: False
   🛠️  Tech Stack: Java, SQL, Oracle Database
   🔌 API: ✅ Available
   📝 Description: Oracle Cloud Infrastructure (OCI) provides cloud computing services for developers, including compute, storage, and networking.


3. 🏢 Microsoft
   🌐 Website: https://www.microsoft.com/en-us/microsoft-365/business/microsoft-365-plans-and-pricing   
   💰 Pricing: Paid
   📖 Open Source: False
   🛠️  Tech Stack: Microsoft 365
   🔌 API: ✅ Available
   🔗 Integrations: Teams, Copilot
   📝 Description: Microsoft 365 provides a suite of productivity tools and services for businesses, including collaboration features and cloud storage.


4. 🏢 MariaDB
   🌐 Website: https://mariadb.com/pricing/
   💰 Pricing: None
   📖 Open Source: None

Developer Recommendations:
----------------------------------------
For a MongoDB alternative, AWS is the best option due to its comprehensive services and robust scalability.  Pricing is usage-based, so costs depend on your specific needs.  The main technical advantage is its extensive integration capabilities and mature ecosystem.
```

---

## Project Structure

```
main.py                  # CLI entry point
src/
  firecrawl.py           # Firecrawl web search & scraping service
  models.py              # Pydantic models for structured data
  prompts.py             # LLM prompt templates
  workflow.py            # Main workflow logic (search, extract, analyze, recommend)
  __init__.py
```

---

## Configuration

- **API Keys:** Required for Firecrawl and Google Gemini (set in `.env`).
- **LLM Model:** Uses `gemini-1.5-flash` by default (see `workflow.py`).

---

## Extending

- **Add new analysis fields:** Edit `models.py` and update prompt templates in `prompts.py`.
- **Change LLM or scraping logic:** Modify `workflow.py` and `firecrawl.py`.
- **Add new data sources:** Extend `FireCrawlService` or add new service modules.

---

## Dependencies

- firecrawl
- langchain
- langgraph
- langchain_google_genai
- pydantic
- python-dotenv

---
