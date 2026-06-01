# Learning Roadmap

## Overview

This roadmap covers 16 weeks of Python learning through practical,
portfolio-ready projects aligned with a Python Developer /
Data Operations Analyst role in Consumer & Community Banking.

All datasets used across all projects are entirely synthetic.
No real customer data, real bank data, or proprietary information
is used anywhere in this portfolio.

---

## Goal

Learn Python systematically by building real apps and projects across:

- Automation workflows
- Web applications
- APIs
- Data science tools
- Web scraping programs
- Desktop GUI apps
- AI automation and LangChain agents

Each project builds a GitHub portfolio relevant to Python development,
data operations, loan operations, banking-style workflows, ETL,
SQL reconciliation, data validation, reporting automation, exception
management, Agile delivery, testing, documentation, and operational
controls.

---

## Target role context

Work I am preparing for:

- Loan data ingestion, validation, reconciliation, and exception management
- Python automation for data checks, transformations, and reporting outputs
- ETL-style workflows using Python and pandas
- SQL-based data extraction, comparison, and anomaly investigation
- Data quality controls for completeness, accuracy, and timeliness
- Evidence capture, audit-ready documentation, and operational controls
- Git, version control, testing, code review, and documentation
- Batch process orchestration, monitoring, alerts, and failure handling
- UAT, parallel runs, migration support, and operational sign-offs
- Clear communication with technical and non-technical stakeholders
- Prioritization, SLAs, escalation, and timely delivery
- Troubleshooting and root-cause analysis
- Secure handling of credentials, environment variables, and config files

---

## 16-Week roadmap

| Week | Project | Sprint goal | Python topic | Data ops concept |
|------|---------|-------------|--------------|-----------------|
| 1–2  | P0: Python & Git Foundations | Set up environment, file I/O, logging, pytest, Git | pathlib, logging, pytest, venv, csv | File handling, audit logging, project structure |
| 3–4  | P1: Loan File Validator | Validate synthetic loan CSV files and generate exception reports | pandas, openpyxl, data validation | Data completeness, exception management, reporting |
| 5–6  | P2: SQL Reconciliation Tool | Build source-vs-target reconciliation and break report | SQLite, SQLAlchemy, SQL joins | Reconciliation, break quantification, exception summary |
| 7–8  | P3: FastAPI Validation Service | Build a loan validation REST API with pydantic | FastAPI, pydantic, httpx, pytest | Validation service, structured errors, API contracts |
| 9–10 | P4: Streamlit Ops Dashboard | Build an operational metrics dashboard with SLA indicators | Streamlit, pandas, altair | SLA monitoring, operational controls, stakeholder reporting |
| 11   | P5: Data Quality Analyzer | Detect anomalies and score data quality across the portfolio | numpy, matplotlib, seaborn | Anomaly detection, data quality controls, timeliness |
| 12   | P6: Public Rates Scraper | Ethically scrape public interest rate reference data | requests, BeautifulSoup | Ethical data sourcing, reference data, structured output |
| 12   | P7: Desktop CSV Validator | Build a desktop GUI for non-technical validation users | customtkinter, tkinter | Desktop tooling, operational usability |
| 13–14 | P8: LangChain Exception Agent | Build an AI agent to summarize and route exceptions | LangChain, LangGraph, pydantic | AI-assisted triage, exception routing, summarization |
| 15–16 | Capstone: Loan Data Ops Platform | Integrate all components into one portfolio platform | All of the above + GitHub Actions | End-to-end delivery, UAT, sign-off, audit trail |

---

## Project sequence

```
P0: Foundations
    └── P1: Automation (pandas, validation)
            └── P2: SQL (reconciliation, breaks)
                    └── P3: API (FastAPI, pydantic)
                            └── P4: Web App (Streamlit, dashboard)
                                    └── P5: Data Science (anomaly detection)
                                    └── P6: Web Scraping (ethical, public data)
                                    └── P7: Desktop GUI (customtkinter)
                                            └── P8: AI Agent (LangChain)
                                                    └── Capstone (full platform)
```

Each project builds on the skills from the previous one.
Do not skip projects. The sequence is intentional.

---

## Weekly learning routine

| Day | Activity |
|-----|----------|
| Monday | Sprint planning — review backlog, set sprint goal, create Issues, create branch |
| Tuesday–Thursday | Coding sessions — implement features, run tests, update docs |
| Friday | Git day — commit, push, open pull request, review against acceptance criteria |
| Saturday | Sprint review — test outputs, write review notes, update README |
| Sunday | Retrospective — what went well, what to improve, plan next sprint |

---

## Skills I will demonstrate by Week 16

### Python fundamentals
- Variables, data types, functions, type hints, docstrings
- File I/O with pathlib
- Error handling with try/except
- Logging module — console and file output
- Virtual environments and requirements.txt

### Data operations
- pandas for CSV ingestion, filtering, aggregation, and export
- openpyxl for Excel report generation
- Data validation: null checks, duplicate detection, date and numeric validation
- Exception report generation
- Source-vs-target SQL reconciliation and break quantification
- Anomaly detection using IQR method
- Data quality scoring and trend analysis

### APIs and web
- FastAPI endpoints with pydantic validation models
- REST request/response patterns and HTTP status codes
- Streamlit dashboard with charts, filters, and file downloads
- Ethical web scraping with requests and BeautifulSoup

### Desktop and AI
- Desktop GUI with customtkinter
- LangChain chains and prompt templates
- LangGraph routing logic
- Structured LLM output with pydantic

### Engineering practices
- pytest with fixtures and edge case coverage
- Logging and audit trails
- Secure credential handling with python-dotenv
- Git branching, commits, pull requests
- GitHub Issues and Project board (Kanban)
- Agile sprint delivery
- README and technical documentation
- GitHub Actions CI (capstone)

---

## Data and security rules

These rules apply to every project in this portfolio without exception:

1. Use only synthetic datasets
2. Never use real customer data or real bank data
3. Never hardcode passwords, API keys, tokens, or credentials
4. Never commit .env files
5. Always add .env to .gitignore before the first commit
6. Never scrape websites that prohibit scraping
7. Respect robots.txt and rate limits for all scraping projects
8. Always include a synthetic data disclaimer in every README
