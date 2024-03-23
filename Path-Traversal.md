# Path Traversal

## What is Path Traversal?

Path traversal, also known as directory traversal, is a web security vulnerability that allows an attacker to read (and sometimes write to) arbitrary files on the server running an application. This can include sensitive files such as application code and data, credentials for back-end systems, and operating system files, potentially leading to full control over the server.

![image](https://github.com/vsang181/Appsec-Cheatsheet-Port-Swigger-/assets/28651683/0cb819a5-33c4-47f8-895b-d5711fcc4612)

### Reading Arbitrary Files via Path Traversal

Consider a shopping application that loads item images with a URL like: `<img src="/loadImage?filename=218.png">`. This URL takes a `filename` parameter and returns the contents of the specified file, typically stored in a directory such as `/var/www/images/`.

Without defenses against path traversal, attackers can manipulate the `filename` parameter to access files outside the intended directory. For example, requesting `https://insecure-website.com/loadImage?filename=../../../etc/passwd` would attempt to access the `/etc/passwd` file, which contains user details on Unix-based systems.

Windows servers are also vulnerable, with directory traversal sequences like `..\` being valid. An example attack URL on a Windows server might look like `https://insecure-website.com/loadImage?filename=..\..\..\windows\win.ini`.

## Common Obstacles and Bypass Techniques

Applications often implement defenses against path traversal, such as blocking or stripping directory traversal sequences from input. However, several techniques can bypass these defenses:

- **Using Absolute Paths:** Specifying an absolute file path directly, e.g., `filename=/etc/passwd`.
- **Nested Traversal Sequences:** Employing sequences like `....//` or `....\/` which revert to simple traversal sequences when the inner sequence is stripped.
- **URL Encoding:** Encoding traversal sequences, e.g., `%2e%2e%2f` for `../`, to bypass web server sanitization.
- **Required Base Folder in Input:** Including the expected base directory in the user input followed by traversal sequences.
- **Expected File Extension Bypass:** Using null bytes to terminate the file path before an expected file extension, e.g., `filename=../../../etc/passwd%00.png`.

## Prevention of Path Traversal Attacks

The most effective prevention strategy is to avoid passing user-supplied input to filesystem APIs. If unavoidable, two layers of defense are recommended:

1. **Validate User Input:** Use whitelisting or ensure the input contains only permitted content.
2. **Canonicalize the Path:** Append user input to the base directory and use filesystem APIs to canonicalize the path, verifying it starts with the expected base directory.

### Example Defense in Java

```java
File file = new File(BASE_DIRECTORY, userInput);
if (file.getCanonicalPath().startsWith(BASE_DIRECTORY)) {
    // process file
}

This Java code example demonstrates validating the canonical path of a file based on user input to prevent path traversal.
```

.
.
.
.
.
.
_In progress..._

## Let's Connect

I welcome your insights, feedback, and opportunities for collaboration. Together, we can make the digital world safer, one challenge at a time.

- **LinkedIn**: (https://www.linkedin.com/in/aashwadhaama/)

I look forward to connecting with fellow cybersecurity enthusiasts and professionals to share knowledge and work together towards a more secure digital environment.
