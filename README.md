# QueryMind 🧠

QueryMind is an AI-powered Text-to-SQL application that allows users to interact with a MySQL database using natural language.

Instead of manually writing SQL queries, users can simply ask questions such as:

- What is the average salary of each department?
- Which department has the highest average salary?
- Show employees working on multiple projects.
- Which project has the highest budget?

The application uses **Google Gemini** to understand the user's question, generate SQL based on the database schema, validate the query, execute it on MySQL, and provide the results with an AI-generated explanation.

## 🚀 Features

- Natural language to SQL generation
- Google Gemini integration
- Automatic MySQL schema extraction
- SQL validation using SQLGlot
- Safe SELECT-only query execution
- Automatic SQL error detection and repair
- AI-generated explanations for query results
- Basic automatic data visualization
- Support for complex SQL queries, JOINs and aggregations

## 🏗️ How It Works

```text
User Question
      ↓
Database Schema Extraction
      ↓
Gemini generates SQL
      ↓
SQL Validation
      ↓
MySQL Execution
      ↓
 ┌───────────────┐
 │               │
Success         Error
 │               │
 ↓               ↓
Results      Gemini SQL Repair
 │               │
 └───────┬───────┘
         ↓
AI Explanation + Visualization
```

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Frontend | Streamlit |
| Backend | Python |
| AI | Google Gemini API |
| Database | MySQL 8 |
| Database Connectivity | SQLAlchemy, PyMySQL |
| SQL Processing | SQLGlot |
| Configuration | python-dotenv |

## 📁 Project Structure

```text
QueryMind/
│
├── app.py
├── evaluate_model.py
├── requirements.txt
├── README.md
├── .env.example
├── .gitignore
│
├── database/
│   ├── connection.py
│   └── __init__.py
│
└── services/
    ├── schema_service.py
    ├── llm_service.py
    ├── sql_service.py
    ├── query_service.py
    └── __init__.py
```

## ⚙️ Setup

### 1. Clone the Repository

```bash
git clone https://github.com/shivansh1609/QueryMind.git
cd QueryMind
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

For Windows:

```powershell
.\venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the project root:

```env
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=temp
GEMINI_API_KEY=your_gemini_api_key
```

> Never commit your `.env` file or API keys to GitHub.

## 🗄️ Database

QueryMind uses a MySQL database with relational tables such as:

- `departments`
- `employees`
- `projects`
- `employee_projects`
- `performance_reviews`
- `salaries`

The application automatically extracts the database schema and provides the relevant structure to the AI during SQL generation.

## ▶️ Run the Application

Start the Streamlit application:

```bash
streamlit run app.py
```

Then open the local URL provided by Streamlit.

Example:

```text
What is the average salary of each department?
```

QueryMind generates the SQL, executes it against the database, and displays the result along with an explanation and visualization when applicable.

## 🔒 Safety

QueryMind currently allows only `SELECT` queries through SQL validation.

Queries such as:

```text
INSERT
UPDATE
DELETE
DROP
ALTER
```

are rejected before execution.

For production use, additional database-level read-only permissions, query limits and authentication would be recommended.

## 🔮 Future Improvements

- Multi-turn conversational database queries
- PostgreSQL and SQLite support
- Query result caching
- Advanced visualizations
- Query performance analysis
- SQL optimization
- Better semantic validation
- User authentication
- Database connection management

## 👨‍💻 Author

**Shivanshu Pandey**

AI / Software Engineering

GitHub: https://github.com/shivansh1609

## 🔗 Repository

https://github.com/shivansh1609/QueryMind
