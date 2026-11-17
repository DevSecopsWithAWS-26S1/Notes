#### User management:

* User creation 
* Password creation to the user 
* AWS server default comes with keybased . Default user ec2-user

* adduser <username>
* passwd <username>


* To make server authentication available with password :
    1. vi /etc/ssh/sshd_config 
    2. Shift + G
    3. Change ```PasswordAuthentication no`` >> ```PasswordAuthentication yes```
    4. sudo systemctl restart ssh 
    5. change ```PubkeyAuthentication no``` >> ```PubkeyAuthentication yes```
    6. There are some default configs in the folder -/etc/ssh/sshd_config.d/ . We renmaed them as .bak and restart the sshd 
    7. change ```UsePAM no``` >> ```UsePAM yes```  
        * UsePAM takes acre of user password verification 
    8. There are some default configs in the folder -/etc/ssh/sshd_config.d/ . We renmaed them as .bak and restart the sshd 
    9. sudo systemctl restart sshd 



* Use mobaxterm for better UI and management of servers :
    ```
    winget install -e --id Mobatek.MobaXterm
    ```

* User deletion along with home directory :
    ```
    sudo userdel -r username 
    ```

* Only user deletion , doent delete home directory :
    ```
    sudo userdel  username
    ```

* group creation:
    ```
    groupadd <groupname>
    ```
* add users to the group 
    ```
    sudo usermod -aG <groupname> <username>
    ```
* List user groups :
    ```
    groups <username>
    ```
* Add a primary group to the user 
    ```
    sudo usermod -g <groupname> <username>

    ```

* Remove users from the group :
    ```
    sudo gpasswd -d <username> <groupname>
    ```
* You cant delete a user from all groups , the user should be part of atleat one group 

* List groups :
    ```
    getent group
    cat /etc/group
    ```

### Scenario : New person joined . you have a provide access to a server 
1. Ask the user to generate keys on his laptop
    ```
    ssh-keygen
    ```
2. Ask user to shar the pubkey 
3. On Server Create a user wihth username, create a folder .ssh , create a file authorized_keys , copy the pubkey and paste in authorized_keys
    ```
    adduser krishna
    mkdir .ssh
    vi authorized_keys
    ```
    
* How to give root access to a user :
    ```
    sudo usermod -aG wheel <username>
    ```
* visudo - opens sudoers file 
    * search for this line ```%wheel  ALL=(ALL)       ALL ```
    * add this line below to above line 
    ```
    krishna  ALL=(ALL)       NOPASWD: ALL
    ```
 


