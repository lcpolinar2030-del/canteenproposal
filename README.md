# Canteen Meal Budget Tracker

**Group Members:**  
- Lexyl Caye V. Polinar – 8 - Daffodil  
- Ethan Jhan Rosales – 8 - Daffodil  
- Jade Sumaylo – 8 - Daffodil

---

# Canteen Meal Budget Tracker for Dormers

## Project About

The **Canteen Meal Budget Tracker for Dormers** is a simple web system that helps dorm students manage their meal allowance. Many dormers receive a **weekly or monthly budget**, but sometimes they overspend without realizing it.

This project allows dormers to **set a budget, record daily canteen expenses, and automatically see their remaining balance**. The main purpose of the system is to **help students become more responsible with their money while living in the dorm**.

The system is designed to be **simple, clear, and easy to use**. Only important budgeting features are included to avoid confusion.

---

# Updated Features

The system includes:

* **User registration and login**
* **Set weekly or monthly meal budget**
* **Add daily meal expenses**
* **Automatic balance calculation**
* **Simple dashboard summary**

Advanced features like online payment and complex charts were removed to keep the system **focused and beginner-friendly**.

---

# File Structure

```
/canteen-budget-tracker
│── app.py
│── database.db
│── /templates
│     ├── login.html
│     ├── dashboard.html
│── /static
│     ├── style.css
│── README.md
```

The system uses:

* **Python**
* **Flask**
* **SQLite**

Flask is used because it is simple and lightweight based on official Flask documentation.

---

# Simple Python Code (Flask Version)

Below is a **very simple version** of the main features.

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

This saves the dormer’s budget.

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

This adds the expense to the total spending.

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

The system works using **Flask routes** to handle user requests. When a dormer sets a budget or adds an expense, the frontend sends data to the Flask server. The server updates the SQLite database. When checking the balance, the server retrieves stored data and calculates the remaining amount.

The backend and frontend communicate using **HTTP POST and GET requests**. Data is stored in a simple SQLite database for easy management.

The system focuses only on **meal budgeting for dormers**, avoiding unnecessary features. This keeps the application lightweight and easier to maintain.

---

# Annotated GitHub Repository

The repository is organized clearly into:

* Python backend file (`app.py`)
* Database file
* Templates folder for HTML files
* Static folder for CSS
* README documentation

## Commit Messages

Commit messages are descriptive, such as:

* Added budget feature
* Implemented expense tracking
* Fixed balance calculation
* Updated README documentation

## Branch Usage

* `main` – stable version
* `feature-budget` – budget function
* `feature-expense` – expense function

