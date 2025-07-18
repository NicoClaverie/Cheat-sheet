## Pour compresser (créer une archive)
Pour créer une archive compressée au format .tar.gz (le plus courant) à partir d'un dossier ou de fichiers :
```
tar -czvf nom_de_larchive.tar.gz /chemin/du/dossier_ou_fichier
```

Exemple : Pour compresser tout le contenu du dossier `/home/user/documents` dans un fichier `backup.tar.gz` :

```
tar -czvf backup.tar.gz /home/user/documents
```
---

## Pour décompresser (extraire une archive)
Pour extraire le contenu d'une archive .tar.gz dans le dossier courant :

```
tar -xzvf nom_de_larchive.tar.gz
```

Exemple : Pour extraire le contenu de backup.tar.gz :

```
tar -xzvf backup.tar.gz
```
---

## Explication des options (lettres)
C'est plus facile de s'en souvenir quand on sait ce que chaque lettre signifie :

  * `-c` : Create (Créer une archive).

  * `-x` : Extract (Extraire d'une archive).

  * `-z` : Compresser/décompresser avec gzip (pour les fichiers .tar.gz).

  * `-v` : Verbose (Affiche les noms des fichiers pendant l'opération). C'est optionnel mais pratique pour voir la progression.

  * `-f` : File (Spécifie que le prochain argument est le nom du fichier d'archive). Cette option doit être placée juste avant le nom de l'archive.

---

## Commandes utiles supplémentaires

  * Lister le contenu d'une archive sans l'extraire :

```
tar -tzvf nom_de_larchive.tar.gz
```

(On remplace `-x` (extract) par `-t` (list)).

  * Extraire dans un dossier spécifique :

```
tar -xzvf nom_de_larchive.tar.gz -C /chemin/du/dossier_de_destination
```

(On ajoute l'option `-C` (Change directory)).

  * Pour d'autres formats de compression :

    * .tar.bz2 (bzip2) : remplace `-z` par `-j`.

      * Compresser : `tar -cjvf archive.tar.bz2 /dossier`

      * Décompresser : `tar -xjvf archive.tar.bz2`

    * .tar.xz (XZ) : remplace `-z` par `-J` (J majuscule).

      * Compresser : `tar -cJvf archive.tar.xz /dossier`

      * Décompresser : `tar -xJvf archive.tar.xz`
