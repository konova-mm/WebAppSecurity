## Cross Site Scripting (XSS) 
``` Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it. ```


### Web For Pentester ( XSS ) Walkthrough
### Example 1
``` There is no input validation, so, can exploit it directly with the classic “alert(1)” injection. ```
### Payload - <script>alert(1)</script>
