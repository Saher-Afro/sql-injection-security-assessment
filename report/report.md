# SQL Injection Security Assessment

## Project Overview
This project demonstrates a practical security assessment of a deliberately vulnerable e-commerce web application. The objective was to identify and validate an SQL Injection vulnerability affecting the product filtering functionality.

The assessment was performed using manual testing techniques with **Burp Suite** to analyze HTTP requests, manipulate input parameters, verify the vulnerability, evaluate its impact, and document remediation recommendations.

---

## Project Objectives
* Identify SQL Injection vulnerabilities.
* Validate exploitability using manual testing.
* Analyze the application's behavior.
* Assess potential business impact.
* Provide practical remediation guidance.

---

## Scope & Target Information

| Parameter | Details |
| :--- | :--- |
| **Application Type** | E-Commerce Web Application |
| **Target Functionality** | Product Category Filter |
| **Testing Methodology** | Manual Web Application Penetration Testing |
| **Tools Used** | Burp Suite Community Edition, Google Chrome, PortSwigger Academy |

---

## Testing Methodology & Proof of Concept (PoC)

### Step 1 – Intercepting the Request
The product filtering request was intercepted using Burp Suite Proxy.  
The application sends the selected category through the parameter: `GET /filter?category=Gifts`

![Original Request](../screenshots/solved.png)

---

### Step 2 – Manual Payload Injection
The intercepted request was sent to Burp Repeater and modified with a classic SQL Injection payload:
```sql
Gifts' OR 1=1--
