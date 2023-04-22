# CVE-2023-30458
Exploit Title: Medicine Tracker System 1.0.- Observable Discrepancy: Username enumeration via response timing
Date: April, 22 2023
Exploit Author: William David Mathisen (d34dun1c02n)
Vendor Homepage: https://www.sourcecodester.com/php/16308/medicine-tracker-system-php-oop-and-mysql-db-source-code-free-download.html
Software Link: https://www.sourcecodester.com/download-code?nid=16308&title=Medicine+Tracker+System+in+PHP+%28OOP%29+and+MySQL+DB+Source+Code+Free+Download
Version: v1.0
Tested on: Kali Linux, XAMPP, Mysql
CVE : 2023-30458
Exploit Description:
A username enumeration issue was discovered in Medicine Tracker System 1.0. The login functionality allows a malicious user to guess a valid username due to a different response time from invalid usernames.

Manual Attack Vector
Manual attack path: Url: http://localhost/php-mts/app/login.php

1. With Burp running, submit an invalid username and password, then send the POST /php-mts/app/login.php request to Burp Repeater.

2. Notice that when the username is invalid, the response time is roughly the same. However, when you enter a valid username, the response time is increased depending on the length of the password you entered.

3. Send this request to Burp Intruder and select the attack type to sniper. Clear the default payload positions and select the username position.

4. From the payloads tab select "add from list" usernames and manually add a username into the list that you know is legitimate (mcooper, etc). Select start attack.

5. When the attack finishes, at the top of the dialog, click Columns and select the Response received and Response completed options. These two columns are now displayed in the results table.

6. Notice that the valid username takes significantly longer than the others.
