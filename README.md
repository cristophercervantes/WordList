# XSS Payloads

## Overview

This repository contains a collection of Cross-Site Scripting (XSS) payloads designed for educational and security testing purposes. It includes payloads leveraging various HTML event handlers, tags, and encoding techniques to demonstrate XSS vulnerabilities in web applications. The payloads are intended for use in controlled environments, such as local vulnerability labs (e.g., DVWA, WebGoat), to help developers and security researchers understand and mitigate XSS risks.

**⚠️ Legal and Ethical Notice**: These payloads are for **educational and authorized testing only**. Unauthorized use on live systems or applications without explicit permission is illegal and unethical. Always obtain consent from system owners before testing.

## Contents

- **Payloads**: Over 100 XSS payloads using HTML event handlers (e.g., `onerror`, `onclick`, `onmouseover`) across 12 HTML tags (`<img>`, `<div>`, `<input>`, etc.).
- **Encodings**: Examples of HTML entity, JavaScript Unicode, URL, and Base64 encodings to bypass common input filters.
- **Documentation**: Guides on payload usage, trigger conditions, and encoding strategies.
- **Examples**: Sample payloads for reflected, stored, and DOM-based XSS scenarios.

## Purpose

This repository aims to:
- Educate developers and security professionals about XSS vulnerabilities.
- Provide a reference for crafting payloads to test web application security.
- Demonstrate encoding techniques to understand filter bypass mechanisms.
- Promote secure coding practices to prevent XSS attacks.

## Getting Started

### Prerequisites

- A local web vulnerability lab (e.g., [DVWA](https://dvwa.co.uk/), [WebGoat](https://owasp.org/www-project-webgoat/)) or a test environment with explicit permission.
- A modern web browser (e.g., Chrome, Firefox, Edge) for testing payloads.
- Optional: Tools like [Burp Suite](https://portswigger.net/burp) or [OWASP ZAP](https://www.zaproxy.org/) for advanced testing and encoding.

### Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/xss-payloads.git
   cd xss-payloads
   ```

2. **Explore Payloads**:
   - Navigate to the `payloads/` directory for raw XSS payloads.
   - Check `encodings/` for encoded versions (HTML entity, JavaScript Unicode, etc.).
   - Review `docs/` for usage guides and trigger conditions.

3. **Set Up a Test Environment**:
   - Install a local lab like DVWA:
     ```bash
     docker run --rm -p 80:80 vulnerables/web-dvwa
     ```
   - Access the lab (e.g., `http://localhost`) and configure it for XSS testing (low security settings recommended for learning).

### Usage

1. **Select a Payload**:
   - Browse `payloads/event-handlers.txt` for payloads like:
     ```html
     <img src="x" onerror="alert(1)">
     <div onclick="alert(1)">Click me</div>
     ```
   - Check `encodings/` for obfuscated versions, e.g.:
     ```html
     <img src="x" onerror="&#97;&#108;&#101;&#114;&#116;&#40;&#49;&#41;">
     ```

2. **Test in a Controlled Environment**:
   - Inject payloads into input fields, query parameters, or other injectable areas in your test lab.
   - Example: In DVWA’s “Reflected XSS” module, enter `<img src="x" onerror="alert(1)">` in the input field and submit.
   - Observe the browser’s behavior (e.g., an `alert(1)` pop-up indicates a successful XSS).

3. **Apply Encodings**:
   - Use encoded payloads to bypass filters. For example, if `alert` is blocked, try:
     ```html
     <img src="x" onerror="\u0061\u006c\u0065\u0072\u0074(1)">
     ```
   - Use tools like Burp Suite’s encoder to generate custom encodings.

4. **Analyze Results**:
   - Check which payloads trigger successfully.
   - Note filter bypasses (e.g., HTML entities vs. plain text) and document findings.

## Payload Categories

- **Event Handlers**: Payloads using 105 HTML event handlers (e.g., `onload`, `onmouseover`, `onerror`) across tags like `<img>`, `<div>`, `<video>`, and `<body>`.
- **Tags**: 12 HTML tags used, including `<input>`, `<form>`, `<script>`, and `<marquee>` (for legacy systems).
- **Encodings**:
  - HTML Entity: `&#97;&#108;&#101;&#114;&#116;`
  - JavaScript Unicode: `\u0061\u006c\u0065\u0072\u0074`
  - URL Encoding: `javascript%3Aalert%281%29`
  - Base64: `eval(atob('YWxlcnQoMSk='))`
- **Contexts**: Covers reflected, stored, and DOM-based XSS scenarios.

## Best Practices for Testing

- **Controlled Environment**: Use local labs or authorized systems only.
- **Ethics**: Obtain explicit permission before testing on any live application.
- **Mitigation**: Learn to prevent XSS by implementing:
  - Input sanitization (e.g., [DOMPurify](https://github.com/cure53/DOMPurify)).
  - Content Security Policy (CSP) to block inline scripts.
  - Proper escaping of user input in HTML, JavaScript, and URL contexts.
- **Tools**: Use Burp Suite, OWASP ZAP, or browser developer tools to analyze injection points and responses.

## Contributing

Contributions are welcome! To contribute:
1. Fork the repository.
2. Add new payloads, encodings, or documentation in the appropriate directories.
3. Ensure payloads are tested in a controlled environment.
4. Submit a pull request with a clear description of changes.

Please follow the [Code of Conduct](CODE_OF_CONDUCT.md) and ensure all contributions align with ethical security practices.

## Resources

- [OWASP XSS Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [PortSwigger XSS Guide](https://portswigger.net/web-security/cross-site-scripting)
- [DVWA](https://dvwa.co.uk/) (Damn Vulnerable Web Application)
- [WebGoat](https://owasp.org/www-project-webgoat/) (OWASP’s training platform)

## License

This repository is licensed under the [MIT License](LICENSE). Use responsibly and only for authorized purposes.

## Contact

For questions or suggestions, open an issue or contact the maintainers. For security vulnerabilities in the repository, use the private reporting feature on GitHub.

**Happy (ethical) hacking!**
