# Database-Security - Pentest Project

In this lab, myself and two other teams were tasks with conducting a pentest on a system in a virtual lab environment. In this project we learned how to breach a MySQL database using Metasploit. We also got an understanding of the process of brute-forcing logins, extracting password hashes, and enumerating database users.

## Task 1: Nmap scan of the server
In task 1 we needed to scan the target using nmap. In this project it was an ecommerce server. 

![image](https://github.com/user-attachments/assets/a771e8d9-2523-4e16-9aa2-630d7d3e648a)

After running “nmap 192.168.1.220 -sV”, we noticed port 3306 for mysql was open. Tag “sV” specifies the open ports on the server.

## Task 2: Brute-Forcing logins

In task 2 we needed to brute force the MySQL logins. Howevor, for project and learning purposes we were already given the logins (username: root password: root) and simulate a brute force attack. 

![image](https://github.com/user-attachments/assets/5ff424bd-6d7d-4c33-a654-30db147c99e5)

Since we already had the login information, we created a password list file with that information to run against the sql server. We did this to act as if we did not already have the information and needed to run a full password list. This validated that “root” “root” was the login. 

## Task 3: Obtaining MySQL version

In task 3 we need to find the MySQL version in order to decide which exploit to use. 

![image](https://github.com/user-attachments/assets/28e49b25-b0bb-4f32-afaf-fd2a6ceb0504)

In the picture above you can see that we found the version to be MySQL 5.5.62-0ubuntu0.14.04.1

## Task 4: Enumerating MySQL Users

In task 4 we needed to find the right exploit to use based on the MySQL version. We used "search MySQL" to find the the right exploit to enumerate the users. We used the "mysql_enum" within metasploit. 

![image](https://github.com/user-attachments/assets/4cb8a3e8-be95-49c3-ba68-149fcb478246)

![image](https://github.com/user-attachments/assets/23cb9063-75ce-4f83-82e0-0a818815d3d3)

The MySql users that we extracted were “root”, “john”, and “debian-sys-maint”. Root and John were not restricted by source as pictured above.

## Task 5: Dump password hashes of MySQL Users

In task 5 we needed to dump password hashes for the users above. To do this, we used the "mysql_hashdump" exploit. 

![image](https://github.com/user-attachments/assets/5984bf6f-ac0f-4ac2-9c35-2d575fca9d0d)

As you can see in the image above, we got hash strings for root, debian-sys-maint, and john. 

# Task 6: Dump database schema

In task 6 we needed to dump the database schema to finally complete the pentest project. To accomplish this we used the "mysql_schemadump" exploit. 

![image](https://github.com/user-attachments/assets/2602496f-f51a-4add-b5a8-ec9f2fc7d15c)

![image](https://github.com/user-attachments/assets/16e844bc-3ebf-4733-9994-b74f03401753)

While you may not be able to see it from the picture above, we counted a total of 47 tables within the ecommerce server. 

## Tools Used
 - Nmap
 - Metasploit
 - Kali
 - SQL
 - ProxMox VM




