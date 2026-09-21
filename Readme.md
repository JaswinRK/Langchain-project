# Student Agent — LangChain + Gemini

A LangChain agent powered by Google Gemini that answers student-related
questions by **autonomously selecting and calling tools**. The LLM decides
which tool to use based on the user's question — no hardcoded sequence.

---

## Overview

Given a SQLite database of student marks, the agent can:

- Look up a student's **name and department**
- Retrieve a student's **subject marks** (Python, Database, AI, Web)
- **Calculate totals and averages**
- Check **university pass eligibility** against official rules

The agent chains multiple tools together when a question requires it.

---

## Tools

| Tool | Purpose |
|------|---------|
| `get_student_info(student_id)` | Returns the student's name and department |
| `get_student_marks(student_id)` | Returns marks in Python, Database, AI, Web |
| `calculator(expression)` | Evaluates math expressions for totals and averages |
| `get_passing_rules()` | Returns university rules: min average 40%, min 35% per subject |

Each tool is defined with LangChain's `@tool` decorator, with **type hints**
and **docstrings** that the LLM reads to decide when to use it.

---

## How It Works
