#### Tommorow we will practice the following commands :

* head <filename> - Display the first 10 lines of a file
* head -n 5 <filename> - Display the first 5 lines of a file


* tail <filename> - Display the last 10 lines of a file
* tail -n 5 <filename> - Display the last 5 lines of a file

* grep <pattern> <filename> - Search for a specific pattern in a file
* grep -i <pattern> <filename> - Search for a specific pattern in a file (case-insensitive)
* grep -r <pattern> <directory> - Search for a specific pattern in all files    


* wget <url> - Download a file from the internet


* cut & awk  - these are used to extract specific columns or fields from a file or output. 

```
root:x:0:0:root:/root:/bin/bash

root x 0 0 root /root /bin/bash
1    2 3 4 5     6      7 

```

* cut OPTION... [FILE]...
* cut -d ":" -f 1 <filename>


* awk -F ":" '{print $1}' passwd 
* awk -F ":" '{print $NF}' passwd  - Print last value 
* awk -F ":" '{print $1,$6}' passwd 

* cut -d ":" -f 1,6  passwd | grep "ec2-user"
*  grep -i "Ec2-user" passwd
*  grep  "ec2-user" passwd

* shows the HTML page :
    * curl https://github.com/DevSecopsWithAWS-26S1/ExpenseTracker/blob/main/expense-backend-v2.zip

* download the file 
    * curl -o /tmp/expense.zip  https://github.com/DevSecopsWithAWS-26S1/ExpenseTracker/blob/main/expense-backend-v2.zip
    * curl -o /tmp/expense.zip  https://github.com/DevSecopsWithAWS-26S1/ExpenseTracker/blob/main/expense-backend-v2.zip



### Create a Server in AWS RHEL-9.6.0
* By default the AWS servers comes with passwordless or key based authntication 

* ssh devops@ipaddres
* ec2-user
* ssh -i "tejapem.pem" ec2-user@ipaddress
* The ec2-user will be root user , but you should use sudo before any command 
```
sudo cat /etc/ssh/sshd_config 
```

* switch to root user 
```
sudo su 
```
* Switch along with home directory of root 
```
sudo su - 
```
* /root - it is root directory which belongs to root user 

* ```NOTE``` : It is always a good practice to take a back before changing any configurations 

* /etc/passwd - This file containers the user detials in your server 



#### Security groups in AWS :
* Security groups provide you an option to restrict who can access your server and also to whom your server can access on the ports 
* Inbound  rules - incoming traffic to the server 
* Outbound rules - Takes care of outgoing traffic from the server

* SSH - 22 
* Application - 8080 

* 0.0.0.0/0 - Open to the world 