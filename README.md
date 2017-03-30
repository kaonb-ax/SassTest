# SASS pour : Syntactically Awesome Style Sheets  

SASS([site officiel](http://sass-lang.com/guide)) est un langage de feuilles de style en cascade (CSS) qui sera compilé pour obtenir du CSS.  

Permet principalement d'utiliser des variables, permet facilement l'import de fichiers scss dans d'autres fichiers scss et  donc découper et organiser ces styles en plusieurs fichiers qui au final produiront un seul fichier.

Le résultat peut également être compressé en passant une option à la ligne de commande, la plus efficace état compressed  
option possible de compression : nested (default), compact, compressed, ou expanded  
 exemple :  
̀```
sass --watch chemin_fichiers_scss chemin_fichiers_css --style compressed
̀̀```

- Comparaison du code SASS / SCSS   

La syntaxe originale , nommée « syntaxe indentée », vous pourrez donc croisé des fichiers avec l'extension .sass, qui est l'ancien format. La nouvelle syntaxe se nomme « SCSS » avec l'extension .scss. Elle a un formalisme proche de CSS(avec les accolades).  

La différence : l'indentation pour le SASS et les accolades pour SCSS  
![Sass Vs Scss Vs CSS](sass-vs-scss.png)  

- Installation:
```
sudo apt install ruby
```

- Puis:  
```
sudo gem install sass
```
Vous trouverez dans ce dépot un exemple de projet SASS:  

- Créer un répertoire assets/scss et assets/css  

! Ne créez rien dans assets/css ! c'est la commande sass que vous avez installé plus haut qui va créer les fichiers css automatiquement pour vous à partir du code scss que vous allez mettre dans vos fichiers scss :  

Essayez les styles ci-dessous :  

Tous ces fichiers SCSS seront au final réunis en un seul lors de l'éxécution de la commande sass :  
Nous allons créer plusieurs feuilles de style partiales :  
[Exemple de répertoire SCSS](https://github.com/MyClientisRich/WPbaseTheme/tree/master/scss)  
- Utilisation de variables :
Créer un fichier assets/scss/variables.scss est mettre dedans :    
```
$fond: #222;
$texte: #AAA;

$base_color: #48A3E9;
```

- Nesting ( traduction : Nidification?? par rapport à la structure )  
```
ul {  
    padding: 0;
    li {
        list-style: none;
        a {
            color: blue;
            &:hover {
                color: lime;
            }
        }
    }
}
```

- Compiler et Tester vos fichiers SCSS et linkez le app.css obtenu sur votre index.html  

- Inheritance ( Héritage )   
```
%box {
    margin: 2px;
    border: 1px solid black;
}

.greenBox {
    @extend %box;
    border-color: lime;
}

.greenBoxBlueBackground {
    @extend .greenBox;
    background-color: blue;
}
```

Créez un héritage %box, vous pouvez l'utiliser ensuite avec le mot clef @extend dans vos autres classes pour ajouter ces propriétés.

@mixin box($bg-color) {
    background-color: $bg-color;
    // this is a predefined sass-function
    color: complement($bg-color);
}

--
$color: red;

@mixin my-border($color) {
  border: 1px solid $color;
}

body {
  background: $color;
  @include my-border(green);
}

- Les fonctions :  
Comme Darken et Lighten() qui permettent d'assombrir ou d'éclaircir une couleur.  
