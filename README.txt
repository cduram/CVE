**Description**:

The Element55 Maketime Appliance stores passwords in cleartext within the application. This can be 
seen by navigating to admin pages for Exchange, LDAP, SQL, and Shortel. Passwords that have been 
submitted to Maketime within these pages are obfuscated with asterisks. However, when viewing the 
HTML source the passwords are visible in plain text. While by itself this doesn't qualify as 
critical, it's not unusual for users to make a service account a Domain Administrator, and Exchange 
service accounts by themselves are often unnecessarily over-provisioned, meaning that if someone 
does gain access to them, they can escalate their privileges within a network. Finally, passwords 
that are chosen for web consoles are often weak and guessable, such as admin:admin.

**HTML Tag Locations**:
LDAP:
<input type=password name="settings[ldap_password]" value="password" size=20>

Exchange:
<input type=password name="settings[exchange_password]" value="password" size=20>

SQL:
<input type=password name="settings[ms_password]" value="password" size=20>

Shoretel:
<input type=password name="settings[password]" value="password" size=20>

**Fixed Version**:
22

**Vulnerable Versions**:
21 and older.

**References**:
http://getmaketime.com/
https://cwe.mitre.org/data/definitions/312.html
