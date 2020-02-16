# TP 1  - Installation d’Ubuntu Server et prise en main du shell

## Exercice 2

### Manuel

1. `which` permet de connaître l'emplacement d'une commande / programme utilisable par le shell, la commande `whereis` ne se limitera pas à celui actuellement utilisé par le shell mais à tous ceux présents dans le PATH

2. `man which` puis `/options` pour rechercher "options" dans le manuel de `which`

3. Pour quitter le man (ou la plupart des CLI) : `q` 

4. Pour afficher la première page de la section 6 il faut taper : `man 6 intro`.



### Navigation dans l’arborescence des fichiers

1. `cd /var/log`
2. `cd ..`
3. `cd ~`
4. `cd -` (revenir à l'emplacement précédent)
5. Permission denied: (ce dossier appartient à l'utilisateur root)
6. sudo: cd: command not found: `sudo cd /root` ne fonctionne pas car `cd` est une commande built-in de bash, elle n'est pas connue de sudo 
7. `mkdir -p ~/Dossier1 ~/Dossier2/Dossier2.1 ~/Dossier2/Dossier2.2` \
   `touch ~/Dossier1/Fichier1 ~/Dossier2/Dossier2.2/Ficher2 ~/Dossier2/Dossier2.2/Ficher3`
8. Seul Ficher1 est supprimé car la commande `rm` ne permet pas de supprimer un dossier (besoin de l'argument -d)
9. `rmdir` ou `rm -d`
10. rm: cannot remove 'dossier2': Directory not empty    
11. `rm -r Dossier2` 

### Commandes importantes

1. Afficher l'heure : `date`, `time commande` permet d'obtenir le temps que `commande` a mis pour s'exécuter
2. Les fichiers commençant par un point sont cachés. `la` est un alias de ls -a (affichage des fichiers / dossiers cachés)
3. La commande ls se situe dans `/bin/ls`
4. Il n'y a pas de page de manuel concernant la commande `ll` car c'est un alias de `ls -l`
5. `ls -f /bin` pour n'afficher que les fichiers de /bin
6. `ls ..` affiche les dossiers / fichiers du dossier parent
7. `pwd` donne le chemin complet du dossier courant ("print working directory")
8.  Faire 2 fois `echo 'yo' > plop` va créer un fichier plop avec 1 fois 'yo' écrit dedans
9.  Faire 2 fois `echo 'yo' >> plop` va créer un fichier plop avec 2 fois 'yo' écrit dedans 
10. file permet de savoir le type du fichier / dossier passé en paramètre (Ascii, etc.)
11. `echo "Hello Toto !" > toto` \ `ln toto titi` les modifications sont effectuées sur les deux, lorsqu'on supprime toto, titi existe toujours (avec son contenu)
12. `ln -s titi tutu` les modifications sont effectuées sur les deux, lorsqu'on supprime titi, tutu n'est plus accessible `tutu: No such file or directory`
13. `cat /var/log/syslog`, Ctrl-S permet d'interrompre le défilement, Ctrl-Q pour rependre
14. `head -n 5 /var/log/syslog`, `tail -n 15 /var/log/syslog`, `sed -n '10,15p' /var/log/syslog`
15.  `dmesg | less` `dmesg` affiche la mémoire tampon de message du noyau. `less` affiche cela de façon plus lisible un "écran" à la fois, possiblité de défiler le texte, etc.
16. `cat /etc/passwd` il contient les différents utilisateurs et `man 5 passwd`
17. Affichez seulement la première colonne triée par ordre alphabétique inverse :  `cat /etc/passwd | cut -f 1 -d : | sort -r`
18. Comptez le nombre d'utilisateurs `cat /etc/passwd | wc -l`
19. On peut chercher le nombre de pages qui ont dans leur description un élément avec la commande : `man -k conversion | wc -l` : 35 pages avec le mot "conversion"
20. `find / -name passwd`
21. `find / -name passwd > ~/list_passwd_files.txt 2> /dev/null`
22.  `grep -r '~' -e 'alias ll'`
23. `locate file` permet de trouver le chemin vers file : history.log se trouve dans le dossier /var/log/apt
24. On ne voit pas le nouveau fichier avec la commande `locate` car la base de données qu'utilise locate n'est mise à jour que lors du démarrage ou à 7h30 si la machine est allumée

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