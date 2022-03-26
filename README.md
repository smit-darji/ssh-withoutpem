# ssh-withoutpem
1. SSH your default account using .pem

ssh -i /path_to_pem_file/you_pem_file_name.pem ur_default_user@public_ip_address 

2. Then add a new user from there

sudo adduser new_user 

3. Set a password

sudo passwd new_user 

4. Add new _user to SUDOers

    sudo visudo // this will open editor 
To edit this file, press 'insert' key

using arrows, you will see "root All=(ALL) ALL"

Hit an enter(to go to next line) and add the below line
        new_user	All=(ALL)	ALL 
press escape and then write the below command



5. Change PasswordAuthentication "yes" to "no"

sudo vi /etc/ssh/sshd_config 
Using arrows find "PasswordAuthentication yes", press "insert" key change "PasswordAuthentication yes" to "PasswordAuthentication no"

press escape and save your changes and quit the editor

cntl + x For Exit

6. Restart SSH

sudo /etc/init.d/sshd restart 
That is it!

Now you can ssh the new user without requiring pem file

ssh new_user@ur_public_ip 
enter password, and Voila!!!