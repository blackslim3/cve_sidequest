## Vulnerability Details

**Credits**:
  > Paul Rivera: (https://github.com/blackslim3)<br/>

**Tested On**:
  > Hostel Management System using PHP and MySQL 1.0 : https://github.com/Surya2Developer/Hostel_Management_System/

**Affected Version**:
  > Hostel Management System using PHP and MySQL 1.0

**Affected Site Page**:
  > /check_availability.php

**Affected Code**:
  > check_availability.php

**Related CWE**:
  > CWE-203: Observable Discrepancy: https://cwe.mitre.org/data/definitions/203.html

## **Details**:
  > An unauthenticated attacker can enumerate valid passwords and usernames through different HTTP response. When a POST request is sent with valid password as a value to the `oldpassword` parameter:

![image](https://github.com/blackslim3/cve_sidequest/blob/main/poc/assets/password_enumeration_REQUEST(1).png)  

  > The server will contains "Password Matched" on its response or "Password Not Matched" if the oldpassword value is invalid.

![image](https://github.com/blackslim3/cve_sidequest/blob/main/poc/assets/password_enumeration_RESPONSE(2).png)  


## **Vulnerability Impact**:
    Allows an unauthenticated attacker to enumerate valid usernames/email addresses and passwords through observing discrepancies in HTTP responses from the server. 
    
