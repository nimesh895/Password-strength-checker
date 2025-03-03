# Password-strength-checker
# Password Strength Checker

A Python-based tool that evaluates the strength of passwords and estimates how long it would take to crack the password using brute-force methods. This project helps users assess their passwords’ security and provides feedback on how to improve them.

## Features:
- **Password Strength Evaluation**: Evaluates passwords based on criteria like length, use of lowercase letters, uppercase letters, digits, and special characters.
- **Brute-Force Crack Time Estimation**: Estimates the time it would take for a brute-force attack to crack the password, based on the characters used and the password length.

## How It Works:
1. The program checks the password against five strength criteria:
   - Minimum length of 8 characters.
   - Inclusion of lowercase and uppercase letters.
   - Inclusion of at least one digit.
   - Inclusion of at least one special character from a predefined list (`@$!%*?&`).
   
2. The password is then classified as:
   - **Weak**: If it meets fewer than 3 criteria.
   - **Moderate**: If it meets at least 3 criteria.
   - **Strong**: If it meets all 5 criteria.

3. The tool also estimates the time it would take to crack the password using brute-force methods. It calculates the number of possible combinations based on the characters used and the length of the password.

## Requirements:
- Python 3.x or higher

## How to Use:
1. Clone this repository:
   ```bash
   

