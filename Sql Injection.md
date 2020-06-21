## SQL Injection Attack
`` SQL injection (SQLi) is an application security weakness that allows attackers to control an application’s database – letting them access or delete data, change an application’s data-driven behavior, and do other undesirable things – by tricking the application into sending unexpected SQL commands. ``

## Types of SQL Injection (SQLi)
### In-band SQLi (Classic SQLi) - an attacker is able to use the same communication channel to both launch the attack and gather results.
``Error-based SQLi - relies on error messages thrown by the database server to obtain information about the structure of the database.``

``Union-based SQLi - leverages the UNION SQL operator to combine the results of two or more SELECT statements into a single result which is then returned as part of the HTTP response.``

### Inferential SQLi (Blind SQLi) - no data is actually transferred via the web application and the attacker would not be able to see the result of an attack in-band (which is why such attacks are commonly referred to as “blind SQL Injection attacks”)
``Blind-boolean-based SQLi - relies on sending an SQL query to the database which forces the application to return a different result depending on whether the query returns a TRUE or FALSE result.``

``Blind-time-based SQLi - relies on sending an SQL query to the database which forces the database to wait for a specified amount of time (in seconds) before responding ``

### Out-of-band SQLi -  an attacker is unable to use the same channel to launch the attack and gather results

### [Audi 1 Lab](https://github.com/Audi-1/sqli-labs)
### [Useful Link](http://index-of.es/Varios-2/Advanced%20SQL%20Injection.pdf)



### Noted by [konova](https://www.facebook.com/kon0va)

### Ref : 
- [acunetix](https://www.acunetix.com/websitesecurity/sql-injection2/)


