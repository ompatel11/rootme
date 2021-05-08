export $IP = 

>  Scan the machine, how many ports are open? 
2

> What version of Apache is running?
2.4.29

> What service is running on port 22?
ssh

> What is the hidden directory?
/panel/

> Getting a shell 
<p>
Since from the nmap scan we can see that the server is running php we can exploit it by a php script.<code>PHPSESSID:httponly flag not set</code>
</p>
<p> But the website has a file extension filter so .php files won't be uploaded to the server, so change the extension of the exploit file to <code>.phtml</code> 
</p>

<p> Now we have the shell </p>

> User flag:
<code> THM{y0u_g0t_a_sh3ll} </code>


> Privelege Escalation 
<p>After running linpeas on the target machine, you can see that <code><b>/usr/bin/python </b></code>  is a SSUID binary so normal user can run python script as a root</p>
<code> python -c 'import os; os.execl("/bin/sh", "sh", "-p")' </code>

<p> And now you have a root shell </p>

> Root Flag:
<code> THM{pr1v1l3g3_3sc4l4t10n} </code>