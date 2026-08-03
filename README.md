# SQL Injection Security Assessment

## Project Overview
This project demonstrates a manual Web Application Penetration Test performed on a deliberately vulnerable e-commerce application from PortSwigger Web Security Academy.

The objective was to identify and validate an SQL Injection vulnerability affecting the product filtering functionality.

---

## Scope & Target Information

- **Application Type:** Deliberately Vulnerable E-commerce Application
- **Target:** Product Category Filter
- **Testing Methodology:** Manual Web Application Penetration Testing

---

## Tools Used

- Burp Suite Community Edition
- Google Chrome
- Burp Repeater
- PortSwigger Web Security Academy

---

## Proof of Concept (PoC) & Steps

### 1. Intercepting Request
![Original Request](screenshots/request.png)

### 2. Payload Injection
![Modified Request](screenshots/exploit.png)

### 3. Server Response
![Server Response](screenshots/response.png)

### 4. Lab Solved
![Lab Completed](screenshots/solved.png)

---

## Technical Report
For the full detailed security assessment report, mitigation steps, and technical analysis, please check the [Full Report](report/report.md).
