# 🤖 AI Database Query Assistant

Transform natural language questions into SQL queries and get instant results!

## Features
- 🗣️ Natural language to SQL conversion
- 🔗 Interactive database schema visualization
- 📊 Column type analysis and charts
- 📜 Query history tracking
- 🎨 Beautiful modern UI

## Local Development
1. Clone this repository
2. Install dependencies: `pip install -r requirements.txt`
3. Set up your database connection in Streamlit secrets
4. Run: `streamlit run main.py`

## Environment Variables
- `GROQ_API_KEY`: Your Groq API key for AI processing
- `MYSQL_HOST`: MySQL database host
- `MYSQL_USER`: MySQL username
- `MYSQL_PASS`: MySQL password
AI Database Query Assistant
The AI Database Query Assistant is an intelligent Streamlit-based application that converts natural language (plain English) questions into safe, optimized SQL queries, executes them against your MySQL databases, and visualizes the results interactively. It integrates both Groq Cloud API and local Ollama LLMs, offering users the flexibility of cloud speed or local privacy.

🚀 Overview
This project allows non-technical users to query databases simply by typing their questions in plain language.
Example:

“Show all customers who placed orders last month”

The system automatically translates this into a valid SQL SELECT query, validates it for safety, executes it on a selected MySQL database, and displays the results along with quick charts and schema insights.

⚙️ Key Features
Natural Language to SQL Conversion
Converts English queries into SQL using LLMs (Groq API or Ollama).
Ensures only safe SELECT statements and prevents destructive operations.

Dual AI Provider Support

Groq Cloud API: Fast, reliable, cloud-based inference.

Local Ollama Models: Private, offline execution using locally installed models.

Interactive Streamlit Interface

Intuitive sidebar for AI model and database selection.

Schema auto-loading with ongoing session memory.

Detailed result visualization with quick charting tools.

Enhanced Schema Visualization

Explore table structures and data types interactively.

Relationship graph powered by Plotly (auto-detects foreign key patterns).

Column type distribution analytics.

Query History Tracking
Stores and displays the 20 most recent queries with timestamps, providers used, and execution metrics.

Safety and Validation
Includes SQL validation checks to block modification queries (DROP, DELETE, UPDATE, INSERT, etc.).

Rich UI/UX Design
Custom CSS and hover animations for an engaging and responsive experience.

🧩 Project Architecture
Module	Description
config.py	Loads environment variables, API keys, and defines available AI models and databases.
llm_helpers.py	Contains logic for converting natural language queries into SQL using Groq or Ollama APIs.
sql_helpers.py	Handles MySQL connectivity, schema extraction, query execution, and SQL safety validation.
ui_components.py	Responsible for custom UI design, schema visualization, history tracking, and result rendering.
app.py	Main Streamlit entry point integrating all components into a cohesive app.
🔍 Core Functionality
1. Natural Language to SQL (llm_helpers.py)
nl_to_sql_groq():
Sends structured prompts to Groq API to convert natural language into SQL.

nl_to_sql_ollama():
Handles local inference through Ollama.

nl_to_sql():
Routes the query to the chosen provider and model.

2. Database Management (sql_helpers.py)
get_db_schema(): Loads table structure (columns and types).

run_sql_query(): Executes validated SQL and returns a pandas DataFrame with execution time.

validate_sql(): Prevents dangerous statements (only allows SELECT).

3. Streamlit Interface (app.py)
Dynamic Sidebar:
Select AI provider, model, and database interactively.

Main Query Box:
Input natural language questions and execute them instantly.

Schema and History Panels:
On-demand exploration of loaded database structure and previous queries.

Enhanced Displays:
Query results, statistics, visual analytics, and CSV download support.

4. User Interface Enhancements (ui_components.py)
Includes:

Gradient headers and animated buttons.

Interactive schema exploration.

Relationship graphs (using Plotly).

Type-based highlighting in schema tables.

Easy navigation between views (schema details, relationships, analysis).

🔑 Configuration
Environment Variables (.env)
You must create a .env file with the following entries:

text
GROQ_API_KEY=your_groq_api_key_here
MYSQL_HOST=localhost
MYSQL_USER=root
MYSQL_PASS=your_password
ALLOWED_DATABASES=employees,products,sales
APIs and Endpoints
Groq API Endpoint: https://api.groq.com/openai/v1/chat/completions

Ollama Local Endpoint: http://localhost:11434/api/chat

🧠 Supported Models
Groq Cloud Models

llama-3.3-70b-versatile

llama-3.1-70b-versatile

llama-3.1-8b-instant

mixtral-8x7b-32768

gemma2-9b-it

Ollama Local Models

llama3.2:3b

nomic-embed-text:latest

qwen3:4b

granite3.2-vision:latest

gemma2

💻 Installation & Setup
bash
# 1. Clone the repository
git clone https://github.com/yourusername/ai-db-assistant.git
cd ai-db-assistant

# 2. Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # on Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Create a .env file and set configurations
nano .env

# 5. Run the Streamlit app
streamlit run app.py
🧪 Usage Guide
Launch the Streamlit app.

Select your AI provider (Groq or Ollama) and desired model.

Choose from available databases in the dropdown (must be whitelisted in .env).

Type a plain English question in the input box.

View the generated SQL, its execution output, and dynamic charts.

Optionally view schema details or previous query history in the sidebar.

📊 Visualization Capabilities
Interactive schema relationship graph

Column type distribution charts (Pie + Bar)

Query results view with data download

Quick histogram or box plot visualizations for numeric results

🧰 Tech Stack
Core Language: Python 3.10+

Frontend Framework: Streamlit

Database: MySQL

Visualization: Plotly, Pandas

AI Providers: Groq API, Ollama Local Models

Environment Management: python-dotenv
