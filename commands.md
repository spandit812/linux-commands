1. To add group: sudo **groupadd** developers
2. To check which group particular user belongs to -> **groups** **user-name** or **id** **user-name**
3. Give **sudo** group access to the user(username) -> 
   > sudo usermod -aG **groupname** **username** 
   example: sudo usermod -aG sudo shashikant
   
4. To list groups: **getent group** OR **cat /etc/group**
5. Add user (shashikant)-> **useradd** **shashikant**
6. List added users-> 
      > cat /etc/passwd OR 
      > cut -d: -f1 /etc/passwd (Most used command)
7. **who** shows all users currently logged in via a terminal session
8. **whoami** shows current user currently operating
9. This switches your shell into the root account.--> **sudo su -**
10. Set password for the user:
      >**passwd shashikant**
11. Switch user
     > **su - shashikant**    su = switch user
                               - = loads their full environment (home folder, PATH, etc.)
12.   **useradd** does NOT create a home directory unless **-m** flag is used.
    <pre>
      > sudo mkdir /home/shashikant
      > sudo chown shashikant:shashikant /home/shashikant
      > sudo chmod 755 /home/shashikant
      **chown** → change ownership
      **developers:developers** → user:group
      **/home/developers** → the folder whose ownership you are changing
     </pre>
13. Delete group: 
      <pre> sudo groupdel groupname </pre>
            This deletes the group only if:
            * No user has this group as their primary group
            * The group exists in /etc/group
14. newgrp groupname--> this switches your current group id to the another without loging our or switching user
      
