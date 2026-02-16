# Canteen Meal Budget Tracker

**Group Members:**  
- Lexyl Caye V. Polinar – 8 - Daffodil  
- Ethan Jhan Rosales – 8 - Daffodil  
- Jade Sumaylo – 8 - Daffodil


---

## Project About

The **Canteen Meal Budget Tracker for Dormers** is a simple web application designed to help dorm students manage their meal allowance. Many dormers receive a **weekly or monthly budget**, but sometimes they overspend without tracking their daily expenses.

This system allows dormers to **set a budget, record daily canteen expenses, and automatically calculate their remaining balance**. The main goal of the project is to **help students become more financially responsible while living in the dorm**.

The system is intentionally simple so that it is easy to understand and use.

---

# Purpose of the Project

The purpose of this project is to:

* Help dormers **monitor their daily meal spending**
* Prevent students from **overspending their allowance**
* Encourage **financial discipline and budgeting habits**
* Provide a **simple and accessible budgeting tool**


---

# How It Benefits Dormers

This system benefits dormers because:

* They can clearly see how much money they have left.
* They can control their spending before their allowance runs out.
* They become more aware of their daily expenses.
* It reduces financial stress during the week or month.


---

# What Was Updated

The following improvements were made to the project:

* The system was changed from a general canteen system to a **budget tracker specifically for dormers**.
* The features were simplified to focus only on budgeting.
* Complex features like online payments were removed.
* The code structure was organized more clearly.
* Ethical considerations were added in the documentation.
* Simpler Python code was used for better understanding.
* The README was improved with clearer explanations.

---

# Why These Updates Were Made

These updates were made to:

* Make the system more **focused and practical for dorm students**.
* Keep the project **simple and beginner-friendly**.
* Improve code readability.
* Make the documentation clearer and more professional.
* Ensure the project follows **ethical programming practices**.

---

# System Features

The system includes:

* **User registration and login**
* **Set weekly or monthly meal budget**
* **Add daily meal expenses**
* **Automatic balance calculation**
* **Simple dashboard display**


---

# Technologies Used

The project uses:

* **Python**
* **Flask (web framework)**
* **SQLite (database)**
* **HTML and CSS**

Flask was chosen because it is lightweight and simple for beginners. SQLite was selected because it is built into Python and does not require complex installation.

---

# Simple Python Code (Flask Version)

Below are simplified examples of the main system functions.

---

## 1. Set Budget

```python
from flask import Flask, request
import sqlite3

app = Flask(__name__)

@app.route("/set_budget", methods=["POST"])
def set_budget():
    budget = request.form["budget"]

    conn = sqlite3.connect("database.db")
    cursor = conn.cursor()
    cursor.execute("UPDATE users SET budget=?", (budget,))
    conn.commit()
    conn.close()

    return "Budget saved"
```

This saves the dormer’s budget in the database.

---

## 2. Add Expense

```python
@app.route("/add_expense", methods=["POST"])
def add_expense():
    amount = request.form["amount"]

    conn = sqlite3.connect("database.db")
    cursor = conn.cursor()
    cursor.execute("UPDATE users SET total_expense = total_expense + ?", (amount,))
    conn.commit()
    conn.close()

    return "Expense added"
```

This adds the new meal expense to the total expenses.

---

## 3. Check Remaining Balance

```python
@app.route("/balance")
def balance():
    conn = sqlite3.connect("database.db")
    cursor = conn.cursor()
    cursor.execute("SELECT budget, total_expense FROM users")
    data = cursor.fetchone()
    conn.close()

    remaining = data[0] - data[1]
    return str(remaining)
```

The formula used is:

**Remaining Balance = Budget − Total Expense**

---

# Detailed Methodology

The system works using Flask routes to process user requests. When a dormer sets a budget or adds an expense, the frontend sends the data to the Flask server. The server updates the SQLite database. When the dormer checks their balance, the system retrieves stored values and calculates the remaining amount.

The backend and frontend communicate using **HTTP POST and GET requests**.

The design is minimal and focused only on meal budgeting to ensure clarity and usability.


