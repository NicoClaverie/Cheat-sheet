
# Commandes Bash Essentielles

Ce document rassemble les commandes et structures de contrôle de base pour écrire des scripts Bash.

---

## 1. Structure de base d'un script Bash

Un script Bash commence généralement par un "shebang" qui indique l'interpréteur à utiliser.

```bash
#!/bin/bash
# Ceci est un commentaire
echo "Bonjour depuis mon script Bash !"
````
---

## 2. Variables

### Déclaration et utilisation

Bash

```
NOM="Alice"
AGE=30
echo "Je m'appelle $NOM et j'ai $AGE ans."
```

### Variables spéciales

- `$0`: Nom du script
- `$1`, `$2`, ...: Arguments passés au script
- `$#`: Nombre d'arguments
- `$@`: Tous les arguments (séparés)
- `$*`: Tous les arguments (en une seule chaîne)
- `$?`: Code de sortie de la dernière commande (0 pour succès, autre pour erreur)
- `$$`: PID du processus actuel
- `$!`: PID du dernier processus en arrière-plan

<!-- end list -->

Bash

```
echo "Le nom de ce script est : $0"
echo "Le premier argument est : $1"
echo "Il y a $# arguments."
```

## 3. Entrée/Sortie

### Afficher un message

Bash

```
echo "Ceci est un message."
echo -e "Message avec\nretour à la ligne." # -e pour interpréter les séquences d'échappement
```

### Lire une entrée utilisateur

Bash

```
echo "Quel est votre nom ?"
read PRENOM
echo "Bonjour, $PRENOM !"
```
---

## 4. Conditions (if)

### `if` simple

Bash

```
if [ "$NOM" == "Alice" ]; then
    echo "Bonjour, Alice !"
fi
```

### `if-else`

Bash

```
AGE=25
if [ "$AGE" -ge 18 ]; then
    echo "Vous êtes majeur."
else
    echo "Vous êtes mineur."
fi
```

### `if-elif-else`

Bash

```
NOTE=15
if [ "$NOTE" -ge 16 ]; then
    echo "Très bien !"
elif [ "$NOTE" -ge 10 ]; then
    echo "Bien."
else
    echo "Insuffisant."
fi
```

### Opérateurs de comparaison pour `[ ]` (test)

- **Chaînes de caractères :**
    - `==` ou `=`: Égalité
    - `!=`: Inégalité
    - `-z STRING`: STRING est vide
    - `-n STRING`: STRING n'est pas vide
- **Nombres entiers :**
    - `-eq`: Égal à
    - `-ne`: Différent de
    - `-gt`: Supérieur à
    - `-ge`: Supérieur ou égal à
    - `-lt`: Inférieur à
    - `-le`: Inférieur ou égal à
- **Fichiers :**
    - `-d FICHIER`: FICHIER existe et est un répertoire
    - `-e FICHIER`: FICHIER existe
    - `-f FICHIER`: FICHIER existe et est un fichier régulier
    - `-r FICHIER`: FICHIER est lisible
    - `-w FICHIER`: FICHIER est modifiable (writable)
    - `-x FICHIER`: FICHIER est exécutable

### `[[ ]]` (bashism, plus puissant)

Permet des expressions régulières et des opérateurs logiques `&&`, `||`.

Bash

```
NOM="Bob"
if [[ "$NOM" =~ ^B ]]; then
    echo "Le nom commence par B."
fi

if [[ "$AGE" -gt 18 && "$NOM" == "Alice" ]]; then
    echo "Alice est majeure."
fi
```
---

## 5. Boucles

### `for` (itération sur une liste)

Bash

```
for FRUIT in pomme banane orange; do
    echo "J'aime la $FRUIT."
done
```

### `for` (itération numérique - style C)

Bash

```
for i in {1..5}; do
    echo "Compteur: $i"
done

# Ou avec la syntaxe style C (bashism)
for (( i=1; i<=5; i++ )); do
    echo "Compteur (style C): $i"
done
```

### `while` (tant que la condition est vraie)

Bash

```
COMPTEUR=1
while [ "$COMPTEUR" -le 5 ]; do
    echo "Boucle while: <span class="math-inline">COMPTEUR"
COMPTEUR\=</span>((COMPTEUR + 1)) # Incrémentation
done
```

### `until` (jusqu'à ce que la condition soit vraie)

Bash

```
COMPTEUR=1
until [ "$COMPTEUR" -gt 5 ]; do
    echo "Boucle until: <span class="math-inline">COMPTEUR"
COMPTEUR\=</span>((COMPTEUR + 1))
done
```
---

## 6. Fonctions

Bash

```
ma_fonction() {
    echo "Ceci est une fonction."
    echo "Arguments : $1 et <span class="math-inline">2"
return 0 \# Code de retour
\}
ma\_fonction "valeur1" "valeur2"
CODE\_RETOUR\=</span>?
echo "Le code de retour est : $CODE_RETOUR"
```
---

## 7. `case` (structures de sélection)

Similaire à un `switch` dans d'autres langages.

Bash

```
ACTION="stop"

case "$ACTION" in
    "start")
        echo "Démarrage du service."
        ;;
    "stop")
        echo "Arrêt du service."
        ;;
    "restart"|"reload") # Plusieurs motifs possibles
        echo "Redémarrage ou rechargement du service."
        ;;
    *) # Cas par défaut
        echo "Action inconnue."
        ;;
esac
```

---

## 8. Commandes utiles

- `ls`: Lister le contenu d'un répertoire
- `cd`: Changer de répertoire
- `pwd`: Afficher le répertoire de travail actuel
- `mkdir`: Créer un répertoire
- `rmdir`: Supprimer un répertoire vide
- `rm`: Supprimer des fichiers ou répertoires
- `cp`: Copier des fichiers ou répertoires
- `mv`: Déplacer ou renommer des fichiers ou répertoires
- `cat`: Afficher le contenu d'un fichier
- `grep`: Rechercher du texte dans des fichiers
- `find`: Rechercher des fichiers ou répertoires
- `chmod`: Changer les permissions de fichiers
- `chown`: Changer le propriétaire de fichiers
- `sudo`: Exécuter une commande en tant que superutilisateur
- `sleep SECONDES`: Mettre en pause l'exécution pendant un certain nombre de secondes
- `exit CODE`: Quitter le script avec un code de sortie

---

## 9. Opérations arithmétiques

Bash peut effectuer des opérations arithmétiques en utilisant `(( ))` ou `expr`. La première option est généralement préférée.

Bash

```
# Utilisation de (( ))
NB1=10
NB2=5
SOMME=$((NB1 + NB2))
SOUSTRACTION=$((NB1 - NB2))
MULTIPLICATION=$((NB1 * NB2))
DIVISION=$((NB1 / NB2))
MODULO=$((NB1 % NB2)) # Reste de la division

echo "Somme: $SOMME"
echo "Soustraction: $SOUSTRACTION"
echo "Multiplication: $MULTIPLICATION"
echo "Division: $DIVISION"
echo "Modulo: $MODULO"

# Incrémentation/Décrémentation
COMPTEUR=1
((COMPTEUR++)) # COMPTEUR devient 2
echo "Incrémentation: $COMPTEUR"
((COMPTEUR--)) # COMPTEUR redevient 1
echo "Décrémentation: $COMPTEUR"

# Utilisation de expr (moins moderne, mais possible)
RESULTAT_EXPR=$(expr 10 + 5)
echo "Résultat avec expr: $RESULTAT_EXPR"
```

---

## 10. Redirection d'entrée/sortie et Pipes

Ces mécanismes sont fondamentaux pour le travail en ligne de commande et dans les scripts.

### Redirection de sortie

- `>`: Redirige la **sortie standard (stdout)** vers un fichier, **écrasant** le contenu s'il existe.
- `>>`: Redirige la **sortie standard (stdout)** vers un fichier, en l'**ajoutant** à la fin.
- `2>`: Redirige la **sortie d'erreur (stderr)** vers un fichier.
- `&>` ou `>&`: Redirige la **sortie standard et la sortie d'erreur** vers un fichier.

<!-- end list -->

Bash

```
echo "Ceci ira dans un fichier." > mon_fichier.txt
echo "Ceci sera ajouté au fichier." >> mon_fichier.txt
ls non_existant 2> erreurs.log # Les erreurs de ls iront dans erreurs.log
ls -l /tmp &> sortie_complete.log # Sortie et erreurs dans le même fichier
```

### Redirection d'entrée

- `<`: Redirige le contenu d'un fichier vers l'entrée standard (stdin) d'une commande.

<!-- end list -->

Bash

```
# Trie les lignes du fichier et affiche le résultat
sort < mon_fichier.txt
```

### Pipes (`|`)

Le pipe permet de **chaîner des commandes** en envoyant la sortie standard d'une commande comme entrée standard de la commande suivante.

Bash

```
# Lister les fichiers, puis rechercher ceux qui contiennent "log"
ls -l | grep "log"

# Compter le nombre de lignes dans un fichier
cat mon_fichier.txt | wc -l
```

---

## 11. Gestion des erreurs et Débogage

Des pratiques importantes pour des scripts robustes.

### `set -e` (Exit on error)

Arrête le script immédiatement si une commande échoue (retourne un code de sortie non nul).

Bash

```
#!/bin/bash
set -e # Active l'option d'arrêt en cas d'erreur

echo "Début du script."
commande_qui_existe # Cette commande va s'exécuter
commande_qui_n_existe_pas # Cette commande va échouer et arrêter le script
echo "Cette ligne ne sera pas exécutée si la commande précédente échoue."
```

### `set -u` (Treat unset variables as errors)

Traite l'utilisation de variables non définies comme une erreur et arrête le script.

Bash

```
#!/bin/bash
set -u # Active l'option d'erreur sur variable non définie

echo "Bonjour, $NOM_DEFINI!" # OK si NOM_DEFINI est définie
echo "Salut, $VARIABLE_NON_DEFINIE!" # Erreur si VARIABLE_NON_DEFINIE n'est pas définie
```

### `set -x` (Debug mode)

Affiche chaque commande exécutée par le script avant son exécution, ce qui est très utile pour le débogage.

Bash

```
#!/bin/bash
set -x # Active le mode débogage

echo "Ceci est un test."
ls -l /tmp
# Désactiver le mode débogage
set +x
echo "Le mode débogage est désactivé ici."
```

### Vérifier le code de sortie (`$?`)

Bash

```
cp /source/non/existante /tmp/destination
if [ $? -ne 0 ]; then
    echo "Erreur lors de la copie du fichier."
fi
```

---

## 12. Arguments de ligne de commande et Options (getopts)

Pour rendre les scripts plus flexibles.

### Accès aux arguments positionnels

Bash

```
#!/bin/bash
echo "Premier argument : $1"
echo "Deuxième argument : $2"
echo "Tous les arguments : $@"
echo "Nombre d'arguments : $#"
```

### Gestion des options avec `getopts`

Pour des options plus complexes (ex: `-f fichier`, `-v` pour verbose).

Bash

```
#!/bin/bash

FICHIER=""
VERBOSE=0

while getopts "vf:" opt; do
  case $opt in
    v)
      VERBOSE=1
      echo "Mode verbeux activé."
      ;;
    f)
      FICHIER="$OPTARG"
      echo "Fichier spécifié : $FICHIER"
      ;;
    \?) # Caractère non reconnu
      echo "Option invalide: -$OPTARG" >&2
      exit 1
      ;;
  esac
done

shift $((OPTIND-1)) # Supprime les options déjà traitées des arguments

# Les arguments restants sont accessibles via $1, $2, etc.
echo "Arguments restants : $@"

if [ "$VERBOSE" -eq 1 ]; then
    echo "Exécution en mode verbeux."
fi
if [ -n "$FICHIER" ]; then
    echo "Traitement du fichier $FICHIER..."
fi
```

---

## 13. Expressions régulières et `grep`, `sed`, `awk`

Des outils puissants pour manipuler du texte.

- **`grep`**: Filtre les lignes qui correspondent à un motif.
    
    Bash
    
    ```
    grep "mot" mon_fichier.txt
    grep -E "pattern1|pattern2" mon_fichier.txt # -E pour regex étendues
    grep -v "exclure" mon_fichier.txt # Exclure les lignes
    ```
    
- **`sed`**: Éditeur de flux, utile pour des remplacements ou des suppressions.
    
    Bash
    
    ```
    sed 's/ancien/nouveau/g' mon_fichier.txt # Remplacer toutes les occurrences
    sed '/pattern/d' mon_fichier.txt # Supprimer les lignes contenant "pattern"
    ```
    
- **`awk`**: Langage de script puissant pour le traitement de texte basé sur des colonnes.
    
    Bash
    
    ```
    # Afficher la première et la troisième colonne d'un fichier (séparateur par défaut: espace/tab)
    awk '{print $1, $3}' mon_fichier.txt
    # Calculer la somme d'une colonne
    awk '{sum += $2} END {print sum}' nombres.txt
    ```
    

---

## 14. Cheatsheet rapide des opérateurs de test

|Opérateur|Type|Description|
|:--|:--|:--|
|`==`, `=`|Chaînes|Égal à|
|`!=`|Chaînes|Différent de|
|`-z`|Chaînes|Chaîne vide|
|`-n`|Chaînes|Chaîne non vide|
|`-eq`|Nombres|Égal à|
|`-ne`|Nombres|Différent de|
|`-gt`|Nombres|Strictement supérieur à|
|`-ge`|Nombres|Supérieur ou égal à|
|`-lt`|Nombres|Strictement inférieur à|
|`-le`|Nombres|Inférieur ou égal à|
|`-d fichier`|Fichiers|Est un répertoire|
|`-e fichier`|Fichiers|Existe|
|`-f fichier`|Fichiers|Est un fichier régulier|
|`-r fichier`|Fichiers|Est lisible|
|`-w fichier`|Fichiers|Est modifiable (writable)|
|`-x fichier`|Fichiers|Est exécutable|
|`&&`|Logique (`[[ ]]`)|ET logique (AND)|
|`|`|Logique (`[[ ]]`)|
|`!`|Logique (`[[ ]]`)|NON logique (NOT)|

Exporter vers Sheets

---

Ces ajouts couvriront des scénarios plus avancés et rendront tes scripts Bash beaucoup plus flexibles et robustes.
