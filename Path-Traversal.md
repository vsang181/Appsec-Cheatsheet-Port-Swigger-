# Path Traversal

## Introduction
Path Traversal, also known as directory traversal, represents a critical security vulnerability that can allow attackers to access arbitrary files on a server. This cheatsheet provides an overview, examples, and mitigation strategies to prepare for application security (AppSec) interviews.

## What is Path Traversal?
Path traversal vulnerabilities enable attackers to read (and possibly write to) arbitrary files on the server running an application. This can lead to unauthorized access to sensitive data or even full control over the server.

### Potential Risks
- **Exposure of Application Code and Data**: Access to application source code can reveal backend logic, secrets, and other sensitive information.
- **Access to Backend System Credentials**: Credentials stored on the server can be compromised, leading to unauthorized access to databases and other systems.
- **Leakage of Sensitive OS Files**: Files like `/etc/passwd` on Unix systems or `C:\Windows\win.ini` on Windows can reveal user information and system configurations.

## Exploiting Path Traversal
Consider a web application that loads images for items on sale using a query parameter to specify the image file. Without proper validation, an attacker can manipulate the `filename` parameter to access arbitrary files on the server.

### Example Vulnerability
An application uses the following HTML to display images:

```
html
<img src="/loadImage?filename=218.png">
```
It constructs the file path by appending the filename parameter to a base directory, such as /var/www/images/. Without safeguards, an attacker could manipulate the path to access system files:
url

```
https://insecure-website.com/loadImage?filename=../../../etc/passwd
```

This URL attempts to traverse up the directory structure to access /etc/passwd, a critical system file on Unix-based systems.

## Windows Path Traversal

On Windows, traversal sequences include ../ and ..\. An attacker could use these to target system files like win.ini:

```
https://insecure-website.com/loadImage?filename=..\..\..\windows\win.ini
```
## Mitigation Strategies
- **Validating Input**: Ensure that the file paths or names supplied in user input match expected patterns.
- **Using Allow Lists**: Only allow access to a predefined list of safe files or directories.
- **Implementing Secure File Access**: Utilize secure APIs that automatically mitigate directory traversal vulnerabilities.
- **Applying the Principle of Least Privilege**: Restrict the application's permissions to access only the files and directories necessary for its operation.


## Conclusion
Understanding and mitigating path traversal vulnerabilities are crucial for securing web applications. This cheatsheet aims to provide AppSec interview candidates with the knowledge to identify and discuss strategies to prevent these vulnerabilities.

## Further Reading
- [OWASP Guide on Path Traversal](https://owasp.org/www-community/attacks/Path_Traversal)
