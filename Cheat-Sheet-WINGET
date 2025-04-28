# 📦 Guide rapide de `winget` (Windows Package Manager)

## Présentation rapide

`winget` est un gestionnaire de paquets pour Windows qui permet d'installer, mettre à jour, configurer et désinstaller des applications directement depuis le terminal.

Il est disponible nativement sur Windows 10 (à partir de 2020) et Windows 11.

---

## Commandes principales

| Commande                           | Description                                        | Exemple                                      |
|:------------------------------------|:---------------------------------------------------|:---------------------------------------------|
| `winget search <nom>`               | Rechercher une application                        | `winget search vscode`                       |
| `winget install <nom>`              | Installer une application                         | `winget install vscode`                      |
| `winget uninstall <nom>`            | Désinstaller une application                      | `winget uninstall vscode`                    |
| `winget upgrade`                    | Lister les mises à jour disponibles               | `winget upgrade`                             |
| `winget upgrade <nom>`              | Mettre à jour une application spécifique          | `winget upgrade vscode`                      |
| `winget list`                       | Lister toutes les applications installées         | `winget list`                                |
| `winget show <nom>`                 | Afficher les détails d'une application            | `winget show vscode`                         |
| `winget settings`                   | Ouvrir le fichier de configuration `winget`       | `winget settings`                            |
| `winget source list`                | Lister les sources disponibles                    | `winget source list`                         |
| `winget source add <nom> <url>`     | Ajouter une nouvelle source                      | `winget source add myrepo https://...`        |
| `winget source update`              | Mettre à jour les sources (catalogues)             | `winget source update`                       |
| `winget source reset --force`       | Réinitialiser les sources officielles              | `winget source reset --force`                |

---

## Explication rapide

- **Recherche** :  
  Pour trouver un logiciel disponible dans le catalogue officiel (Microsoft ou communauté).

- **Installation** :  
  Installe directement sans passer par un navigateur ou un installeur classique.

- **Mise à jour** :  
  Un moyen rapide de maintenir vos logiciels à jour sans vérifier manuellement.

- **Sources** :  
  - `source list` permet de voir toutes les sources utilisées.
  - `source update` met à jour la liste des applications disponibles.
  - `source add` ajoute un dépôt personnalisé.
  - `source reset --force` restaure les dépôts officiels si besoin.

- **Configuration** :  
  Personnalisation du comportement de `winget` via un fichier JSON (ex : installation silencieuse sans confirmation).

---

## Exemple d'utilisation

```bash
# Rechercher Google Chrome
winget search "Google Chrome"

# Installer Google Chrome
winget install "Google Chrome"

# Mettre à jour tous les logiciels
winget upgrade

# Mettre à jour les sources
winget source update

# Désinstaller VLC Media Player
winget uninstall "VLC media player"
```

