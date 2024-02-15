# Access Control

## Introduction
Access control involves applying constraints to determine who or what is authorized to perform actions or access resources, particularly in web applications. It plays a crucial role in maintaining the security and integrity of systems by ensuring that only authenticated and authorized users can access specified resources or perform certain actions.

![image](https://github.com/vsang181/Appsec-Cheatsheet-Port-Swigger-/assets/28651683/959f31f0-ddda-4af9-8060-6897d9768c4e)

## Key Components
- **Authentication**: Verifies that the user is who they claim to be.
- **Session Management**: Identifies subsequent HTTP requests from the same user.
- **Access Control**: Determines if the user is allowed to perform the attempted action.

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

## Conclusion

Understanding access control and its vulnerabilities is essential for securing web applications. By implementing robust authentication, session management, and access control measures, and by avoiding common pitfalls such as insecure direct object references and reliance on security through obscurity, organizations can significantly reduce the risk of unauthorized access and escalation of privileges.

## Further Reading
- OWASP Guide on Access Control
- Secure Coding Practices for Web Applications
