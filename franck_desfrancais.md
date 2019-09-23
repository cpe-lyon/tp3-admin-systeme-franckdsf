## Exercice 1. Commandes de base 

#### Commencez par mettre à jour votre système avec les commandes vues dans le cours. 

`sudo apt upgrade` <br>
`sudo apt update`


#### 1. Quels sont les 5 derniers paquets installés sur votre machine? 

`grep "installed" /var/log/dpkg.log | tail -5`

```
2019-09-23 13:56:33 status installed dictionaries-common:all 1.28.1
2019-09-23 13:56:33 status installed libgdk-pixbuf2.0-0:amd64 2.38.1+dfsg-1
2019-09-23 13:56:33 status installed libc-bin:amd64 2.29-0ubuntu2
2019-09-23 13:56:33 status installed dbus:amd64 1.12.12-1ubuntu1.1
2019-09-23 13:56:34 status installed systemd:amd64 240-6ubuntu5.7
```

#### 2. Utiliser `dpkg` et `apt` pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !). Comment explique-t-on la (petite) différence de comptage?

avec `dpkg` il faut utiliser la commande : <br>
`sudo dpkg-query -f '${binary:Package}\n' -W | wc -l` 514

ou encore : <br>
`dpkg -l | grep "^ii" | wc -l` 1135 <br>
`apt list --installed | wc -l` 1136

#### 3. Combien de paquets sont disponibles en téléchargement? 



#### 4. Créer un alias “maj” qui met à jour le système

Ouvrir le fichier .bashrc dans le dossier personnel. trouver la ligne "some more ls aliases" ajouter : 
```
#some more aliases
alias maj='sudo apt upgrade && sudo apt update'
```

Voir s'il faut faire des mises à jour : <br>
`/usr/lib/update-notifier/apt-check --human-readable`

Output :<br>
`0 updates can be installed immediately.
0 of these updates are security updates.`

Il y a donc 0 mises à jours disponibles.

#### 5. A quoi sert le paquet fortunes? Installez-le. 

Pour savoir a quoi sert le paquet :
`apt show fortunes`<br>
Les fortunes sont de petits messages, des citations, des proverbes, etc. affichés à chaque connexion en mode console (terminal).

pour l'installer : <br>
`sudo apt install fortunes`

#### 6. Quels paquets proposent de jouer au sudoku? 

`apt-cache search sudoku` permet de trouver les paquets disponibles. <br>
gnome-sudoku par exemple
`sudo apt-get install gnome-sudoku`

#### 7. Lister les derniers paquets installés explicitement avec la commande apt install


# Exercice 2

il suffit d'ajouter cette commande à un script bash créé dans le dossier Script. On peut alors l'appeler en passant en paramêtre le nom d'une commande. <br>

`which -a $1 | xargs dpkg -S 2> /dev/null`

# Exercice 3

`(dpkg -l <nom-du-paquet> | grep "^ii" ) && echo "installé" || echo "non installé"`

Le && est executé que si la fonction d'avant a renvoyé quelque chose. Le || est éxecuté dans le cas contraire.

# Exercice 5

Pour installer aptitude il faut entrer la commande suivante : 
`sudo apt install aptitude`
On ouvre aptitude avec `aptitude`
Puis on recherche _emacs_ et on l'installe.

# Exercice 6

On installe la version Oracle de java
```
sudo add-apt-repository ppa:linuxuprising/java
sudo apt update
sudo apt install oracle-java11-installer
```

_linuxuprising-ubuntu-java-disco.list_ est contenu dans le dossier _/etc/apt/sources.list.d_
