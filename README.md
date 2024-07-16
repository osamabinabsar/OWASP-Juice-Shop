# OWASP-Juice-Shop

## Objective

This project aims to deepen understanding of common security vulnerabilities and their exploitation techniques in a controlled environment. By actively testing, identifying, and exploiting vulnerabilities within OWASP Juice Shop, I aim to strengthen my proficiency in web application penetration testing and secure coding practices. This hands-on experience not only prepares me for real-world cybersecurity challenges but also contributes to building a robust skill set as a security professional.


### Skills Learned
- Various web application vulnerabilities, tactics and techniques
- SQL Injeciton, XSS, CSRF
- Broken Access Control,
- Brute forcing, BurpSuite

### Tools Used
- Burp Suite


### Steps




#### Persistent vs Reflected XSS
Persistent XSS (Stored XSS):
   - Definition: Persistent XSS occurs when the malicious script is injected into a website's database (or another data store) through a vulnerable input field (e.g., comment section, forum post, user profile, etc.).
  -  Execution: The injected script is then served to every user who accesses the affected page, regardless of who injected the malicious code originally.
  -  Impact: This type of XSS attack can have a wide-reaching impact as the malicious script persists and is executed whenever the vulnerable page is loaded by any user.
  -  Example: An attacker injects a malicious script into a comment form on a blog. When other users view the blog post containing the comment, the script executes in their browsers, potentially stealing session cookies or performing actions on behalf of the victim.

Reflected XSS:
   - Definition: Reflected XSS occurs when the malicious script is part of the request sent to the server and is reflected back in the server's response. The script is not stored on the server but is included in the response directly from the request.
  -  Execution: The attacker typically crafts a URL containing the malicious script and tricks the victim into clicking the URL. The script executes in the victim's browser when the vulnerable page processes the request and reflects the script back in the response.
 -   Scope: Reflected XSS attacks are often limited to the context of the victim who clicked the malicious link or submitted the specially crafted request containing the malicious script.
 -   Example: An attacker sends a crafted URL to a victim through phishing or social engineering. When the victim clicks the URL, the script executes in their browser, potentially sending sensitive information back to the attacker.
-
Key Differences:
  -  Persistence: Persistent XSS involves storing the malicious script on the server or in a data store, making it persistent across multiple user sessions. Reflected XSS does not involve server-side storage of the script; it is reflected back in the server's response from the request.
   - Delivery: Persistent XSS delivers the malicious script to all users who access the affected page where the script is stored. Reflected XSS delivers the script to specific victims who interact with a specially crafted URL or form submission.
   - Mitigation: Mitigating Persistent XSS often requires sanitizing and validating user input and implementing strict output encoding. Reflected XSS can be mitigated with proper input validation, output encoding, and implementing mechanisms like Content Security Policy (CSP) to restrict script execution.



Why do we have to send this Header?

The True-Client-IP  header is similar to the X-Forwarded-For header, both tell the server or proxy what the IP of the client is. Due to there being no sanitation in the header we are able to perform an XSS attack. 

URL modified replacing order id with our iframe XSS 
<img src="https://github.com/user-attachments/assets/f2632f52-1dbe-424e-bce6-cdaf1093cca9">


Why does this work?

The server will have a lookup table or database (depending on the type of server) for each tracking ID. As the 'id' parameter is not sanitised before it is sent to the server, we are able to perform an XSS attack.  





    
