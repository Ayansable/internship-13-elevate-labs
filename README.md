# internship-13-elevate-labs
Secure API Testing &amp; Authorization Validation
This project focuses on testing REST APIs for common security misconfigurations and authorization flaws using tools like Postman, cURL, and Insomnia.
The goal is to identify vulnerabilities related to authentication, authorization, input validation, and rate limiting, and map them to OWASP API Security Top 10 risks.

Tools Used

Postman (Primary)

cURL

Insomnia

Prerequisites

Basic understanding of REST APIs

Knowledge of HTTP methods (GET, POST, PUT, DELETE)

API endpoint URL and documentation

Valid and invalid authentication tokens (if applicable)

API Testing Steps
1. Basic API Request

Open Postman

Select HTTP method (GET/POST)

Enter API endpoint URL

Click Send

Verify response status and data

2. Authentication Testing

Objective: Check if the API properly enforces authentication.

Send request with valid token

Remove Authorization header and resend request

Expected Result:

Without token → 401 Unauthorized or 403 Forbidden

OWASP Mapping: API2 – Broken Authentication

3. Authorization Testing (IDOR)

Objective: Check if users can access other users’ data.

Change resource ID in URL
Example:

/users/1 → /users/2


Expected Result:

Access denied

OWASP Mapping: API1 – Broken Object Level Authorization

4. HTTP Method Testing

Objective: Ensure only allowed methods are accepted.

Try unsupported methods (e.g., DELETE instead of GET)

Expected Result:

405 Method Not Allowed

5. Input Validation Testing

Objective: Check handling of malformed or malicious input.

Send invalid data:

{
  "name": "<script>alert(1)</script>",
  "age": -9999
}


Expected Result:

400 Bad Request

OWASP Mapping: API8 – Injection / Input Validation Issues

6. Mass Assignment Testing

Objective: Check if hidden or sensitive fields can be modified.

Add extra fields:

{
  "role": "admin",
  "isVerified": true
}


Expected Result:

Fields ignored or rejected

OWASP Mapping: API6 – Mass Assignment

7. Rate Limiting Testing

Objective: Check if API limits excessive requests.

Send multiple rapid requests

Expected Result:

429 Too Many Requests

OWASP Mapping: API4 – Lack of Resources & Rate Limiting

8. Error Handling Testing

Objective: Check if API exposes sensitive error details.

Send invalid requests

Observe error messages

Expected Result:

Generic error messages only

OWASP Mapping: API7 – Security Misconfiguration

What to Observe

HTTP status codes

Response body data
