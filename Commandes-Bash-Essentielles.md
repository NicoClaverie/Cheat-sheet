
# Commandes Bash Essentielles

Ce document rassemble les commandes et structures de contrôle de base pour écrire des scripts Bash.


## 1. Structure de base d'un script Bash

Un script Bash commence généralement par un "shebang" qui indique l'interpréteur à utiliser.

```bash
#!/bin/bash
# Ceci est un commentaire
echo "Bonjour depuis mon script Bash !"
````

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
