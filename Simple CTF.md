#Simple CTF
On commence par lancer un scan nmap et gobuster. On trouve la page suivante : /simple
On voit la version cms made simple 2.2.8, on se rend donc sur exploitdb.
On éxécute le code en le mettant en python3 (mettre des paranthèses sur les prints)
On trouve le mdp hashé on qu'on met ensuite sur dcode : mdp = secret
on se connecte donc en ssh : mitch@ip_machine -p 2222
si on fait un sudo su mitch on a le chemin suivant : /usr/bin/vim
On sait donc qu'il faut exploiter vim https://gtfobins.github.io/gtfobins/vim/
Sur le site on trouve cette commande qui fonctionne :  sudo vim -c ':!/bin/sh'
Enfin on peut lire le flag final
