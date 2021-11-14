# Exercice - Script bash


## Exercices pas-à-pas


1- Nous allons d'abord faire un script  bash qui va nous permettre de vérifier l'espace disque.


- Pour ce faire créer le script bash suivant à la racine de votre répertoire usage: 
```bash
$nano espace.sh
```


Nous donnons ici l'extension  .sh au fichier. On le fait par convention pour indiquer que c'est un script shell, mais ce n'est pas une obligation. Nous aurions pu appeler le script toto, et ce sans extension.


```bash
#!/bin/bash
Fichier="espaceDisque.txt"



date >> $Fichier
df -H | grep /dev/sda >> $Fichier


cat $Fichier
```
- Sauvegardez votre fichier en tapant sur Crtl+X et répondez Yes
- Faite la commande suivante pour rendre le script bash exécutable : 





```bash
$chmod u+x espace.sh
#Vérifier les droits d'exécution sur le fichier :
$ls -l
# et pour exécuter votre script bash :
./espace.sh
```
Question : Qu'est-ce qui arrive si vous exécutez plusieurs fois le script ?




**read : demander une saisie**


Vous pouvez demander à l'utilisateur de saisir du texte avec la commanderead. Ce texte sera immédiatement stocké dans une variable.
La commande read propose plusieurs options intéressantes. La façon la plus simple de l'utiliser est d'indiquer le nom de la variable dans laquelle le message saisi sera stocké :
```bash
read nomvariable
```
Créons un script bonjour.sh pour qu'il nous demande notre nom puis qu’il nous l'affiche :
```bash
#!/bin/bash


read nom
echo "Bonjour $nom !"
```
Lorsque vous lancez ce script, rien ne s'affiche, mais si vous tapez du texte (votre nom, par exemple) le résultat va s'afficher.


On peut demander de saisir autant de variables d'affilée que l'on souhaite. Voici un exemple de ce qu'il est possible de faire :


```bash
#!/bin/bash


read nom prenom
echo "Bonjour $nom $prenom !"
```


On est d'accord, ça manque d'informatique c'est ce que vas permettre l'option -p : afficher un message de prompt : 
```bash
#!/bin/bash


read -p 'Entrez votre nom : " nom 
echo "Bonjour $nom !"
```


**Exécution de débogage**


Plus tard, vous ferez probablement de gros scripts et risquerez de rencontrer des bugs. Il faut donc dès à présent que vous sachiez comment déboguer un script.


Il faut l'exécuter comme ceci :


```bash
$bash -x espace.sh
```
On appelle en fait directement le programme bash et on lui ajoute en paramètre un -x (pour lancer le mode débogage) ainsi que le nom de notre script à déboguer.


Le shell affiche alors le détail de l'exécution de notre script, ce qui peut nous aider à retrouver la cause de nos erreurs.



## A vous de jouer, réaliser les scripts suivants


**Attention : n'oubliez pas de donner les droits d'exécution sur les script 
(chmod a+x)**


1- De quelle manière peut-on écrire un code qui permette d'afficher à l'écran : 


    Bonjour à tous, je m'appelle {Votre prénom}


     Je me pratique pour bash




2- Quelle est la commande à taper pour demander à l'utilisateur de rentrer 
son nom et de le stocker dans la variable NAME ?




3- Quelle est la commande à taper pour afficher à l'écran : "Bonjour NOM, tu 
as AGE ans." en remplaçant NOM et AGE par les valeurs entrées par l'utilisateur 
?




4- Réalisation un compteur qui commencer au chiffre rentré par l'utilisateur 
et qui descend jusqu'à 1.




6- Crer un jeu qui permet à l'utilisateur de deviner un chiffre généré par le 
script entre 1 et 50. À chaque fois que l'utilisateur entre un chiffre, le 
script lui indique si le chiffre à trouver est supérieur ou inférieur à celui 
qu'il a entré, etc.




7- Réaliser un script bash qui permet de vérifier si l'utilisateur a bien 
saisi des arguments, et si les fichiers placés en arguments existent bien.




8- Réaliser un script faisant appel à une fonction qui prend comme paramètre 
un login d'un user et vérifie si l'utilisateur existe déjà.




**Fin de l'exercice**

