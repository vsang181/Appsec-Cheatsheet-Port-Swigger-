# Access Control Vulnerabilities and Privilege Escalation

## Introduction

Access control in the context of web applications is pivotal for maintaining secure interactions on the web. It relies on authentication, session management, and the actual access control mechanisms to ensure that only authorized actions are performed by authenticated users. Unfortunately, broken access controls are common, presenting significant security risks.

![image](https://github.com/vsang181/Appsec-Cheatsheet-Port-Swigger-/assets/28651683/5cab0175-b719-4386-86be-ca2dd1d340ff)

### What is Access Control?

- **Authentication**: Confirms the user's identity.
- **Session Management**: Identifies HTTP requests from the authenticated user.
- **Access Control**: Determines if the user can perform the attempted action.

### Access Control Vulnerabilities
Designing and managing access controls is complex, involving technical implementations that adhere to business, organizational, and legal constraints. This complexity often leads to vulnerabilities.

#### Types of Access Control

1. **Vertical Access Controls**: Restrict access to sensitive functionality based on user types.
2. **Horizontal Access Controls**: Restrict access to resources based on the specific user.
3. **Context-dependent Access Controls**: Restrict access based on the application's state or user interaction.

### Examples of Broken Access Controls

- **Vertical Privilege Escalation**: Users access functions they shouldn't.
- **Unprotected Functionality**: Sensitive functions are accessible without proper protection.
- **Parameter-based Access Control Methods**: Access rights are stored in user-controllable locations, leading to unauthorized access.
- **Broken Access Control from Platform Misconfiguration**: Incorrect platform layer access control settings.
- **Broken Access Control from URL-matching Discrepancies**: Inconsistent path matching leads to unauthorized access.
- **Horizontal Privilege Escalation**: Accessing resources that belong to another user.
- **Insecure Direct Object References (IDORs)**: Directly accessing objects based on user-supplied input.

### Preventing Access Control Vulnerabilities

1. **Avoid Obfuscation**: Never rely solely on obfuscation for access control.
2. **Deny Access by Default**: Access should be denied by default unless a resource is intended to be publicly accessible.
3. **Use a Unified Access Control Mechanism**: Implement a single, application-wide mechanism for access control.
4. **Mandatory Access Declaration**: Developers should declare allowed access for each resource at the code level.
5. **Audit and Test**: Conduct thorough audits and tests on access controls to ensure they function as intended.


