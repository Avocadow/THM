## Cyborg 
## Scan the machine, how many ports are open? 
To answer this question, we will simply do a nmap scan with this command : ""nmap -sC -sV 'machine ip'" 2 services are running on this machine : ssh (port 22) and http (port 80) 
Then, we are going to perform a gobuster scan to find hidden pages by using this command :

gobuster dir -u http://10.10.177.252/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

:tw-26a0:It's better to but extensions, in this case we didn't need them:tw-26a0: We found two pages :**/admin and /etc** 
In this website, there are some informations about a guy who loves music. In his website, we can download an archive.tar file. To extract this file we are going to use this command "tar -xvf archive.tar" Then we got a home file. If we investigate a little bit, we can found that there is a readme file who told us to have a look to **Borg Backup", Let's dowload it. 
Before, we found a passwdkey. In order to use Borg, we are going to crack it using John. **John h.txt --wordlistr/usr/share/wordlists/rockyou.txt" **The password is sguidward** 
Now that we got the password, we can use Borg with this command : 
**borg mount home/field/dev/final_archive final**

In his machine, we found his password **S3cretP@s3**, we can use it to connect with ssh.
ssh alex@ip + password
and then we got our first flag : flag{1_hop3_y0u_ke3p_th3_arch1v3s_saf3}

Now, we know that we have to get root privilege to get our final flag. In order to do that, we are going to use privilege escalations. 
First, let's use this command : sudo -l
User alex may run the following commands on ubuntu:
    (ALL : ALL) NOPASSWD: /etc/mp3backups/backup.sh

Let's nano this file. It's a bash file and the first line is !#/bin/bash
In Linux, `/bin/bash` refers to the Bash shell, which is used by users and scripts to execute commands. We will therefore replace the contents of the file with `/bin/bash`.
First, we need permissions : chmod 777 /etc/mp3backups/backup.sh
Then : echo "/bin/bash" > /etc/mp3backups/backup.sh
After doing that, our file is now edited, we can execute it and we goot our root privilege.

flag{Than5s_f0r_play1ng_H0p£_y0u_enJ053d}






