# TP 1  - Installation d’Ubuntu Server et prise en main du shell

Ce premier TP a pour but de créer et configurer à l’aide de VirtualBox les machines virtuelles qui nous serviront durant tout
le module, d’installer de zéro un système Ubuntu Server et de prendre en main les commandes de base de l’interpréteur de
commandes ( _shell_ ).

## Évaluation

Pour chaque TP, on attend de vous un compte-rendu **sous forme de ”tutoriel” répondant aux
questions posées**. Ces compte-rendus doivent être rédigés directement sur la page GitHub du module,
dans le dossier correspondant à votre binôme(vous créerez un fichier par TP; ne rédigez pas dans la partie
”Wiki”).

Afin de ne pas perdre de temps avec la mise en forme et rester concentrés sur le **contenu** , ils seront
rédigés enMarkdown, en langage de balisage très simple d’apprentissage. Vous pourrez par exemple suivre
ce guide d’introduction pour vous familiariser avec ce langage :https://guides.github.com/features/
mastering-markdown/


## Préliminaire

La clé USB qui vous a été distribuée est formatée par le constructeur avec le système de fichiers (on verra
dans un prochain cours de quoi il s’agit) **vfat**. L’inconvénient de ce système de fichiers est qu’il ne prend
pas en charge les fichiers ayant une taille supérieure à 2G o. Il faut donc reformater la clé avec un système
moins restrictif. Afin que vous puissiez utiliser votre clé aussi bien sous Windows que sous Linux ou Mac,
on va se tourner vers NTFS.

## Exercice 1.  Installation du serveur

**Configuration de la machine virtuelle**

1. Copier le fichier d’installation d’Ubuntu Server (ubuntu-18. 10- live-server-amd64. iso, présent dans
/softwares/sync/VMs/Admin-Système ) dans /var/tmp
2. Dans VirtualBox, créez une nouvelle machine virtuelle avec les caractéristiques suivantes :
—Nom : Ubuntu-Server_[numéro_binôme] où numéro_binôme = [ETI | IRC]-numéro (par exemple :
Ubuntu-Server_ETI-12) 
—Type : Linux
—Version : Ubuntu (64  bits)
—Mémoire : 2048  Mo
—Disque dur : nouveau disque, de type VDI, d’une capacité de 10  Go, dynamiquement alloué
3. Avant de démarrer la machine, ajoutez le support USB 2. 0  (il y a parfois des problèmes avec l’USB 3. 
dans VirtualBox)
4. La machine est configurée! Démarrez-la : comme aucun système d’exploitation n’est encore installé,
une fenêtre apparaît et demande un ”disque de démarrage”. Choisissez le fichier iso copié à l’étape 1
et validez : le programme d’installation se lance.

**Installation d’Ubuntu Server**

Le processus d’installation est relativement simple grâce au nouveau programme d’installation,Subiquity.
Il vous suﬀit de suivre les instructions; la configuration attendue est la suivante :
— Connexions réseau :
—conserver celle proposée par défaut
—pas de proxy
— Disque :
—utiliser le premier choix : ”utiliser le disque entier”
— Profil utilisateur :
—pour le nom de serveur : mettre simplement ”serveur”
—mot de passe : dans le cadre des TP, n’employez pas un mot de passe trop long, car vous serez
souvent amené à le retaper; veillez aussi à ne pas l’oublier , car vous ne pourrez plus vous
connecter à votre VM!
—import d’une identité SSH : laissernon
— Modules supplémentaires : aucun


**Clonage de la VM**

Pour les TP sur les services réseau, nous aurons besoin d’une deuxième VM qui fera oﬀice de client et
communiquera avec notre serveur. Heureusement, VirtualBox propose un mécanisme de clonage de VM, ce
qui nous épargnera la configuration et l’installation de cette deuxième VM.

1. si votre VM est lancée, tapez la commande sudo poweroff pour l’éteindre proprement En théorie, seul
l’administrateur a le pouvoir d’éteindre la machine; l’utilisateur créé lors de l’installation dispose de
certains droits lui permettant de prendre temporairement le rôle d’administrateur : c’est à cela que
sert la commande sudo
2. Dans VirtualBox, faites un clic droit sur la VM et choisissez Cloner
3. Paramètres du clone :
— Nom : ”Ubuntu-Client_[ETI|IRC]-[numéro_binôme]”
— Type : clone intégral
— Instantanés : état actuel
— Politique supplémentaire MAC : Générer de nouvelles adresses MAC pour toutes les interfaces
réseau

Le clonage peut prendre quelques minutes.
### Exercice 2.  Prise en main de l’interpréteur de commandes

A tout moment, vous pouvez sortir de la VM pour revenir dans le système hôte en appuyant sur la
touche **CTRL (droite)** du clavier.

 **Manuel**

1. A l’aide du manuel, identifiez le rôle de la commande which
2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher
le termeoptiondans la page de manuel dewhich?
3. Comment quitte-t-on le manuel?
4. Chaque section du manuel a une première page, qui présente le contenu de la section. Aﬀicher la
première page de la section 6;  de quoi parle cette section?

 **Navigation dans l’arborescence des fichiers**

1. allez dans le dossier /var/log
2. remontez dans le dossier parent (/var) en utilisant un chemin relatif
3. retournez dans le dossier personnel
4. revenez au dossier précédent (/var) sans utiliser de chemin
5. essayez d’accéder au dossier /root; que se passe-t-il?
6. essayez la commande sudo cd /root; que se passe-t-il? Expliquez
7. à partir de votre dossier personnel, créez l’arborescence suivante :
8. revenez dans votre dossier personnel; à l’aide de la commande rm, essayez de supprimer Fichier1,  puis
Dossier1;  que se passe-t-il?
9. quelle commande permet de supprimer un dossier?
10. que se passe-t-il quand on applique cette commande à Dossier2? 
11. comment supprimer en une seule commande Dossier2  et son contenu?
 **Commandes importantes**

1.  Quelle commande permet d’aﬀicher l’heure? A quoi sert la commande time?
2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire
sur les fichiers commençant par un point?
3. Où se situe le programme ls?
4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande? Utilisez les com-
mandes alias ou alias pour en savoir plus sur la nature de cette commande.
5. Quelle commande permet d’aﬀicher les fichiers contenus dans le dossier /bin?
6. Que fait la commande ls ..?
7. Quelle commande donne le chemin complet du dossier courant?
8. Que fait la commande echo 'yo' > plop exécutée 2  fois?
9. Que fait la commande echo 'yo' >> plop exécutée 2  fois?
10. A quoi sert la commande file? Essayez la sur des fichiers de types différents.
11. Créez un fichier toto qui contient la chaîne Hello Toto! ; créer ensuite un lien titi vers ce fichier
avec la commande ln toto titi. Modifiez à présent le contenu de toto et aﬀichez le contenu de titi :
qu’observe-t-on? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi?
12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le
contenu de titi ; quelle conséquence pour tutu? Et inversement? Supprimez le fichier titi ; quelle
conséquence cela a-t-il sur tutu?
13. Aﬀichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et
reprendre le défilement à l’écran?
14. Aﬀichez les 5  premières lignes du fichier /var/log/syslog , puis les 15  dernières, puis seulement les
lignes 10  à 20. 
15. Que fait la commande dmesg | less?
16. Aﬀichez à l’écran le fichier /etc/passwd ; que contient-il? Quelle commande permet d’aﬀicher la page
de manuel de ce fichier?


17. Aﬀichez seulement la première colonne triée par ordre alphabétique inverse
18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seule-
ment les utilisateurs connectés)?
19. Combien de pages de manuel comportent le mot-clé conversion dans leur description?
20. A l’aide de la commande find , recherchez tous les fichiers se nommant passwd présents sur la machine
21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier
~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null
22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu
précédemment
23. Utilisez la commande locate pour trouver le fichier history.log.
24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il? Pourquoi?
**Travailler avec plusieurs shells**

On peut utiliser jusqu’à 6  shells en parallèle. Ils portent les noms **ttyX** (où X va de 1  à 6)  et sont
accessibles via **Alt + FX**

### Exercice 3.  Découverte de l’éditeur de texte nano

Nano est un éditeur de texte rudimentaire, où toutes les commandes évidemment se font au clavier.
Les raccourcis clavier les plus courants sont aﬀichés en bas de l’écran, mais sous une forme peut-être
inhabituelle :

- ^G signifie **Ctrl + G**
- M-U signifie **Alt + U**

```
Quelques raccourcis utiles :
F1  ou Ctrl + G Aﬀichage de l’aide
Ctrl + X Quitter nano / Fermer une fenêtre / Exécuter une commande
Ctrl + R Ouvrir un fichier
Ctrl + O Enregistrer sous
Ctrl + S Enregistrer
Ctrl + K Couper
Ctrl + U Coller
Ctrl + W Rechercher
Ctrl + \ Remplacer
Ctrl + C Aﬀicher des informations sur la position du curseur (numéro de ligne, de colonne)
Alt + U Annuler
Alt + E Refaire
```
1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec
nano
2. Remplacez toutes les occurrences du mot kernel par le mot noyau
3. Déplacer les 10  premières lignes à la fin du fichier
4. Annulez cette action
5. Enregistrez le fichier avant de quitter nano

### Exercice 4.  Personnalisation du shell

Le shell par défaut est plutôt austère, mais il existe de nombreux moyens de le personnaliser, en modifiant
le fichier **~/.bashrc**.

1. Commencez par créer une copie de ce fichier, que vous appellerez .bashrc_bak
2. Editez le fichier .bashrc avecnanoet décommentez la ligne force_color_prompt=yes pour activer
la couleur. Enregistrez le fichier et quitteznano.
3. Le fichier .bashrc est lu au démarrage du shell; pour le recharger, il faudrait donc se déconnecter
puis se reconnecter; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite
de commande devrait immédiatement passer en couleurs.
4. Les couleurs par défauts (surtout celle du dossier courant) ne sont pas très visibles. Dans .bashrc ,
cherchez les lignes commençant par PS1=  ; elles indiquent la mise en forme de l’invite de commande
(selon que l’on est en couleurs ou non).
Sur cette ligne, on peut distinguer un certain nombre de raccourcis :
```
\u Nom de l’utilisateur
\h Nom de la machine ( hôte )
\d Date
\t Heure avec les secondes
\A Heure sans les secondes
\w Chemin complet du dossier courant
```

Remarquez la séquence particulière :`\[\033[ 1; 32m ]\u@\h\[\033[ 00m \]`

C’est cette instruction qui indique d’aﬀiche le nom de l’utilisateur et de la machine en vert clair. Plus précisément :
- un code couleur se place entre\[\033[ et\]
- on peut remplacer\033p ar\e(ce n’est pas forcément toujours plus lisible...)
- un code couleur se termine toujours par la lettre m
- le code couleur 00  efface toute mise en forme
- on peut combiner différents attributs (couleur, souligné, clignotant, etc.) en les séparant par des
    points virgules
La page suivante vous donne les différents codes couleurs possibles :https://misc.flogisoft.com/
bash/tip_colors_and_formatting

Modifiez l’invite de commande pour qu’elle s’aﬀiche sous la forme suivante :

`[heure]-user@host:chemin_courant$`

où l’heure est aﬀichée en violet et entre crochets, et le chemin du dossier courant en cyan

### Exercice 5.  Pour les plus rapides

Faites le tutoriel sur AWK disponible ici :https://www.tutorialspoint.com/awk/index.htm

