# Student Assistant

An AI-powered Student Assistant built using **Python, SQLite, LangChain, Google Gemini, and Gradio**.

The application allows users to ask questions about students, their marks, total marks, average marks, and pass eligibility. The LangChain agent automatically selects the appropriate tool to answer each question.

## Features

- Get student name and department using student ID
- Get subject-wise marks
- Calculate total marks
- Calculate average marks
- Check pass eligibility based on university rules
- AI-powered tool selection using LangChain
- SQLite database for storing student information
- Interactive Gradio chatbot interface

## Technologies Used

- **Python**
- **SQLite**
- **LangChain**
- **Google Gemini**
- **Gradio**

## Project Structure

```text
Student-Assistant/
│
├── main.py
├── students.db
├── README.md
└── .env
```

## How It Works

The application uses four tools:

### 1. `get_student_info`

Retrieves the student's:

- Name
- Department

Example:

```text
What is the name and department of student 22CS045?
```

### 2. `get_student_marks`

Retrieves the student's marks in:

- Python
- Database
- AI
- Web

Example:

```text
What are the marks of 22CS047?
```

### 3. `calculator`

Calculates mathematical expressions such as:

```text
85+72+90+78
```

or

```text
(85+72+90+78)/4
```

It is used by the agent to calculate total and average marks.

### 4. `get_passing_rules`

Returns the university passing requirements:

- Minimum overall average: **40%**
- Minimum mark in each subject: **35%**

The agent uses these rules when checking a student's eligibility.

## Database

The SQLite database contains the following student details:

| Student ID | Name | Department | Python | Database | AI | Web |
|---|---|---|---:|---:|---:|---:|
| 22CS045 | Dhanushya | Computer Science | 85 | 72 | 90 | 78 |
| 22CS046 | Rahul | Computer Science | 65 | 70 | 68 | 72 |
| 22CS047 | Priya | Information Technology | 92 | 88 | 95 | 90 |
| 22CS048 | Arun | Information Technology | 55 | 60 | 58 | 62 |
| 22CS049 | Meena | Computer Science | 78 | 85 | 80 | 88 |

## Installation

Install the required packages:

```bash
pip install langchain langchain-core langchain-google-genai gradio
```

If you are using Google Colab:

```python
%pip install -qU langchain langchain-core langchain-google-genai gradio
```

## API Key Setup

The application requires a Google Gemini API key.

For Google Colab, store the API key in **Colab Secrets** with the name:

```text
GOOGLE_API_KEY
```

Then access it using:

```python
from google.colab import userdata
os.environ["GOOGLE_API_KEY"]=userdata.get("GOOGLE_API_KEY")
```

Do **not** upload your API key to GitHub.

## Running the Project

Run the Python program:

```bash
python main.py
```

The program first tests the predefined questions and then launches the Gradio chatbot.

The chatbot can answer questions such as:

```text
What is the name and department of student 22CS045?
```

```text
What are the marks of 22CS047?
```

```text
What is the total and average mark of 22CS045?
```

```text
Is 22CS045 eligible to pass according to the university rules?
```

```text
I am 22CS045. Tell me my name, department, total marks,
average marks, and whether I satisfy the university passing requirements.
```

## Agent Workflow

```text
User Question
      ↓
LangChain Agent
      ↓
Understand the Question
      ↓
Select Required Tool
      ↓
SQLite Database / Calculator / Passing Rules
      ↓
Tool Result
      ↓
Gemini Generates Final Answer
      ↓
Gradio Chatbot
```

For example, for a pass eligibility question:

```text
User
 ↓
Get Student Marks
 ↓
Calculate Average
 ↓
Get Passing Rules
 ↓
Compare Marks With Rules
 ↓
Final Answer
```

## Important Note

The current program uses:

```python
DROP TABLE IF EXISTS students
```

Therefore, the `students` table is recreated every time the program starts.

This is useful for a demonstration project, but it should be removed in a production application where database data must be preserved.

## Future Improvements

- Add more students dynamically
- Add student registration
- Add authentication
- Store conversation history
- Add attendance information
- Add subject-wise performance analysis
- Add faculty/admin tools
- Use a safer mathematical expression evaluator
- Deploy the chatbot as a web application
- Connect the application to MySQL or PostgreSQL

## Author

**Jaswin Rajkumar A**

B.Tech Information Technology  
St. Joseph's College of Engineering
