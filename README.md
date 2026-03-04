# QueryForge — Natural Language to Bash + SQL Pipeline Generator

QueryForge is an experimental system that converts **natural language data tasks into executable hybrid pipelines (Bash + SQL)**.

The system analyzes database schemas and local filesystem metadata, generates a structured execution pipeline using a Large Language Model (LLM), executes the pipeline in a controlled sandbox environment, and automatically attempts to repair failures through an iterative correction loop.

This project was developed as part of a **university team research project focused on LLM-driven data pipeline automation**.

---

# Key Features

• **Natural Language → Data Pipeline**  
Transforms human language instructions into executable data pipelines.

• **Schema-Aware Pipeline Generation**  
The system analyzes relational database schemas before generating SQL queries.

• **Hybrid Execution Model**  
Generated pipelines can combine:
- SQL queries
- Bash commands
- file processing steps

• **Sandboxed Execution Environment**  
Each generated step is executed safely with controlled permissions.

• **Error Detection and Repair Loop**  
If a pipeline step fails, the system attempts automatic repair using the LLM.

• **Execution Logging & Traceability**  
All pipeline runs and repair attempts are logged for debugging and analysis.

---

# System Architecture

The QueryForge system operates in the following stages:

1. **User Input**
   - The user submits a natural language request describing a data task.

2. **Context Collection**
   - Database schema metadata
   - Filesystem structure

3. **Pipeline Generation**
   - The LLM generates a structured pipeline consisting of Bash and SQL steps.

4. **Pipeline Synthesis**
   - Each step is converted into executable `.sql` or `.sh` scripts.

5. **Sandbox Execution**
   - Steps are executed sequentially inside a controlled environment.

6. **Error Detection**
   - If a step fails, the system analyzes logs and identifies the issue.

7. **Repair Loop**
   - The LLM generates a corrected step and the pipeline is retried.

8. **Execution Logging**
   - Results and logs are stored for reproducibility and debugging.

    ! See architecture diagram in /docs/architecture.md !

---

# Technology Stack

Backend
- Python
- FastAPI

Database
- SQLite

AI / LLM
- Google Gemini API

Execution Layer
- Bash
- SQL

Other Components
- Schema introspection
- pipeline generation logic
- sandbox execution engine
- automated repair loop

---

# Project Structure
QUERYFORGE/
│
├── app/ # FastAPI application
├── core/ # pipeline generation and orchestration
├── sandbox/ # controlled execution environment
├── database/ # database models and logging
├── scripts/ # generated bash/sql steps
├── requirements.txt
└── PRD.md # product design document

---

# Installation

Clone the repository:
git clone https://github.com/CanSsever/QUERYFORGE.git

cd QUERYFORGE

Create a virtual environment:
python -m venv .venv

Activate the environment:

Windows PowerShell
.venv\Scripts\Activate.ps1

Install dependencies:
pip install -r requirements.txt

---

# Environment Configuration

Create a `.env` file and configure the required API keys.

Example:
GEMINI_API_KEY=your_api_key_here

---

# Running the API

Start the FastAPI server:
uvicorn app.main:app --reload

Open the API documentation:
http://127.0.0.1:8000/docs

---

# Example Workflow

Example user request:
"Find the top 10 customers by total purchase value and export the results as a CSV file."

QueryForge will:

1. Inspect the database schema
2. Generate a SQL query
3. Create a Bash step for exporting results
4. Execute the pipeline
5. Log results and potential repair attempts

---

# Research Context

This project explores the use of **Large Language Models for automated data engineering workflows**.

The goal is to move beyond simple **Text-to-SQL systems** and investigate how LLMs can:

- generate multi-step data pipelines
- interact with relational databases
- orchestrate hybrid execution environments
- repair runtime errors automatically

---

# Team Project

This repository is part of a **team-based university project**.

Contributions included:

- system design
- architecture planning
- integration of LLM components
- pipeline execution logic
- testing and experimentation

---

# License

This project is intended for research and educational purposes.

If you plan to reuse or extend the project, consider adding an open source license such as MIT.
