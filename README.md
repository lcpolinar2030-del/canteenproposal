# Canteen Meal Budget Tracker

**Group Members:**  
- Lexyl Caye V. Polinar – 8 - Daffodil  
- Ethan Jhan Rosales – 8 - Daffodil  
- Jade Sumaylo – 8 - Daffodil

---

Project Description

The Canteen Meal Budget Tracker for Dormers is a simple web-based system designed to help dorm students manage their meal allowance. Many dormers receive a weekly or monthly budget, and sometimes they spend too much without tracking their expenses. This system helps students set a budget, record daily canteen expenses, and automatically calculate their remaining balance.

The main goal of this project is to promote responsible spending and financial awareness among dorm students. The system is intentionally designed to be simple, clear, and easy to use, focusing only on budgeting and expense tracking.

System Features

The system allows users to register and log in securely. After logging in, the dormer can:

Set a weekly or monthly meal budget

Record daily meal expenses

View total expenses

Check remaining balance automatically

See a simple financial summary on the dashboard

Advanced features such as online payments and complex analytics were removed to keep the system focused and easy for dormers to understand.

Technologies Used

The system uses:

Python for backend logic

Flask as the web framework

SQLite as the database

HTML and CSS for frontend design

Flask is used because it is lightweight and beginner-friendly, based on official Flask documentation. SQLite was selected because it is built into Python and does not require complex installation, making it suitable for student projects.

Sample Code Implementation (Python + Flask)

Below are examples of the main system functions.

1. Setting the Budget

This function saves the dormer’s budget in the database.

from flask import Flask, request, jsonify
import sqlite3

app = Flask(__name__)

@app.route('/set_budget', methods=['POST'])
def set_budget():
    data = request.json
    budget = data['budget']
    user_id = data['user_id']

    conn = sqlite3.connect('database.db')
    cursor = conn.cursor()
    cursor.execute("UPDATE users SET budget = ? WHERE id = ?", (budget, user_id))
    conn.commit()
    conn.close()

    return jsonify({"message": "Budget saved successfully"})

Important: The budget is linked to the specific user to ensure data privacy.

2. Adding an Expense

This function updates the total expenses of the dormer.

@app.route('/add_expense', methods=['POST'])
def add_expense():
    data = request.json
    amount = data['amount']
    user_id = data['user_id']

    conn = sqlite3.connect('database.db')
    cursor = conn.cursor()
    cursor.execute("UPDATE users SET total_expense = total_expense + ? WHERE id = ?", (amount, user_id))
    conn.commit()
    conn.close()

    return jsonify({"message": "Expense added successfully"})

Important: Each expense is automatically added to the total expense column in the database.

3. Calculating Remaining Balance

This function computes the remaining balance.

@app.route('/get_balance/<int:user_id>', methods=['GET'])
def get_balance(user_id):
    conn = sqlite3.connect('database.db')
    cursor = conn.cursor()
    cursor.execute("SELECT budget, total_expense FROM users WHERE id = ?", (user_id,))
    row = cursor.fetchone()
    conn.close()

    balance = row[0] - row[1]

    return jsonify({"remaining_balance": balance})

The formula used is:

Remaining Balance = Budget − Total Expenses

This calculation helps dormers see how much money they still have for meals.

Backend and Frontend Communication

The system uses HTTP requests to connect the frontend and backend.

POST request – used when setting a budget or adding expenses

GET request – used when retrieving the remaining balance

The backend processes the request and sends data in JSON format. This is based on standard Flask routing and REST API principles.

Key Design Decisions

The system was designed to be:

Simple and minimal

Focused only on meal budgeting

Easy to navigate

Lightweight and efficient

SQLite was chosen because it is suitable for small systems. Python and Flask were chosen because they are beginner-friendly and widely used in web development.

The design is made specifically for dorm students who need quick and simple money tracking.
