WordPress-Attackers
===================

Data on attacks / hack attempts of my WordPress installation.

Last updated on February 19, 2014

Get Update Notifications
------------------------

This list will change over time, randomly, therefore sign up to my newsletter to get notifications of when updates are done:

** http://himpfen.com/wordpress-login-attackers/

How-To Get IPs
--------------

Steps I used to grab data from my error_log and commands used to convert the error_log into non-duplicate IP address database.

May create a script to this, so that I don't have to do three separate commands.

Grab all occurances of wp-login.php from my error_log; I disallow access to my wp-login.php through .htaccess

grep -iR wp-login.php sites.himpfen.com-error_log >> data.txt

Grab only the IP addresses in the data.txt file, created above, and make a new file.

grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' data.txt >> ipsonly.txt

Create a new file that removes duplicate IP addresses from the text file created in step 2.

awk '!x[$0]++' ipsonly.txt > IPAddresses.txt

OR

sort -u  ipsonly.txt > IPAddresses.txt
