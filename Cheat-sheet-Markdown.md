Test Obsidian


# Introduction à Markdown  
Markdown est un langage de balisage léger, créé par John Gruber en 2004, qui permet de formater du texte de manière simple et lisible. Il utilise une syntaxe intuitive, facilitant la rédaction de documents, d'articles ou de documentation sans nécessiter de connaissances en HTML.

Markdown prend en charge divers éléments comme les titres, les listes, les liens et les images, ce qui en fait un outil polyvalent. Son principal avantage est de permettre aux utilisateurs de se concentrer sur le contenu plutôt que sur la mise en forme.


Ceci est destiné à être une référence rapide et une vitrine. Pour des informations plus complètes, consultez [la spécification originale de John Gruber](http://daringfireball.net/projects/markdown/) et la [page d'information sur le Markdown avec des fonctionnalités GitHub](http://github.github.com/github-flavored-markdown/).

Notez qu'il existe également une [fiche de référence spécifique à Markdown Here](./Markdown-Here-Cheatsheet) si c'est ce que vous recherchez. Vous pouvez également consulter [d'autres outils Markdown](./Other-Markdown-Tools).

## Table des matières  
[En-têtes](#headers)  
[Mise en forme](#emphasis)  
[Listes](#lists)  
[Lien](#links)  
[Images](#images)  
[Code et mise en surbrillance de syntaxe](#code)  
[Notes de bas de page](#footnotes)  
[Tableaux](#tables)  
[Citations](#blockquotes)  
[HTML en ligne](#html)  
[Règle horizontale](#hr)  
[Sauts de ligne](#lines)  
[Vidéos YouTube](#videos)  

<a name="headers"/>

## En-têtes

```no-highlight
# H1
## H2
### H3
#### H4
##### H5
###### H6

Alternativement, pour H1 et H2, un style de soulignement :

Alt-H1
======

Alt-H2
------
```

# H1
## H2
### H3
#### H4
##### H5
###### H6

Alternativement, pour H1 et H2, un style de soulignement :

Alt-H1
======

Alt-H2
------

<a name="emphasis"/>

## Mise en forme

```no-highlight
Mise en forme, alias italique, avec *astérisques* ou _soulignements_.

Mise en forme forte, alias gras, avec **astérisques** ou __soulignements__.

Mise en forme combinée avec **astérisques et _soulignements_**.

Le barré utilise deux tilde. ~~Gratter ceci.~~
```

Mise en forme, alias italique, avec *astérisques* ou _soulignements_.

Mise en forme forte, alias gras, avec **astérisques** ou __soulignements__.

Mise en forme combinée avec **astérisques et _soulignements_**.

Le barré utilise deux tilde. ~~Gratter ceci.~~

<a name="lists"/>

## Listes

(Dans cet exemple, les espaces de début et de fin sont indiqués par des points : ⋅)

```no-highlight
1. Premier élément de la liste ordonnée
2. Un autre élément
⋅⋅* Sous-liste non ordonnée. 
1. Les chiffres réels n'ont pas d'importance, juste que c'est un nombre
⋅⋅1. Sous-liste ordonnée
4. Et un autre élément.

⋅⋅⋅Vous pouvez avoir des paragraphes correctement indentés dans les éléments de la liste. Remarquez la ligne vide ci-dessus, et les espaces de début (au moins un, mais nous en utiliserons trois ici pour aligner également le Markdown brut).

⋅⋅⋅Pour avoir un saut de ligne sans un paragraphe, vous devrez utiliser deux espaces à la fin.⋅⋅
⋅⋅⋅Notez que cette ligne est séparée, mais dans le même paragraphe.⋅⋅
⋅⋅⋅(Ceci est contraire au comportement typique de saut de ligne GFM, où les espaces de fin ne sont pas requis.)

* La liste non ordonnée peut utiliser des astérisques
- Ou des moins
+ Ou des plus
```

1. Premier élément de la liste ordonnée
2. Un autre élément
   * Sous-liste non ordonnée. 
1. Les chiffres réels n'ont pas d'importance, juste que c'est un nombre
   1. Sous-liste ordonnée
4. Et un autre élément.

   Vous pouvez avoir des paragraphes correctement indentés dans les éléments de la liste. Remarquez la ligne vide ci-dessus, et les espaces de début (au moins un, mais nous en utiliserons trois ici pour aligner également le Markdown brut).

   Pour avoir un saut de ligne sans un paragraphe, vous devrez utiliser deux espaces à la fin.  
   Notez que cette ligne est séparée, mais dans le même paragraphe.  
   (Ceci est contraire au comportement typique de saut de ligne GFM, où les espaces de fin ne sont pas requis.)

* La liste non ordonnée peut utiliser des astérisques
- Ou des moins
+ Ou des plus

<a name="links"/>

## Liens

Il existe deux façons de créer des liens.

```no-highlight
[Je suis un lien de style en ligne](https://www.google.com)

[Je suis un lien de style en ligne avec titre](https://www.google.com "Page d'accueil de Google")

[Je suis un lien de style référence][Texte de référence arbitraire insensible à la casse]

[Je suis une référence relative à un fichier de dépôt](../blob/master/LICENSE)

[Vous pouvez utiliser des chiffres pour des définitions de liens de style référence][1]

Ou laissez-le vide et utilisez [le texte du lien lui-même].

Les URL et les URL entre crochets angulaires seront automatiquement transformées en liens. 
http://www.example.com ou <http://www.example.com> et parfois 
example.com (mais pas sur GitHub, par exemple).

Un peu de texte pour montrer que les liens de référence peuvent suivre plus tard.

[texte de référence arbitraire insensible à la casse]: https://www.mozilla.org
[1]: http://slashdot.org
[texte du lien lui-même]: http://www.reddit.com
```

[Je suis un lien de style en ligne](https://www.google.com)

[Je suis un lien de style en ligne avec titre](https://www.google.com "Page d'accueil de Google")

[Je suis un lien de style référence][Texte de référence arbitraire insensible à la casse]

[Je suis une référence relative à un fichier de dépôt](../blob/master/LICENSE)

[Vous pouvez utiliser des chiffres pour des définitions de liens de style référence][1]

Ou laissez-le vide et utilisez [le texte du lien lui-même].

Les URL et les URL entre crochets angulaires seront automatiquement transformées en liens. 
http://www.example.com ou <http://www.example.com> et parfois 
example.com (mais pas sur GitHub, par exemple).

Un peu de texte pour montrer que les liens de référence peuvent suivre plus tard.

[texte de référence arbitraire insensible à la casse]: https://www.mozilla.org  
[1]: http://slashdot.org  
[texte du lien lui-même]: http://www.reddit.com  

<a name="images"/>

## Images

```no-highlight
Voici notre logo (survolez pour voir le texte du titre) :

Style en ligne : 
![texte alternatif](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Texte de titre du logo 1")

Style de référence : 
![texte alternatif][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Texte de titre du logo 2"
```

Voici notre logo (survolez pour voir le texte du titre) :

Style en ligne : 
![texte alternatif](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Texte de titre du logo 1")

Style de référence : 
![texte alternatif][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Texte de titre du logo 2"

<a name="code"/>

## Code et mise en surbrillance de syntaxe

Les blocs de code font partie de la spécification Markdown, mais la mise en surbrillance de syntaxe ne l'est pas. Cependant, de nombreux rendus -- comme ceux de GitHub et *Markdown Here* -- prennent en charge la mise en surbrillance de syntaxe. Les langages pris en charge et la manière d'écrire ces noms de langages varieront d'un rendu à l'autre. *Markdown Here* prend en charge la mise en surbrillance pour des dizaines de langages (et des pseudo-langages, comme les diffs et les en-têtes HTTP) ; pour voir la liste complète, et comment écrire les noms de langages, consultez la [page de démonstration de highlight.js](http://softwaremaniacs.org/media/soft/highlight/test.html).

```no-highlight
Le code en ligne `code` a `des backticks autour`.
```

Le code en ligne `code` a `des backticks autour`.

Les blocs de code sont soit délimités par des lignes avec trois backticks <code>```</code>, soit indentés avec quatre espaces. Je recommande d'utiliser uniquement les blocs de code délimités : ils sont plus faciles et seuls eux prennent en charge la mise en surbrillance de syntaxe.

<pre lang="no-highlight"><code>```javascript
var s = "Mise en surbrillance de la syntaxe JavaScript";
alert(s);
```
 
```python
s = "Mise en surbrillance de la syntaxe Python"
print s
```


 
```html
<p>Ce code est en HTML.</p>
```</code></pre>

```javascript
var s = "Mise en surbrillance de la syntaxe JavaScript";
alert(s);
```
 
```python
s = "Mise en surbrillance de la syntaxe Python"
print(s)
```
 
```html
<p>Ce code est en HTML.</p>
```

<a name="footnotes"/>

## Notes de bas de page

```no-highlight
Voici une note de bas de page.[^1] 

[^1]: C'est la note de bas de page.
```

Voici une note de bas de page.[^1] 

[^1]: C'est la note de bas de page.

<a name="tables"/>

## Tableaux

```no-highlight
| Colonne 1 | Colonne 2 | Colonne 3 |
| --------- | --------- | --------- |
| Cellule 1 | Cellule 2 | Cellule 3 |
| Cellule 4 | Cellule 5 | Cellule 6 |
```

| Colonne 1 | Colonne 2 | Colonne 3 |
| --------- | --------- | --------- |
| Cellule 1 | Cellule 2 | Cellule 3 |
| Cellule 4 | Cellule 5 | Cellule 6 |

<a name="blockquotes"/>

## Citations

```no-highlight
> Une citation dans un bloc de citation. 
> 
> Une citation peut s'étendre sur plusieurs lignes.
```

> Une citation dans un bloc de citation. 
> 
> Une citation peut s'étendre sur plusieurs lignes.

<a name="html"/>

## HTML en ligne

```no-highlight
Pour du HTML brut en ligne : <b>texte en gras</b>, <i>texte en italique</i>, <a href="http://www.google.com">lien</a>.
```

Pour du HTML brut en ligne : <b>texte en gras</b>, <i>texte en italique</i>, <a href="http://www.google.com">lien</a>.

<a name="hr"/>

## Règle horizontale

```no-highlight
Trois tirets ou plus sur une ligne seule, peut être entouré de blancs : 
--- ou ___
```

Trois tirets ou plus sur une ligne seule, peut être entouré de blancs : 
--- ou ___

<a name="lines"/>

## Sauts de ligne

Un saut de ligne dans un bloc de texte sera ignoré, sauf si une ligne vide le précède.

```no-highlight
Ligne 1, 
Ligne 2, 
Ligne 3
```

Ligne 1,  
Ligne 2,  
Ligne 3

<a name="videos"/>

## Vidéos YouTube

Pour intégrer des vidéos YouTube, utilisez un lien simple ou un iframe. 

```no-highlight
[![Titre de la vidéo](https://img.youtube.com/vi/<ID_VIDEO>/default.jpg)](https://www.youtube.com/watch?v=<ID_VIDEO>)
```

[![Titre de la vidéo](https://img.youtube.com/vi/dQw4w9WgXcQ/default.jpg)](https://www.youtube.com/watch?v=dQw4w9WgXcQ)

--- 

N'hésitez pas à me dire si vous avez besoin de quelque chose d'autre !
