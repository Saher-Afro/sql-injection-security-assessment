# SQL Injection Security Assessment Report

## Project Information

**Assessment Type:** Manual Web Application Penetration Testing

**Target:** Deliberately Vulnerable Web Application (PortSwigger Web Security Academy)

**Category:** SQL Injection

**Testing Method:** Manual Testing using Burp Suite

**Status:** Vulnerability Successfully Verified


---

# Objective

The purpose of this assessment was to identify and verify SQL Injection vulnerabilities affecting the product filtering functionality of the application.

The testing focused on user-supplied input to determine whether SQL queries could be manipulated.

---

# Testing Process

The application was first explored manually to understand how product categories were filtered.

Traffic was intercepted using Burp Suite Repeater.

The request below was identified as the entry point:

```

GET /filter?category=Gifts

```

A simple SQL payload was appended to the category parameter:

```

' OR 1=1--

```

Resulting request:

```

GET /filter?category=Gifts'+OR+1=1--

```

After sending the modified request, the application returned products from every category instead of only the selected one.

This behavior confirmed that the SQL query was vulnerable to injection.

---

# Findings

## Vulnerability

SQL Injection in WHERE Clause

Severity: High

OWASP Category:

A03:2021 - Injection

---

# Evidence

Observed behavior:

- Product filtering restrictions were bypassed.
- Products from all categories became visible.
- The application accepted SQL syntax as part of user input.

The response confirmed successful manipulation of the backend SQL query.

---

# Root Cause

User input was included directly inside the SQL statement without proper validation or parameterized queries.

Because the application trusted user-controlled input, arbitrary SQL conditions could be injected.

---

# Risk

An attacker could potentially:

- Bypass application logic
- Retrieve unauthorized information
- Enumerate hidden records
- Access sensitive data
- Build more advanced SQL Injection attacks

Depending on the database configuration, the impact could become critical.

---

# Recommendation

The following security controls are recommended:

- Use parameterized queries (Prepared Statements).
- Never concatenate user input into SQL queries.
- Validate all incoming parameters.
- Apply allow-list input validation whenever possible.
- Return generic error messages.
- Perform regular security testing before deployment.

---

# Tools Used

- Burp Suite Community Edition
- Google Chrome
- PortSwigger Web Security Academy

---

# Skills Demonstrated

- Manual Web Application Testing
- HTTP Request Analysis
- Burp Suite Repeater
- SQL Injection Identification
- Vulnerability Validation
- Security Reporting
- Risk Assessment

---

# Conclusion

The assessment successfully identified a SQL Injection vulnerability in the application's product filtering functionality.

The issue was manually verified through request manipulation and demonstrated how improper handling of user input can allow attackers to bypass intended application behavior.

Implementing parameterized queries together with proper input validation would eliminate this vulnerability.
