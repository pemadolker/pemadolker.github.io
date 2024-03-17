---
Title: SWS101
categories: [SWS101,journal]
tags: [SWS101]
---

## Topic : Going through tier 0 and 1 of hack the box.

### Tier 0
We must be on the same network as the target machine in order to attack it so we connected to openvpn to get into the system so i first downloaded the access file given on the page changing the server to the nearest one and then went to terminal and started it.   
#### What we are expected to learn from tier 0.
Learn the basics skills in cybersecurity pen-testing and understand how to connect to different services like FTP, SMB, Telnet, Rsync, and RDP without actually revealing the identity. Learn about a tool-Nmap that helps to find open ports on target systems so one could assess their vulnerabilities. Tier 0 is to set a strong fundation for cybersecurity journey. Key points:
- Learn how to connect FTP, SMB, Telnet, Rsync and RDP anonymously.
- Learn how to use Nmap to identify open ports.
- Learn how to connect to a MongoDB server.

#### Tier 0 have 8 machines out of which 4 are for free and 4 are VIP. Here's what I learnt and did in each machines;

1. Meow 
- Nmap is a powerful network scanning tool for finding open ports on a target and ping the target to test the connnection . With root as username I was able to login into the target over telnet with a blank password. Then obtained root flag which serves as evidence of successful exploitation and is often used to verify completion of a challenge or test.

\\pic of commands i learned frome each machine 

2. Fawn 
- File Transfer Protocol(FTP) services usually listens on port 21. SFTP stands for "Secure File Transfer Protocol" which is a network protocol used for secure file transfer over a secure shell (SSH) connection. By using Nmap we could know what version is FTP running on the target and what OS type is running on the target. To login into FTP without having account, we use anonymous username. We get 230 as a response code in FTP when login is successful and get is the command used to download a file on FTP server. Get the root flag and submit it .

3. Dancing
- SMB use port 445 to operate and -L flag is used with the smbclient utility to list the available shares on the machine. There were 4 shares on the machine where we were able to access a share called WorkShares with a blank password. We then use get command and retrieve the root flag.

4. Redeemer
- 6379 TCP port was open on the machine and the service running on the port was redis which is an open-source, in-memory data structure store that can be used as a database, cache, and message broker. We use the command line 'redis-cli', '-h', 'info' to interact with the redis server, specify the host name, to obtain the information and statistics about the redis server respectively.Then we used basic command used in databases to fetch the root flag.


#### What I have learnt from tier 0.
In Tier 0 of cybersecurity pen-testing, the focus is on learning fundamental skills such as connecting to various services anonymously (FTP, SMB, Telnet, Rsync, RDP), using Nmap for port scanning, and connecting to MongoDB servers. Key learnings include understanding the protocols and commands used in these services to identify vulnerabilities and retrieve sensitive information, exemplified by exploiting Telnet on Meow, FTP on Fawn, SMB on Dancing, and Redis on Redeemer to retrieve root flags. This tier establishes a strong foundation for further cybersecurity exploration and learning.

### Tier 1
For tier 1, we followed the same steps as we connected for tier 0.
#### What we are expected to learn from tier 1.
In this tier of cybersecurity training, we learn pen-testing in depth like finding security weakness in systems. Learn about SQL injection which tricks a website's database into revealing information, and Server Side Template Injection, which lets you manipulate how a website looks and behaves. Also we are expected to know about Remote File Inclusion, a method for inserting malicious files into a website, and use Web/Reverse Shells for gaining control over a web server. These are all important skills for understanding and exploiting vulnerabilities in web services.

We are expected to learn to use Jenkins, a tool for automating tasks in software development, to log in and upload a special type of script called a Groovy Shell Script which allows you to remotely perform commands on a server, which is helpful for pen-testing and learn how to upload files to an S3 Bucket, which is a type of storage on Amazon Web Services. This tier give a broad range of abilities to thrive in the field of cybersecurity. Key points;

- Learn basic web exploitation techniques such as SQL injection, Server Side Template Injection, Remote File Inclusion and how to use Web/Reverse Shells.
- Use the services showcased in the previous tier for exploitation.
- Learn how to login to Jenkins and upload a Groovy Shell Script.
- Learn how to upload files to an S3 Bucket.

#### Tier 1 have 10 machines out of which only 5 are for free. Here's what I learnt and did in each machines;

1. Appointment
- SQL injection is one of the most common type of SQL vulnerabilities and Apache httpd 2.4.38 ((Debian)) was the service and version running on the port 80 of the target. The standard port used for the HTTPS protocol is 443 and we call folder a directory in web-application terminology. 404 is the response code given by HTTP for 'Not Found' errors.Gobuster is one tool used to brute force directories on a webserver and we use dir switch to specify that we are looking for directories.

2. Sequel
- During the scan, port 3306 was found to serve MySQL, running MariaDB, and the -u switch was used to specify a login username, revealing that the "root" user allows login without a password; in SQL, the symbol * indicates displaying everything within a table and queries are ended with ";", while the unique database "htb" was discovered; switching to the "htb" database, tables were listed, and a select command was executed to show everything from both tables, leading to the root flag.

3. Crocodile
- We used Nmap command and found that vsftpd 3.0.3 was runnning on port 21. Anonymous FTP login was allowed as FTP code 230 was returned and we use anonymous as username to login anonymously.Admin is a higher-privilege sounding usernames in 'allowed userlist'. The target host was running on Apache httpd 2.4.41 and we used -x is the switch with Gobuster to specify we are looking for specific filetypes. Login.php provide the opportunity to authenticate to the web service.

4. Responder
When visiting the web service using IP address, we were redirected to unika.htb and the server used the php scripting language to generate webpages.Page is the URL parameter which is used to load different language versions of the webpage. To specify the network interfacein the Responder utility, we use '-l' flag. The tool "John the Ripper" is renowned for its capability to take NetNTLMv2 challenge/response pairs and systematically test millions of passwords to determine if any of them produce the same response.
Then we got the password for the administrator user and checked which TCP port the responder machine was listening on i.e port 5985.

5. Three
- There are 2 open TCP ports on the target machine and found the domain of the email address listed in the "Contact" section as thetoppers.htb. Recognizing the absence of a DNS server,  /etc/hosts file on Linux could be used to resolve hostnames to IP addresses. Further enumeration led to the discovery of the s3.thetoppers.htb sub-domain and found the service running was Amazon S3, and learned to interact with it using the AWS CLI and high-level s3 commands. After configuring the AWS CLI using aws configure, you used aws s3 ls to list all S3 buckets and found the server was configured to run files written in PHP. Leveraging the ability to upload files to the S3 bucket, uploaded a PHP webshell, confirmed the upload, and accessed it to discover the root flag. 

#### What I have learnt from tier 1.
In Tier 1 of cybersecurity training, the focus is on deepening penetration testing skills, including exploiting vulnerabilities like SQL injection, Server Side Template Injection, Remote File Inclusion, and using Web/Reverse Shells. Key learnings include understanding and exploiting web services, logging in and uploading Groovy Shell Scripts via Jenkins, and uploading files to S3 Buckets on Amazon Web Services.