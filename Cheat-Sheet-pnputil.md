
# Cheat Sheet - pnputil

`pnputil` est un utilitaire Windows permettant d'ajouter, supprimer et lister les pilotes du magasin de pilotes (driver store).

## Commandes de base

| Commande                                     | Description |
|---------------------------------------------|-------------|
| `pnputil /add-driver monpilote.inf`         | Ajoute un pilote au magasin |
| `pnputil /delete-driver oem42.inf`          | Supprime un pilote du magasin |
| `pnputil /enum-drivers`                     | Liste tous les pilotes présents |
| `pnputil /export-driver oem42.inf dossier`  | Exporte le pilote vers un dossier |
| `pnputil /disable-device <ID>`              | Désactive un périphérique |
| `pnputil /enable-device <ID>`               | Réactive un périphérique |
| `pnputil /scan-devices`                     | Scanne les périphériques pour détecter des changements |

## Détails des options utiles

| Option | Description |
|--------|-------------|
| `/add-driver <fichier.inf>` | Ajoute un pilote INF au magasin |
| `/delete-driver <nom.inf> [/force]` | Supprime un pilote, avec option de forcer si utilisé |
| `/enum-drivers` | Affiche les pilotes installés (nom, date, version, fournisseur) |
| `/export-driver <nom.inf> <dossier>` | Exporte le fichier du pilote |
| `/?` | Affiche l’aide |

---

📝 Astuce : pour connaître le nom exact d’un pilote (`oemXX.inf`), utilise `pnputil /enum-drivers`.
