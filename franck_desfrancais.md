## Exercice 1. Commandes de base 

#### Commencez par mettre à jour votre système avec les commandes vues dans le cours. 

`sudo apt upgrade` <br>
`sudo apt update`


#### 1. Quels sont les 5 derniers paquets installés sur votre machine? 



#### 2. Utiliser `dpkg` et `apt` pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !). Comment explique-t-on la (petite) différence de comptage?

avec `dpkg` il faut utiliser la commande : <br>
`sudo dpkg-query -f '${binary:Package}\n' -W | wc -l`

#### 3. Combien de paquets sont disponibles en téléchargement? 

`/usr/lib/update-notifier/apt-check --human-readable`

Output :<br>
`0 updates can be installed immediately.
0 of these updates are security updates.`

Il y a donc 0 mises à jours disponibles.

#### 4. Créer un alias “maj” qui met à jour le système

Ouvrir le fichier .bashrc dans le dossier personnel. trouver la ligne "some more ls aliases" ajouter : 
```
#some more aliases
alias maj='sudo apt upgrade && sudo apt update'
```

#### 5. A quoi sert le paquet fortunes? Installez-le. 

#### 6. Quels paquets proposent de jouer au sudoku? 

#### 7. Lister les derniers paquets installés explicitement avec la commande apt install
