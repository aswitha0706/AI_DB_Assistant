**🤖 AI Database Query Assistant**
Transform natural language questions into safe, efficient SQL queries and get instant results on your MySQL databases using state-of-the-art large language models (LLMs). This application supports both Groq Cloud API and local Ollama models, providing the best mix of speed, flexibility, and privacy.

**Table of Contents**

Features

How It Works

Installation

Configuration

Usage Guide

Supported AI Models

Project Structure

FAQ

License

**Features**
Natural Language to SQL: Enter questions in English, and let AI produce safe, correct SQL queries.

Dual AI Providers: Choose Groq (cloud) or Ollama (local on your machine).

Interactive UI: Choose models, databases, and settings via a dynamic sidebar.

Schema Exploration: See schemas, relationships, and analytics with charts and graphs.

Query History: Last 20 NL/SQL queries with timings, models, and results.

Safety: Blocks dangerous SQL keywords (DROP, DELETE, etc.), only SELECT queries allowed.

Rich Visualizations: Results table, quick charting, download as CSV, schema network graphs, and pie/bar analysis.

**How It Works**
Select AI Provider and Model:
Choose between fast Groq cloud models or privacy-first Ollama local models.

Pick your Database:
Choose from whitelisted MySQL databases (as defined in .env).

Ask in English:
Example:

"List all products with price over 100"
The LLM produces a safe, optimized SQL query.

Review, Run, and Explore Results:

View generated SQL and execution info.

See results in table form.

Visualize columns, distributions, and schema relationships.

Download results as CSV.

Query History:
Revisit past questions, see timings and provider/model used.

**Installation**
bash
# 1. Clone the repository
git clone https://github.com/yourusername/ai-db-assistant.git
cd ai-db-assistant

# 2. Create a virtual environment
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Create a .env file and configure connection parameters
cp .env.example .env   # or nano .env

# 5. Start the app
streamlit run app.py
Configuration
Create a .env file in your project directory with the following keys:

text
GROQ_API_KEY=your_groq_key_here
MYSQL_HOST=localhost
MYSQL_USER=root
MYSQL_PASS=your_db_password
ALLOWED_DATABASES=employees,products,sales
GROQ_API_KEY: Your Groq API key (get from https://groq.com)

MYSQL_SETTINGS: Your MySQL connection parameters

ALLOWED_DATABASES: Comma-separated list of databases you want available

Ollama requires the models downloaded locally.
If you see model errors, use:

bash
ollama pull model-name
For details see: https://ollama.com

Usage Guide
Start the app (streamlit run app.py)

Select AI provider (“Groq” for cloud, “Ollama” for local)

Choose a model suited to your needs (speed, accuracy)

Select database to query

Ask questions in plain English

View, validate, and download results

Explore schema details, column analytics, relationships, and quick charts

Download your result table as CSV

See previous queries and responses

**Supported AI Models**
Groq Models:

llama-3.3-70b-versatile

llama-3.1-70b-versatile

llama-3.1-8b-instant

mixtral-8x7b-32768

gemma2-9b-it

Ollama Local Models:

llama3.2:3b

nomic-embed-text:latest

qwen3:4b

granite3.2-vision:latest

gemma2

**Project Structure**
File / Module	Purpose
app.py	Main Streamlit web app
config.py	Settings and environment configuration
llm_helpers.py	LLM interaction, NL-to-SQL logic
sql_helpers.py	MySQL connection, schema extraction, query execution, validation
ui_components.py	UI building blocks, schema, history, result visualization
.env	Secure secrets and DB settings, not in repo
