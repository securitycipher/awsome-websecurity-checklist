# Web Application Security Checklist

---

## 1. Authentication and Session Management

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Weak Passwords and Brute-Force Vulnerabilities | Test for weak passwords and brute-force vulnerabilities.                                      |
| Multi-Factor Authentication (MFA)         | Verify that multi-factor authentication (MFA) is properly implemented.                        |
| Password Recovery, Reset, and Update      | Check for password recovery, reset, and update vulnerabilities.                               |
| Session Management                        | Assess session management, ensuring secure cookies, session timeout, and session fixation.     |
| Logout Functionality                      | Ensure proper logout functionality and invalidation of sessions.                               |
| Default Credentials                       | Check if default credentials are changed or disabled.                                         |
| Account Lockout Mechanism                 | Verify the presence and effectiveness of account lockout mechanisms after multiple failed login attempts. |
| Secure Password Storage                   | Ensure passwords are stored securely using strong hashing algorithms like bcrypt.             |
| Token Expiration                          | Verify that authentication tokens have appropriate expiration times.                          |
| Session Hijacking                         | Test for vulnerabilities that could lead to session hijacking, such as missing Secure or HttpOnly flags on cookies. |
| Secure Login Forms                        | Ensure that login forms are served over HTTPS and do not expose credentials in logs or URL parameters. |
| CAPTCHAs                                  | Verify the implementation of CAPTCHAs to prevent automated login attempts.                    |
| Password Complexity                       | Ensure password policies enforce complexity requirements (length, character variety).         |
| Remember Me                               | Check the security of "Remember Me" functionality and ensure tokens expire appropriately.     |
| Session Timeout                           | Validate session timeout configurations to prevent extended idle sessions.                    |
| Inactive Account Handling                 | Ensure that inactive accounts are disabled after a defined period.                            |

---

## 2. Authorization

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Privilege Escalation                      | Test for vertical and horizontal privilege escalation.                                       |
| Role-Based Access Control (RBAC)          | Verify role-based access control (RBAC) implementation.                                      |
| Insecure Direct Object References (IDOR)  | Check for Insecure Direct Object References (IDOR).                                          |
| Access Control Policies                   | Review and test access control policies for effectiveness.                                   |
| Least Privilege Principle                 | Ensure that users have the minimum level of access necessary to perform their functions.      |
| Forceful Browsing                         | Test if unauthorized users can access restricted resources by manipulating URLs or parameters.|
| Multi-Tenancy                             | Verify that users from different tenants cannot access each other's data.                    |
| Security Misconfigurations                | Check for misconfigurations in access controls, such as overly permissive roles.             |
| Time-Based Authorization                  | Test for authorization that changes based on time or other factors.                          |
| Logical Access Controls                   | Ensure that access control mechanisms are implemented logically throughout the application.   |
| Role Misuse                               | Check for roles being misused to gain unauthorized access.                                   |
| Sensitive Functionality                   | Ensure sensitive functionality is only accessible by authorized roles.                       |
| Dynamic Access Control                    | Test for dynamic access control based on context (e.g., IP address, device).                 |

---

## 3. Input Validation

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Cross-Site Scripting (XSS)                | Test for XSS vulnerabilities (Reflected, Stored, DOM-based).                                 |
| SQL Injection (SQLi) and NoSQL Injection  | Check for SQL Injection (SQLi) and NoSQL Injection.                                          |
| Command Injection, LDAP Injection, and XML External Entities (XXE) | Assess for Command Injection, LDAP Injection, and XML External Entities (XXE).               |
| Client-Side and Server-Side Validation    | Validate input on both client-side and server-side.                                          |
| Cross-Site Script Inclusion (XSSI)        | Test for the possibility of including external scripts that execute within the application's context. |
| HTTP Parameter Pollution                  | Check if multiple parameters with the same name can be used to manipulate the application logic. |
| Remote Code Execution (RCE)               | Test for vulnerabilities that could lead to remote code execution.                           |
| Directory Traversal                       | Check for directory traversal vulnerabilities that could allow access to unauthorized files.  |
| HTTP Splitting/Smuggling                  | Test for HTTP request splitting and smuggling vulnerabilities.                               |
| Path Traversal                            | Test for vulnerabilities that allow attackers to traverse the directory structure of the server. |
| File Inclusion                            | Check for Local File Inclusion (LFI) and Remote File Inclusion (RFI) vulnerabilities.         |
| Template Injection                        | Test for vulnerabilities in template engines that could lead to code execution.              |
| Input Length                              | Validate input length to prevent buffer overflow attacks.                                    |
| Data Sanitization                         | Ensure input data is properly sanitized before processing.                                   |
| Encoding                                  | Verify that all input is appropriately encoded before outputting.                            |
| Integer Overflow                          | Test for integer overflow and underflow vulnerabilities.                                     |
| File Upload Restrictions                  | Validate file upload restrictions to prevent malicious files.                                |
| Whitelisting and Blacklisting             | Ensure proper whitelisting and blacklisting of input values.                                 |

---

## 4. Business Logic

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Logic Flaws and Bypasses                  | Identify and test for logic flaws and bypasses in the application’s workflow.                |
| Security Controls in Business Processes   | Verify the proper implementation of security controls in business processes.                 |
| Race Conditions                           | Test for race conditions that could cause security issues.                                   |
| Business Process Tampering                | Ensure that business process steps cannot be manipulated or skipped.                         |
| Transaction Manipulation                  | Test for the ability to manipulate transactions to cause unintended outcomes.                |
| Workflow Validation                       | Verify that business workflows enforce proper sequencing and validation at each step.        |
| Inconsistent State                        | Test for conditions that could lead to an inconsistent state in the application.             |
| Integrity Checks                          | Ensure that integrity checks are implemented and cannot be bypassed.                         |
| Business Logic Abuse                      | Identify potential abuse cases in the business logic.                                        |
| Transaction Duplication                   | Test for the possibility of duplicating transactions.                                        |
| Conditional Logic                         | Verify that conditional logic enforces the correct business rules.                           |
| Business Logic Abuse                      | Test for potential abuse of business logic to perform unauthorized actions.                  |
| Non-Sequential Steps                      | Check if steps can be performed out of order or skipped entirely.                            |
| Transaction Reordering                    | Test if transactions can be reordered to achieve a malicious outcome.                        |

---

## 5. Security Misconfiguration

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Configuration of Servers, Databases, and Frameworks | Check for improper configurations of web servers, databases, and frameworks.                 |
| Debug and Error Messages                  | Verify that debug and error messages do not reveal sensitive information.                    |
| Removal of Unnecessary Features           | Ensure that unnecessary features, such as default accounts or sample files, are removed.     |
| HTTP Headers                              | Verify proper HTTP headers are set (e.g., Content-Type, Cache-Control).                      |
| Secure Directory Listings                 | Ensure directory listings are disabled on the web server.                                    |
| File Permissions                          | Check for proper file permissions to prevent unauthorized access.                            |
| Default Error Pages                       | Ensure custom error pages are configured to prevent information disclosure.                  |
| Administrative Interfaces                 | Verify that administrative interfaces are properly secured and not exposed to unauthorized users. |
| Third-Party Integrations                  | Check for security configurations in third-party integrations and services.                  |
| Configuration Management                  | Verify that configuration management practices are in place to maintain secure settings.     |
| Software Updates                          | Ensure all software components are up-to-date with the latest security patches.              |
| Backup Configurations                     | Check the security of backup configurations and processes.                                   |
| API Security Settings                     | Verify that APIs are securely configured to prevent unauthorized access.                     |
| Cloud Services                            | Ensure secure configuration of cloud services used by the application.                       |
| Environment Variables                     | Check for secure handling and storage of environment variables.                              |

---

## 6. Sensitive Data Exposure

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Encryption of Sensitive Data              | Ensure that sensitive data (PII, passwords, credit card information) is encrypted at rest and in transit. |
| Secure Protocols                          | Verify the implementation of secure protocols (e.g., HTTPS, TLS).                            |
| Data Leakage                              | Check for inadvertent data leakage in logs, error messages, or client-side code.             |
| HTTP Strict Transport Security (HSTS)     | Verify the use of HSTS to enforce secure connections.                                        |
| Information Disclosure                    | Test for information disclosure vulnerabilities that reveal sensitive information.           |
| Backup Data                               | Ensure that backup data is securely stored and encrypted.                                    |
| Data Masking                              | Verify that sensitive data is masked or obfuscated where appropriate.                        |
| Sensitive Data in URLs                    | Check that sensitive data is not included in URLs or referrer headers.                       |
| Secure Data Handling                      | Ensure secure handling of sensitive data throughout its lifecycle.                           |
| Encryption Key Management                 | Verify secure management and storage of encryption keys.                                     |
| Tokenization                              | Ensure that tokenization is used where applicable for sensitive data.                        |
| Data Anonymization                        | Validate data anonymization techniques to protect sensitive information.                     |
| Secure Disposal                           | Ensure secure disposal of sensitive data and related media.                                  |

---

## 7. Cross-Site Request Forgery (CSRF)

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| CSRF Vulnerabilities                      | Test for CSRF vulnerabilities and ensure the use of anti-CSRF tokens.                        |
| State-Changing Operations                 | Validate that the application does not perform state-changing operations without proper authorization. |
| SameSite Cookies                          | Ensure cookies are set with the SameSite attribute to prevent CSRF attacks.                  |
| Referer Header                            | Verify the use of the Referer header to help prevent CSRF attacks.                           |
| Double Submit Cookie                      | Check for the implementation of the double submit cookie pattern as an additional CSRF mitigation. |
| Custom Headers                            | Ensure that custom headers are required for state-changing requests to prevent CSRF.         |
| Form Token Validation                     | Verify that form tokens are used and validated for all state-changing requests.              |
| Secure Token Storage                      | Ensure anti-CSRF tokens are stored securely and not exposed to attackers.                    |
| One-Time Tokens                           | Validate the use of one-time tokens for critical operations to prevent replay attacks.       |
| Token Expiry                              | Check for proper expiry of CSRF tokens to reduce the risk of token reuse.                    |

---

## 8. File Uploads

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Unrestricted File Upload and Malware Injection | Assess file upload functionality for vulnerabilities like unrestricted file upload and malware injection. |
| File Type Validation and Storage          | Check for proper file type validation and storage.                                           |
| File Execution                            | Ensure that uploaded files cannot be executed on the server.                                 |
| Content-Type Verification                 | Verify that the content type of uploaded files matches the expected type.                    |
| File Size Limits                          | Ensure file size limits are enforced to prevent denial of service attacks.                   |
| Virus Scanning                            | Verify that uploaded files are scanned for viruses and malware.                              |
| Temporary Storage                         | Check the security of temporary storage locations for uploaded files.                        |
| File Path Manipulation                    | Ensure that file path manipulation is not possible through file uploads.                     |
| Storage Location                          | Ensure uploaded files are stored in secure locations with appropriate access controls.       |
| File Integrity                            | Verify that file integrity checks are performed on uploaded files.                           |
| Sanitization of File Names                | Ensure that uploaded file names are sanitized to prevent directory traversal attacks.        |
| Quarantine Process                        | Validate the quarantine process for suspicious files uploaded to the server.                 |
| Metadata Stripping                        | Ensure that metadata is stripped from uploaded files to prevent sensitive information leakage. |

---

## 9. Client-Side Security

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Content Security Policy (CSP)             | Verify the implementation of Content Security Policy (CSP).                                  |
| JavaScript Code and Third-Party Libraries | Test for vulnerabilities in JavaScript code and third-party libraries.                       |
| Secure Use of Cookies                     | Ensure secure use of cookies (HttpOnly, Secure, SameSite attributes).                        |
| Local Storage and Session Storage         | Check for sensitive data stored insecurely in local storage or session storage.              |
| JavaScript Obfuscation                    | Ensure that sensitive business logic is not exposed in client-side JavaScript.               |
| Clickjacking                              | Test for clickjacking vulnerabilities and ensure the use of X-Frame-Options or CSP frame-ancestors. |
| DOM Manipulation                          | Check for insecure DOM manipulation practices that could lead to vulnerabilities.            |
| HTML Injection                            | Test for HTML injection vulnerabilities that could compromise the application's integrity.   |
| Secure Event Handling                     | Ensure secure handling of client-side events to prevent event hijacking.                     |
| Browser Security Features                 | Verify the use of browser security features (e.g., sandboxing, site isolation).              |
| Inline Scripts                            | Check for the presence of inline scripts and ensure they are minimized or eliminated.        |
| Sensitive Information Disclosure          | Test for sensitive information being disclosed in client-side code.                          |
| Secure Form Handling                      | Validate secure handling of form data in the client-side code.                               |

---

## 10. Security Headers

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Presence and Configuration                | Verify the presence and correct configuration of security headers (e.g., X-Content-Type-Options, X-Frame-Options, Strict-Transport-Security). |
| Referrer Policy                           | Ensure that the Referrer-Policy header is configured correctly to minimize information leakage. |
| Permissions Policy                        | Check the Permissions-Policy header to control which features and APIs can be used in the browser. |
| Feature Policy                            | Verify the implementation of Feature Policy to control the use of web features and APIs.      |
| Cross-Origin Resource Sharing (CORS)      | Ensure that CORS headers are properly configured to prevent unauthorized cross-origin requests. |
| XSS Protection                            | Verify the presence and configuration of XSS protection headers (e.g., X-XSS-Protection).     |
| Content-Type Options                      | Ensure the use of X-Content-Type-Options to prevent MIME type sniffing.                       |
| Cache Control                             | Check for proper cache control headers to prevent sensitive data caching.                    |
| Expect-CT                                 | Verify the implementation of Expect-CT to enforce Certificate Transparency.                  |
| Server Header                             | Ensure the Server header is configured to minimize information disclosure.                   |

---

## 11. API Security

| Test Case                                 | Description                                                                                  |
|-------------------------------------------|----------------------------------------------------------------------------------------------|
| Rate Limiting and Throttling              | Test for API rate limiting and throttling.                                                   |
| Authentication and Authorization          | Assess for improper API authentication and authorization.                                    |
| Data Exposure                             | Check for data exposure through API responses.                                               |
| Input Validation                          | Ensure proper input validation and sanitization in API endpoints.                            |
| CORS Configuration                        | Verify that Cross-Origin Resource Sharing (CORS) is properly configured to prevent unauthorized access. |
| API Key Management                        | Check for secure management and storage of API keys.                                         |
| Versioning                                | Ensure that API versioning is implemented to manage changes and deprecations securely.       |
| Error Handling                            | Verify that API error messages do not reveal sensitive information.                          |
| Parameter Tampering                       | Test for vulnerabilities where API parameters can be tampered with to achieve unintended effects. |
| Mass Assignment                           | Ensure that APIs do not accept and process unexpected parameters that could lead to mass assignment vulnerabilities. |
| JSON Web Token (JWT)                      | Verify the secure implementation and storage of JWTs, including proper signing and expiration.|
| Response Caching                          | Check for proper caching of API responses to prevent sensitive data exposure.                |
| Rate Limiting Evasion                     | Test for mechanisms to evade API rate limiting.                                              |
| API Gateway Security                      | Ensure the security of API gateways and their configurations.                                |

---
