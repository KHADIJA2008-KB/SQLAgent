SQL Agent Security & Analytics Workshop


- An educational codebase walking you through the journey from simple SQL agents to enterprise-grade, secure analytics systems built with LangChain and OpenAI. Step by step, you’ll see how to evolve from unsafe prototypes to production-ready solutions.

🎯 Learning Goals

- This repository demonstrates how to design SQL agents with progressively stronger safeguards. You’ll begin with no restrictions (unsafe) and progress toward fully hardened, analytics-focused implementations. Each script extends the previous one, showcasing real security and reliability improvements.

📚 Curriculum Flow
- Foundational LLM → raw language model interaction, no tools

- Intro SQL Agent → basic database querying with LangChain’s utilities

- Insecure Agent → examples of unsafe patterns and risks

- Hardened Agent → applying robust guardrails and validations

- Analytics Agent → advanced, business-oriented data analysis

🔒 Security Techniques Explored
- Input validation & defense against SQL injection

- Whitelist enforcement (only SELECT allowed)

- Automatic limits to control dataset size

- Blocking multi-statement chains to reduce exploit risks

- Error handling with safe, user-friendly messages

- Schema-based rules to restrict table access

📊 Analytics Demonstrations
- Multi-table JOINs for richer business insights

- Revenue and profitability analysis

- Cohort & customer lifetime value calculations

- Time-series exploration for growth trends

- Product/category performance comparisons

- Iterative, conversational data exploration

🚀 Getting Started

Requirements

- Python 3.8+

- OpenAI API key

- Basic knowledge of SQL & Python

Setup
<pre> ``` # 1. Create and activate a virtual environment
python -m venv .venv && source .venv/bin/activate   # or .venv\Scripts\activate on Windows

# 2. Install dependencies
pip install -r requirements.txt

# 3. Setup environment variables
cp .env.example .env
# Edit .env and insert your API key: OPENAI_API_KEY=sk-...

# 4. Move into the SQLAgent folder
cd SQLAgent

# 5. (Optional) Re-initialize the database
python scripts/reset_db.py

# 6. Run the scripts sequentially
python scripts/01_simple_agent.py
python scripts/02_risky_delete_demo.py
python scripts/03_guardrailed_agent.py
python scripts/04_complex_queries.py
 ``` </pre>


📁 Project Layout
<pre> ``` Project Root/
├── requirements.txt           # Shared dependencies
├── .env.example               # Template env vars
├── .env                       # Local secrets (ignored by git)
├── .venv/                     # Virtual environment
└── SQLAgent/
    ├── sql_agent_class.db     # SQLite sample database
    ├── sql_agent_seed.sql     # Schema & seed data
    ├── README.md              # Main guide
    └── scripts/
        ├── reset_db.py
        ├── 00_simple_llm.py
        ├── 01_simple_agent.py
        ├── 02_risky_delete_demo.py
        ├── 03_guardrailed_agent.py
        └── 04_complex_queries.py
 ``` </pre>


 🔍 Script Highlights
- 01 – Simple Agent

-  Purpose: first steps with LangChain SQL agents

-  Security: none

-  Risks: can execute any SQL, destructive included

-  Use case: introductory demo

- 02 – Risky Agent Demo

-  Purpose: intentionally insecure for education

-  Features: executes arbitrary SQL, including deletes/drops

-  Lesson: illustrates why guardrails are critical

- 03 – Guardrailed Agent

-  Purpose: secure, production-style agent

- Features:
-  Regex-based query validation

-  Only allows SELECT statements

-  Auto-injects LIMIT

-  Rejects multi-queries

-  Structured error feedback

- Outcome: -
-  safe for analytics & BI

- 04 – Advanced Analytics

- Purpose: business intelligence queries

- Adds:

- Revenue tracking

- Customer segmentation

- Time-based trend analysis

- Comparative product analysis

- Security: inherits safeguards from script 03

🗄️ Database Overview

Tables:

-  customers – customer profiles

-  orders – order history
  
-  order_items – line-level details

-  products – product catalog

-  payments – payment records

-  refunds – refund tracking

-  Metrics supported:

-  Revenue = (quantity × unit price) – refunds

-  CLV = customer total spend – refunds

-  Product & category performance

-  Weekly/monthly trends

🛡️ Security Lessons

- Validate input – reject dangerous keywords & patterns

- Force read-only – never permit write operations

- Enforce limits – prevent resource abuse

- Handle errors gracefully – reveal nothing sensitive

- Adopt least privilege – analytics DB should be read-only

⚠️ Guidelines

  ✅ Safe for development & training

  ❌ Do not use risky agent patterns in real systems

  ✅ Use read-only DB credentials in production

  ✅ Add monitoring, logging, and regular audits

  🔧 Troubleshooting

- Missing packages → activate venv & run pip install -r requirements.txt

- No API key → edit .env and add OPENAI_API_KEY=...

- DB missing → run python scripts/reset_db.py

- Pydantic errors → check Python version (3.8+) and dependency compatibility

🤝 Contributing

-  Contributions that improve learning are welcome:

-  Better documentation/examples

-  More analytics queries

-  Additional security techniques

-  Enhanced error-handling patterns

📄 License

-  This project is for educational purposes. You’re free to reference these ideas in your own work with proper attribution.

🔥 Remember: the key takeaway is understanding the journey — from unsafe to secure SQL agents. Start small, learn the pitfalls, then build systems that are safe, scalable, and insightful.

