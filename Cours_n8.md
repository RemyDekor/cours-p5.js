# **Creative coding avec p5.js : (cours #7)**

### Objectifs de la séance :

- Créer une fonction : la définir et l'exécuter (ou "l'appeler")
- Ajouter des paramètres (ou "arguments") à cette fonction

# ----------------------- Let's code ---------------------------

# Créer sa propre fonction :

Nous utilisons des fonctions depuis le début de l'année dans ce cours. Mais qu'est-ce qu'une fonction, précisément ?

Wikiversity (Wikipédia) nous dit :
"Une fonction désigne un « sous-programme » permettant d'effectuer des opérations répétitives. Au lieu d'écrire le code complet autant de fois que nécessaire, on crée une fonction que l’on appellera pour l'exécuter, ce qui peut aussi alléger le code, le rendre plus lisible."

Pour simplifier, on peut dire qu'une fonction permet d'executer toute une liste d'instructions (de lignes de code), sans devoir recopier celles-ci.

Cela signfie que les fonctions comme `ellipse()` ou `fill()` sont juste une suite d'instructions plus complexes, dont nous n'avons pas besoin de nous préoccuper pour travailler avec.  
C'est un cas d'application du concept d'**abstraction** en programmation.

Pour créer et utiliser sa propre fonction, il faut la **définir** et l'**exécuter**.

## Définir une fonction en javascript :

Une fonction se définit de plusieurs manière en javascript, mais la manière la plus classique est celle-ci :

```
function maFonction() {
    // instructions de mon choix
    // ...
}
```

## Exécuter (ou appeler) une fonction en javascript :

A un autre endroit dans le code, où la fonction est connue (dans le même scope), on peut écrire ceci pour appeler notre fonction :

```
maFonction();
```

## Ajouter de l'intelligence à ma fonction avec des paramètres (ou arguments) :

Il est primodial d'ajouter des arguments à ses fonctions dans certains cas (assez souvent en fait !!). Un argument est une variable que l'on va "passer" à la fonction lorsqu'on l'execute.  
Par exemple, lorsque j'écris "`ellipse(200, 100, 50)`", j'appelle la fonction `ellipse()` avec **3 arguments** : une coordonnée en x de 200, en y de 100, et un rayon de 50.

## Définir une fonction avec des arguments :

Pour donner des paramètres (ou arguments) à notre définition de fonction, il faut procéder comme ceci :

```
// avec un seul argument :

function maFonction(monArgument) {
    // instructions utilisant monArgument
    // ...
}
```

```
// avec plusieurs arguments :

function autreFonction(arg1, arg2, arg3, arg4) {
    // instructions utilisant tous les arguments arg1, arg2, arg3, arg4
    // ...
}
```

## Exécuter (ou appeler) une fonction avec des arguments :

Cela sous-entend que l'on exécute notre fonction avec autant d'arguments que dans la définition, tout le temps, comme ci-dessous :

```
maFonction(50); // ici on passe la valeur 50 pour l'argument "monArgument"

maFonction(maVariable); // ici on passe la valeur de maVariable

autreFonction(50, 30, 100, 100);  // etc...
```

## Exemple de fonction personnalisée :

Vous pouvez copier ce code dans l'éditeur de p5.js :

```
function setup() {
 createCanvas(500, 400);
}

function draw() {
 background(220);

 // appeler la fonction plusieurs fois avec une boucle, en modifiant les arguments passés à chaque fois
 for (let i =0; i < 4; i++) {
 	mickey((0.5+i)*120, height*0.7, 70, i/4);
 }

 // appeler la fonction avec des variables interactives (mouseX et mouseY)
 mickey(200, mouseY, 100, mouseX/width);
}


// La définition de la fonction :
function mickey(posX, posY, size, happiness) {
 // La valeur de happiness doit être comprise entre 0 et 1 (comme un pourcentage)
 happiness = Math.min(1, happiness);
happiness = Math.max(0, happiness);
 push();

 noStroke();
 translate(posX, posY);

 // visage
 fill(0);
 ellipse(0, 0, size, size*0.95);
 // oreilles
 ellipse(+size / 2, -size / 2, size * 0.6);
 ellipse(-size / 2, -size / 2, size * 0.6);
 // yeux
 let eyesHeight = size * 0.44 + happiness *11;
 fill(255);
 ellipse(+size / 7, -size *0.13, size * 0.35, eyesHeight);
 ellipse(-size / 7, -size *0.13, size * 0.35, eyesHeight);
 fill(0);
 ellipse(+size / 8, -size / 8, size * 0.15, size * 0.2);
 ellipse(-size / 8, -size / 8, size * 0.15, size * 0.2);
 // museau
 fill(0);
 ellipse(0, size * 0.15, size * 0.8, size * 0.3);
 fill(255);
 ellipse(0, size * 0.22, size * 0.8, size * 0.4);
 // bouche
 let mouthWidth = size * 0.1+happiness*20;
 fill(0);
 ellipse(0, size * 0.2, mouthWidth, size * 0.25);
 fill(255);
 ellipse(0, size * 0.15, size * 0.5, size * 0.25);
 // nez
 fill(0);
 ellipse(0, size * 0.1, size * 0.2, size * 0.15);

 pop();
}
```

# Exercice à finir pendant ce cours :

Voici le code dont vous pouvez partir pour l'exercice à rendre :
https://editor.p5js.org/RemyDekor/sketches/RNHrpF5Sn

Il faut :

- Mettre le code qui permet de dessiner le pendule dans une fonction,
- Utiliser cette fonction dans une boucle for(), elle même dans la fonction draw(), afin de dessiner plusieurs pendules,
- Modifier la fonction pour dessiner le pendule en lui ajoutant des arguments (par exemple la position en x et y où on veut dessiner le pendule, et le temps)
- faire varier les arguments afin de dessiner des pendules différents, toujours en étant dans la boucle for()

Je vous conseille de partir du code ci-dessus, pour plus de simplicité.
Si vous voulez jouer avec l'exemple vu en cours, ou bien pousser votre propre code, vous pouvez vous inspirer de ceci :
https://editor.p5js.org/RemyDekor/sketches/ztQLIUT3w

# Exercice pour la prochaine fois :

- En utilisant **un ou plusieurs vecteurs** (avec un angle et une magnitude), créez une fonction de votre choix qui dessinera quelque chose (exemples: une spirale, un groupe de points, un objet figuratif, un arbre, un motif, etc.). Utilisez les cours précédents si besoin.
- Vous devrez appeler cette fonction en lui passant une variable interactive (par exemple les positions en X et Y de la souris) et produire un changement dans la forme dessinée.
