# Access Control

## Introduction
Access control involves applying constraints to determine who or what is authorized to perform actions or access resources, particularly in web applications. It plays a crucial role in maintaining the security and integrity of systems by ensuring that only authenticated and authorized users can access specified resources or perform certain actions.

![image](https://github.com/vsang181/Appsec-Cheatsheet-Port-Swigger-/assets/28651683/80a0a249-0100-4699-b874-cf7c8fde7c6f)

## Key Components
- **Authentication**: Verifies that the user is who they claim to be.
- **Session Management**: Identifies subsequent HTTP requests from the same user.
- **Access Control**: Determines if the user is allowed to perform the attempted action.

### Potential Risks
- **Unauthorized Access to Sensitive Data**: Without proper access controls, sensitive information such as personal data, financial records, or proprietary secrets can be exposed to unauthorized users.
- **Privilege Escalation**: Attackers may exploit weak access controls to gain higher privileges than intended, allowing them to access restricted areas of the application or perform unauthorized actions.
- **Session Hijacking and Management Flaws**: Poorly implemented session management can lead to attackers hijacking user sessions, gaining the same access as the victim.

## Challenges
Designing and managing access controls is complex, often presenting critical security vulnerabilities. It requires a careful balance of business, organizational, and legal constraints, with a high potential for human error.

# Vertical Privilege Escalation

Occurs when a user gains access to functionality or resources they are not authorized for, often due to insufficient protection of sensitive functionalities.

## Examples of Insecure Access Controls
- Accessing admin functionalities without proper authorization.
- Bypassing controls by navigating directly to specific URLs (e.g., https://insecure-website.com/admin).

## Unprotected Functionality
Lack of enforcement on sensitive functionalities allows for vertical privilege escalation, where users can access areas like administrative panels by direct URL access or through disclosed URLs in areas like the `robots.txt` file.

## Security by Obscurity
Relying on obscure URLs to protect sensitive functionality is ineffective, as these can often be discovered through various means, such as JavaScript code revealing the URLs based on user roles.

# Parameter-based Access Control Methods

Insecure practices include storing access rights or roles in user-controllable locations, such as hidden fields or cookies. This approach is insecure because users can modify these values to bypass access controls.

# Horizontal Privilege Escalation

This type of escalation occurs when a user gains access to resources or data belonging to another user, leveraging exploits similar to vertical privilege escalation methods.

## Example of Exploitation
An example includes altering the `id` parameter in a URL to access another user's account page, exploiting insecure direct object reference (IDOR) vulnerabilities.

# Horizontal to Vertical Privilege Escalation

A horizontal privilege escalation can lead to vertical escalation if a more privileged user's account is compromised, allowing attackers to gain administrative access.

## Common Access Control Vulnerabilities

### Broken Authentication
Occurs when attackers can bypass authentication mechanisms to impersonate legitimate users.
- **Risk**: Unauthorized access to user accounts and sensitive data.
- **Mitigation**: Implement Multi-Factor Authentication (MFA), secure password storage practices, and account lockout mechanisms.

### Insecure Direct Object References (IDOR)
An application exposes a reference to an internal implementation object, such as a file or directory, allowing attackers to manipulate these references to access unauthorized data.
- **Risk**: Unauthorized access to files, database records, or other sensitive resources.
- **Mitigation**: Use indirect references mapped to the user session or apply rigorous access control checks before accessing objects based on user input.

### Missing Function Level Access Control
Applications fail to properly enforce access controls on server-side functions, allowing attackers to execute functions beyond their permissions.
- **Risk**: Unauthorized execution of sensitive operations.
- **Mitigation**: Ensure consistent access control checks are enforced both on the client and server sides. Verify permissions before executing any action.

### Security Misconfiguration
Improperly configured permissions on files, directories, or services can lead to unauthorized access or information disclosure.
- **Risk**: Accidental exposure of data or functionality that should be restricted.
- **Mitigation**: Regularly audit configurations and permissions. Apply the principle of least privilege.

## Mitigation Strategies
- **Role-Based Access Control (RBAC)**: Implement roles for users and assign permissions to these roles rather than individual users, simplifying management and enforcement of access controls.
- **Attribute-Based Access Control (ABAC)**: Define access permissions based on attributes (user, resource, environment) and policy rules, allowing for more granular and dynamic access control.
- **Regular Access Reviews**: Periodically review and update access rights to ensure they align with current roles, responsibilities, and security policies.
- **Secure Session Management**: Use secure, unpredictable session identifiers and implement timeout mechanisms to reduce the risk of session hijacking.

## Conclusion
Robust access control is critical for securing web applications against unauthorized access and preventing data breaches. Understanding the potential vulnerabilities and appropriate mitigation strategies is essential for AppSec professionals to protect applications from access control-related security threats.

## Further Reading
- [OWASP Guide on Access Control](https://owasp.org/www-community/Access_Control)
