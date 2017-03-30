# SASS pour : Syntactically Awesome Style Sheets  

SASS([site officiel](http://sass-lang.com/guide)) est un langage de feuilles de style en cascade (CSS) qui sera compilé pour obtenir du CSS.  

Permet principalement d'utiliser des variables dans vos CSS, permet facilement l'import de fichiers scss dans d'autres fichiers scss et  donc découper et organiser ces styles en plusieurs fichiers pour travailler à plusieurs sur une application qui au final produiront un seul fichier grâce à la commande sass.

Le résultat peut également être compressé en passant une option à la ligne de commande pour avoir une feuille de style plus rapide à charger pour vos visiteurs, les plus efficace étant compressed , compact
option possible de compression : nested (default), compact, compressed, ou expanded  
 exemple pour compresser vos fichiers scss :  
̀```
sass --watch chemin_fichiers_scss:chemin_fichiers_css --style compressed
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

Nous allons créer plusieurs partiels :  
[Exemple de répertoire SCSS contenant des partiels](https://github.com/MyClientisRich/WPbaseTheme/tree/master/scss)  
- Utilisation de variables :
```
Créer un fichier assets/scss/_colors.scss est mettre dedans :  
```
Ajoutez ceci dedans  
```
$fond: #222;
$texte: #AAA;

$base_color: #48A3E9;
```
- Créer un fichier assets/scss/app.scss et importez dedans le fichier colors.scss dedans grâce à:  
```
@import nomdufichierSeulement
```
Dans app.scss, affectez au body un background en utilisant la variable $fond comme couleur et comme couleur de police la variable $texte

- Compiler et Tester vos fichiers SCSS ci-dessus et linkez le app.css obtenu sur l'index.html pour voir le résultat.
exemple de commande:
```
sass --watch assets/scss/body.scss:assets/css/styles.css --trace --style compressed
```

- Nesting ( traduction : Nidification?? par rapport à la structure )
```
Créer un fichier assets/scss/_liste.scss est mettre dedans :  
```
Modifiez le nesting ci-dessous pour affecter à la liste .listDeux uniquement un lien blue et lime au hover :  
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

Pareil pour la liste de box3 ( .listTrois ), couleur du lien en jaune et grise au survol.

Créez un héritage %box comme ci-dessous, vous pouvez l'utiliser ensuite avec le mot clef @extend dans vos classes box1, box2 et box3 pour ajouter ces propriétés automatiquement.

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
