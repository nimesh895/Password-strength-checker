import re
import time

def check_password_strength(password):
    strength_score = 0
    
    # Criteria
    length_criteria = len(password) >= 8
    lowercase_criteria = bool(re.search(r"[a-z]", password))
    uppercase_criteria = bool(re.search(r"[A-Z]", password))
    digit_criteria = bool(re.search(r"\d", password))
    special_char_criteria = bool(re.search(r"[@$!%*?&]", password))
    
    # Scoring
    if length_criteria:
        strength_score += 1
    if lowercase_criteria:
        strength_score += 1
    if uppercase_criteria:
        strength_score += 1
    if digit_criteria:
        strength_score += 1
    if special_char_criteria:
        strength_score += 1
    
    # Strength evaluation
    if strength_score == 5:
        return "Strong Password"
    elif strength_score >= 3:
        return "Moderate Password"
    else:
        return "Weak Password"

def estimate_crack_time(password):
    charsets = {
        "digits": 10,  # 0-9
        "lowercase": 26,  # a-z
        "uppercase": 26,  # A-Z
        "special": 10  # Common special chars (~10)
    }
    
    charset_size = 0
    if any(c.isdigit() for c in password):
        charset_size += charsets["digits"]
    if any(c.islower() for c in password):
        charset_size += charsets["lowercase"]
    if any(c.isupper() for c in password):
        charset_size += charsets["uppercase"]
    if any(c in "@$!%*?&" for c in password):
        charset_size += charsets["special"]
    
    total_combinations = charset_size ** len(password)
    guesses_per_second = 1e9  # Assuming 1 billion guesses per second (modern GPU brute-force speed)
    estimated_seconds = total_combinations / guesses_per_second
    
    if estimated_seconds < 1:
        return "Less than a second"
    elif estimated_seconds < 60:
        return f"{estimated_seconds:.2f} seconds"
    elif estimated_seconds < 3600:
        return f"{estimated_seconds / 60:.2f} minutes"
    elif estimated_seconds < 86400:
        return f"{estimated_seconds / 3600:.2f} hours"
    elif estimated_seconds < 31536000:
        return f"{estimated_seconds / 86400:.2f} days"
    else:
        return f"{estimated_seconds / 31536000:.2f} years"

if __name__ == "__main__":
    while True:
        password = input("Enter a password to check its strength (or type 'exit' to quit): ")
        if password.lower() == 'exit':
            break
        
        strength = check_password_strength(password)
        crack_time = estimate_crack_time(password)
        
        print(f"Password Strength: {strength}")
        print(f"Estimated Time to Crack: {crack_time}\n")
