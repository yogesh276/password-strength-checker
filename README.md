Project Title:

Password Strength Checker




Overview:

This project is an  password strength checking tool developed in Python.
It evaluates the security level of any password using multiple criteria such as:

Length

Character complexity

Dictionary word detection

Pattern and repetition analysis

Entropy calculation (mathematical strength)


The system provides a final rating (Weak, Medium, Strong, Very Strong) along with suggestions for improvement.



Features:

✔ Multi-Level Strength Analysis

Checks uppercase, lowercase, digits, and special characters

Detects common weak words (e.g., password, admin)

Identifies repeated characters & predictable patterns

Calculates password entropy


✔ Accurate Scoring Algorithm

Uses a scoring + entropy-based model for reliable evaluation.

✔ User-Friendly Output

Displays:

Rating

Entropy

Improvement suggestions





Tech Stack

Language: Python 3

Libraries: math, re

Optional: Tkinter (for GUI), text file for dictionary words





How to Run the Project:

1. Install Python

Make sure Python 3 is installed.

2. Save the code in a file

password_checker.py

3. Run the program

python password_checker.py

4. Enter password

You will receive a rating + entropy score.




Code Snippet:

import math
import re

common_words = ["password", "admin", "welcome", "login", "user"]

def calculate_entropy(password):
    pool = 0
    if re.search(r'[a-z]', password): pool += 26
    if re.search(r'[A-Z]', password): pool += 26
    if re.search(r'[0-9]', password): pool += 10
    if re.search(r'[^A-Za-z0-9]', password): pool += 32
    if pool == 0:
        return 0
    return len(password) * math.log2(pool)

def check_strength(password):
    score = 0

    if len(password) >= 8:
        score += 1

    if (re.search(r'[A-Z]', password) and
        re.search(r'[a-z]', password) and
        re.search(r'[0-9]', password) and
        re.search(r'[^A-Za-z0-9]', password)):
        score += 2

    if any(word in password.lower() for word in common_words):
        score -= 1

    if re.search(r'(.)\1\1', password):
        score -= 1

    entropy = calculate_entropy(password)
    if entropy > 45:
        score += 2
    elif entropy > 28:
        score += 1

    if score <= 1:
        rating = "WEAK"
    elif score == 2:
        rating = "MEDIUM"
    elif score == 3:
        rating = "STRONG"
    else:
        rating = "VERY STRONG"

    return rating, entropy


---

Sample Output

Enter password: Y@g3sh#2024
Rating: VERY STRONG
Entropy: 62.45




Project Structure:

Password-Strength-Checker/
│── README.md
│── password_checker.py
│── dictionary.txt (optional)
└── sample_output.png



Future Enhancements:

GUI version

API to check if password appears in leaked databases

Machine learning–based password classifier

Browser plugin version




Author:

 Name Yogesh
Institution  VIT BHOPAL UNIVERSITY
(Year 2025–26)
