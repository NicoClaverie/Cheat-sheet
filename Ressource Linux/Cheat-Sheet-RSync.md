# Rsync : Remote Sync

`rsync` (Remote Sync) est un outil de synchronisation de fichiers rapide et polyvalent qui permet de copier des fichiers localement ou à distance.


## 📂 Syntaxe de base

```
rsync [OPTIONS] [SOURCE] [DESTINATION]
```

## 🛠️ Options courantes

|Option|Description|
|:-:|:-:|
|`-a`|**Archive** : préserve les permissions, propriétaires, dates et liens symboliques (équivalent à `-rlptgoD`).|
|`-v`|**Verbose** : affiche les détails de la progression.|
|`-z`|**Compression** : compresse les données pendant le transfert.|
|`-h`|**Human-readable** : affiche les tailles de fichiers en format lisible (Ko, Mo, Go).|
|`-e`|	**RSH** : spécifie le shell distant et permet de passer des options SSH (ex:`-e 'ssh -p 2222 -i ~/.ssh/id_rsa'`).
|`-P`|Combine `--partial` (garde les fichiers tronqués) et `--progress` (barre de progression).|
|`-n`|**Dry-run** : simule l'exécution sans rien copier.|
|`--delete`|Supprime les fichiers de la destination s'ils n'existent plus à la source.|

## 📋 Exemples d'utilisation

**1. Synchronisation locale**

Copie le contenu d'un dossier vers un autre :

```
rsync -avh /chemin/source/ /chemin/destination/
```

> **Note** : Le / à la fin de la source copie le contenu du dossier. Sans le /, rsync copie le dossier lui-même.

**2. Synchronisation vers un serveur distant (via SSH)**

```
rsync -avzP /mon/dossier/ utilisateur@ip_serveur:/destination/
```

**3. Récupérer des fichiers depuis un serveur distant**

```
rsync -avzP utilisateur@ip_serveur:/source/ /mon/dossier/local/
```

**4. Mode Miroir (Suppression des fichiers absents de la source)**

```
rsync -av --delete /chemin/source/ /chemin/destination/
```

**5. Exclure des fichiers ou dossiers**

```
rsync -av --exclude 'node_modules' --exclude '*.log' /source/ /destination/
```

**6. Utiliser un port SSH spécifique**

```
rsync -avz -e 'ssh -p 2222' /source/ utilisateur@ip_serveur:/destination/
```

## ⚠️ Précautions (Dry-run)

Il est fortement recommandé d'utiliser l'option `-n` (ou `--dry-run`) avec `-v` avant d'exécuter une commande complexe, surtout avec l'option `--delete` :

```
rsync -avnh --delete /source/ /destination/
```

---

> Lien utile : https://www.it-connect.fr/maitriser-rsync-sous-linux-le-guide-complet-de-la-synchronisation-de-donnees/