# Canteen Meal Budget Tracker

**Group Members:**
Lexyl Caye V. Polinar – 8 Daffodil

Ethan Jhan Rosales – 8 Daffodil

Jade Sumaylo – 8 Daffodil

---

## Project Overview

The **Canteen Meal Budget Tracker for Dormers and Students** is a simple Python-based program designed to help students, especially dormers and those managing their own allowance, track their daily meal expenses.

Many students receive a daily or weekly allowance, but they often overspend because they do not monitor their expenses properly. Small purchases such as snacks and meals accumulate quickly, leading to financial difficulties.

This system allows users to set a daily budget, record meal expenses, and automatically calculate their total spending and remaining balance. The main goal of the project is to help students develop better financial awareness and budgeting habits.

---

## Purpose of the Project

The purpose of this project is to:

* Help dormers and students monitor their daily meal expenses
* Prevent overspending of allowance
* Encourage financial discipline and awareness
* Provide a simple and easy-to-use budgeting tool

---

## How It Benefits Dormers and Students

This system benefits dormers and students in several ways:

* It helps them see how much money they have left
* It allows them to control their spending
* It increases awareness of daily expenses
* It reduces financial stress

---

## System Features

The system includes the following features:

* Set daily budget
* Add meal expenses (Breakfast, Lunch, Dinner, Snack)
* Automatic calculation of total expenses
* Display of remaining budget
* Weekly spending report
* Meal history tracking

---

## Technologies Used

The project uses the following technologies:

* Python – main programming language
* JSON – for data storage
* Datetime module – for recording meal time

Python was chosen because it is simple and suitable for beginners. JSON was used because it allows easy saving and loading of data without requiring a database.

---

## System Explanation

The system works using Python functions. Users interact with the program through a menu system.

* The user first sets a daily budget
* Then inputs meal expenses
* The system stores the data using a JSON file
* The program calculates total spending and remaining budget
* It displays a summary of expenses

---

## Sample Code Explanation

### 1. Add Meal

```python
def add_meal(data):
    name = input("Enter meal name: ")
    cost = float(input("Enter meal cost: "))

    meal = {"name": name, "cost": cost}
    data["meals"].append(meal)
```

This function records the meal and its cost.

---

### 2. Save Data

```python
def save_data(data):
    with open("budget_data.json", "w") as file:
        json.dump(data, file)
```

This saves the user’s data into a JSON file.

---

### 3. Calculate Summary

```python
total_spent = sum(meal["cost"] for meal in data["meals"])
remaining = data["daily_budget"] - total_spent
```

This calculates the total expenses and remaining budget.

---

## Methodology

The system follows a simple process:

1. The user sets a daily budget
2. The user inputs meal expenses
3. The system stores the data using JSON
4. The program calculates total spending
5. The system displays results

The program uses loops, conditions, and functions to process data efficiently.

---

## Conclusion

The Canteen Meal Budget Tracker is a simple but effective system that helps dormers and students manage their daily expenses.

It demonstrates how programming can solve real-life problems by improving financial awareness and helping users avoid overspending.

---

## References (APA Format)

Python Software Foundation. (2023). *Python documentation*. [https://docs.python.org/3/](https://docs.python.org/3/)

JSON. (2022). *Introducing JSON*. [https://www.json.org/json-en.html](https://www.json.org/json-en.html)

Investopedia. (2023). *Budgeting basics*. [https://www.investopedia.com](https://www.investopedia.com)

Organisation for Economic Co-operation and Development. (2020). *Financial literacy and student behavior*. [https://www.oecd.org](https://www.oecd.org)

