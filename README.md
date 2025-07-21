### README.md

# Secure Software Development Portfolio
**MSc Computer Science**

Welcome to my professional e-portfolio for Secure Software Development. This portfolio showcases selected coursework and applied security practices including secure software design, input validation, threat modelling, and ontological data modelling.

## 📂 Contents

- [Towers of Hanoi (Recursion)](projects/towers-of-hanoi.md)
- [Regex Validation for UK Postcodes](projects/uk-postcode-regex.md)
- [UML Design & OWASP Injection Flaw](projects/uml-injection-flaw.md)
- [Secure Ontology for Online Retail](projects/ontology-online-retail.md)

---

### projects/towers-of-hanoi.md

# Towers of Hanoi (Recursion)

This section explores the recursive solution to the Towers of Hanoi problem and reflects on recursion limits and their implications for secure software.

## 🧠 Problem Description
The Towers of Hanoi problem requires moving disks between pegs under constraints. Below is a Python implementation:

```python
# towers_of_hanoi.py
def towers_of_hanoi(n, source, target, auxiliary, moves):
    if n == 1:
        print(f"Move disk * from {source} to {target}")
        moves[0] += 1
        return
    towers_of_hanoi(n - 1, source, auxiliary, target, moves)
    print(f"Move disk * from {source} to {target}")
    moves[0] += 1
    towers_of_hanoi(n - 1, auxiliary, target, source, moves)

def main():
    num_disks = int(input("Enter the number of disks: "))
    moves = [0]
    towers_of_hanoi(num_disks, 'A', 'C', 'B', moves)
    print(f"Total moves executed: {moves[0]}")

if __name__ == "__main__":
    main()
```

## 🔐 Security Implications
- **Recursion Depth**: Python limits recursion to ~1000 levels. Abuse could lead to DoS.
- **Mitigation**: Validate input and consider iterative implementations if needed.

---

### projects/uk-postcode-regex.md

# Regex Validation for UK Postcodes

## ✅ Validating UK Postcodes in Python

```python
import re

def validate_postcode(postcode):
    pattern = r'^(GIR 0AA|[A-Z]{1,2}[0-9][0-9]?[A-Z]?\s?[0-9][A-Z]{2})$'
    return re.match(pattern, postcode) is not None

def main():
    test_postcodes = [
        "M1 1AA", "M60 1NW", "CR2 6XH",
        "DN55 1PT", "W1A 1HQ", "EC1A 1BB", "ST7 9HV"
    ]
    for postcode in test_postcodes:
        print(f"{postcode}: {'valid' if validate_postcode(postcode) else 'invalid'}")

if __name__ == "__main__":
    main()
```

## ⚠️ Preventing Evil Regex Attacks
- Limit input size
- Avoid nested quantifiers
- Use non-capturing groups where possible
- Test edge cases

---

### projects/uml-injection-flaw.md

# UML Design & OWASP Injection Flaw

## 🛠️ Tool Used: Umbrello

## 🔎 Selected OWASP Flaw
**Injection Flaws** – occur when untrusted input is passed to an interpreter (e.g., SQL).

### 📈 Flow of Vulnerability:
1. User Input
2. Input Not Validated
3. Data Processed with Query
4. Executed Unchecked
5. Exploitation Occurs

## 🧩 UML Models Used
- **Use Case Diagram**: For interaction analysis
- **Class Diagram**: Input validation responsibilities
- **Sequence Diagram**: Secure flow validation
- **Activity Diagram**: Visual path of user input processing

These models help visualize and defend against injection threats by clearly outlining logic and input pathways.

---

### projects/ontology-online-retail.md

# Secure Ontology for Online Retail

## 📚 Introduction
Ontology defines the relationships and structure of knowledge domains. In online retail, it enhances system interoperability and secure data handling.

## 📦 Core Classes
- **User**: ID, Name, Email, Password (hashed), Role
- **Product**: ID, Name, Description, Price, Stock
- **Order**: ID, Date, Total, Status
- **Category**: Class hierarchy
- **Payment**: ID, Amount, Method

## 🔗 Relationships
- User → Order (1:N)
- Order → Product (M:N)
- Product → Category (N:1)

## 🔐 Security Features
- **Least Privilege**: Role-based access
- **Audit Trails**: Order/payment logs
- **GDPR Compliance**: Anonymization
- **Data Protection**: Hashed passwords, encryption

## 🧾 References
- Alhassan & Alhassan (2021), Bhatia & Gupta (2022), Saltzer & Schroeder (1975)
