# TP 1  - Installation d’Ubuntu Server et prise en main du shell

## Exercice 2

### Manuel

1. `which`  permet de connaitre l'emplacement d'une commande / programme utilisable par le shell, la commande `whereis` ne se limitera pas à celui actuellement utilisée par le shell mais à tous ceux présent sur le PATH

2. `man which` puis `/options` pour rechercher options dans 

3. pour quitter le man (ou la pluspart des CLI) `q` 

4. Pour afficher la première page de la section 6 il faut taper : `man 6 intro`.



### Navigation dans l’arborescence des fichiers

1. `cd /var/log`
2. `cd ..`
3. `cd ~`
4. `cd -` (revenir a l'emplacement précédent)
5. Permission denied: (ce dossier appartient à l'utilisateur root)
6. `sudo cd /root` fonctionne car sudo permet le temps d'une commande d'avoir les privilèges root 
7. `mkdir -p ~/dossier1 ~/dossier2/dossier2.1 ~/dossier2/dossier2.2`
    `touch ~/dossier1/Fichier1 ~/dossier2/dossier2.2/Ficher2 ~/dossier2/dossier2.2/Ficher3`

8. Seul Ficher1 est supprimer car la commande rm ne permet pas de supprimer un dossier (besoin de l'argument -d)
9. `rmdir` ou `rm -d`
10. rm: cannot remove 'dossier2': Directory not empty    
11. `rm -r Dossier2` 

### Commandes Importantes

1. Afficher l'heure : `date`, `time commande` permet de savoir le temps necessaire pour que la commande a eu besoin pour se réaliser
2. `la` est un alias de ls -a (affichage des dossiers cachés)
3. La commande ls se situe dans `/bin/ls`
4. Il n'y a pas de page de manuel concernant la commande `ll` car c'est un alias de `ls -l`*
5. `ls -f /bin`  pour n'afficher que les fichiers de /bin
6. `ls ..` afficher les dossiers / fichiers du dossier parant
7. `pwd` donne le chemin complet du dossier courant
8.  Faire 2 fois `echo 'yo' > plop`  va créer un fichier plop avec 1 fois 'yo' écrit dedans
9.  Faire 2 fois `echo 'yo' >> plop` va créer un fichier plop avec 2 fois 'yo' écrit dedans 
10. file permet de savoir le type de l'inode passé en paramètre Dossier ou fichier (Ascii, etc.)
11. `echo "Hello Toto !" > toto` `ln toto titi` les modifications sont effectuées sur les deux, lorsqu'on supprime toto, titi existe toujours (avec son contenu)
12. `ln -s titi tutu` es modifications sont effectuées sur les deux, lorsqu'on supprime titi, tutu n'est plus accessible `tutu: No such file or directory`
13. `cat /var/log/syslog`, ctrl-s permet d'interrompre le défilement, ctrl-q pour rependre
14. `head -n 5 r /var/log/syslog`, `tail -n 15 r /var/log/syslog`, `sed -n '10,15 p' /var/log/syslog`
15.  `dmesg | less` `dmesg` affiche la mémoire tampon de message du noyau. `less` affiche cela de façon lisible un "écran" a la fois, possiblité de défiler le text, etc.
16. `cat /etc/passwd` et `man /etc/passwd`
17. Affichez seulement la première colonne triée par ordre alphabétique inverse:  `cat /etc/passwd | cut  -c 1 | sort -r`
18. Comptez le nombre d'utilisateurs `cat /etc/passwd | wc -l`
19. On peut chercher le nombre de page qui ont leur descriptions  qui contiennent un elément avec la commande : man -k elem | wc -l
20. `find / -name passwd`
21. `find / -name passwd > ~/list_passwd_files.txt 2> /dev/null`
22.  `grep -r '/' -e 'alias la'`
23. `locate file` permet de trouver le chemin vers l'inode file
24. On ne voit pas le nouveau fichier avec la commande `locate` car la base de données qu'utilise locate est mis à jour que lors du démarrage ou à 7h30 si la machine est allumées 

---

## Exercice 4
3. `source ~/.bashrc` ou `. ~/.bashrc` pour recharger la configuration du terminal 
4. `PS1='\[\033[0;35m\][\A]\[\033[0m\] - \[\033[0;32m\]\u\[\033[0m\]:\[\033[0;36m\]\w\[\033[0m\]'`

**Variables** 

- \u Nom de l’utilisateur

- \h Nom de la machine (hôte)

- \d Date

- \t Heure avec les secondes

- \A Heure sans les secondes

- \w Chemin complet du dossier courant

- \[\033[0m\]    # Text Reset

**Couleurs** 
 
- \[\033[0;36m\]      # Cyan

- \[\033[0;35m\]      # Violet

- \[\033[0;32m\]      # Vert