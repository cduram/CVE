# CVE-2023-39144

## Background
I discovered this vulnerability in May of 2023. Element55 produces software for law offices to track time. This software pulls information from various locations, such as Exchange, SQL, and Shoretel.

## Timeline

- May 24, 2023 - Reported vulnerability to Element 55
- May 25, 2023 - Element55 confirmed the vulnerability and said they would be fixing as part of version 22. (They were professional and great to work with)
- July 24, 2023 - Confirmed with Element 55 that is had been fixed.


## Vulnerability Description

The Element55 Maketime Appliance stores passwords in cleartext within the application. This can be 
seen by navigating to admin pages for Exchange, LDAP, SQL, and Shortel. Passwords that have been 
submitted to Maketime within these pages are obfuscated with asterisks. However, when viewing the 
HTML source the passwords are visible in plain text. While by itself this doesn't qualify as 
critical, it's not unusual for users to make a service account a Domain Administrator, and Exchange 
service accounts by themselves are often unnecessarily over-provisioned, meaning that if someone 
does gain access to them, they can escalate their privileges within a network. Finally, passwords 
that are chosen for web consoles are often weak and guessable, such as admin:admin.

## Location of vulnerable HTML tags

LDAP:
```
<input type=password name="settings[ldap_password]" value="password" size=20>
```
Exchange:
```
<input type=password name="settings[exchange_password]" value="password" size=20>
```

SQL:
```
<input type=password name="settings[ms_password]" value="password" size=20>
```

Shoretel:
```
<input type=password name="settings[password]" value="password" size=20>
```


## Vulnerable Versions
21 and older.

## Fixed Version
22

## References
[Element55](https://www.element55.com/), [Element55 MakeTime](http://getmaketime.com/), [CWE-312](https://cwe.mitre.org/data/definitions/312.html)
